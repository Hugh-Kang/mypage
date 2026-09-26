# N+1일 리텐션 vs 캘린더월 리텐션 — SQL 쿼리 관점의 개념 및 차이

> 작성 목적: 작년 티빙 서비스플래닝 1차 면접에서 받았던 SQL 질문("N+1 방문일 기준 리텐션 vs 월간 방문 기준 리텐션, 쿼리 작성시 주된 차이는?")에 대한 정확한 개념 설명과 예시 쿼리 준비
> 작성일: 2026-09-26
> 배경: `tving-2025-11-1st-interview-post-mortem.md`(3-7. SQL 역량)에서 이 질문에 "챗GPT로 짜서 기억 안 난다"고 답해 감점 요인으로 지적된 바 있음 — 이번엔 개념·쿼리를 정확히 정리해 재대비

## 0. 설계 프롬프트

> 너는 데이터 분석 면접 문제를 출제하고 모범 답안을 작성하는 코치다. "N+1일(가입일/방문일 기준 상대적 N일 후 재방문) 리텐션"과 "캘린더월(달력상 이번 달 대비 다음 달) 리텐션" 두 개념을 각각 정확히 설명하고, SQL 쿼리를 작성할 때 두 방식이 로직상 근본적으로 어떻게 달라지는지(기준점의 성격, JOIN/비교 조건, 필요한 함수)를 구조화하고, 각각의 예시 쿼리를 작성하라. 마지막으로 이 차이를 한 문장으로 요약하는 면접용 답변을 제시하라.

## 1. 개념 설명

### N+1일 리텐션 (Rolling/N-day Retention)
- **정의**: 각 사용자의 **개인 기준일**(보통 가입일 또는 첫 방문일)로부터 정확히 N일이 지난 시점에 다시 활동했는지를 보는 지표입니다. 예: Day-1 리텐션(가입 다음 날 재방문), Day-7 리텐션(가입 일주일 후 재방문).
- **기준점의 성격**: 사용자마다 기준일이 다릅니다. A 사용자는 1월 5일에 가입했으면 "1월 6일" 방문 여부를, B 사용자는 3월 20일에 가입했으면 "3월 21일" 방문 여부를 봅니다. 즉 **기준점이 사용자별로 상대적(relative)**입니다.

### 캘린더월 리텐션 (Calendar Month Retention)
- **정의**: 달력상의 **월 경계(1월, 2월, 3월...)**를 기준으로, 이번 달에 활동한 사용자 중 몇 %가 다음 달에도 활동했는지를 보는 지표입니다.
- **기준점의 성격**: 모든 사용자가 같은 달력 경계를 공유합니다. 1월 1일에 가입한 사용자든 1월 31일에 가입한 사용자든, "1월에 활동했는가"라는 동일한 기준으로 묶입니다. 즉 **기준점이 모든 사용자에게 절대적(absolute)이고 고정**되어 있습니다.

## 2. SQL 쿼리 작성 시 핵심 차이

| 구분 | N+1일 리텐션 | 캘린더월 리텐션 |
|---|---|---|
| 기준일 계산 | 사용자별로 `MIN(event_date)` 등 **개인 기준일**을 먼저 구해야 함 | 기준일 계산 불필요, `DATE_TRUNC('month', event_date)`로 **월 단위 정규화**만 하면 됨 |
| 비교 조건 | `event_date = 개인기준일 + N일` — **사용자마다 다른 날짜**와 비교 | `active_month = 이번달 + 1개월` — **모든 사용자에게 동일한 오프셋** |
| 필요한 로직 | 사용자별 기준일 계산 + 그 기준일 대비 정확히 N일 후 이벤트 존재 여부 확인 (self-join 또는 `EXISTS`) | 월별로 그룹화한 뒤 `LAG`/`LEAD` 윈도우 함수로 인접 월 존재 여부 확인 |
| 갱신 여부 | 기준일이 **한 번 정해지면 고정**(가입일은 바뀌지 않음) | 매달 새로운 활동 여부에 따라 **매달 갱신**되는 이동형 집계 |

**한 문장 요약**: N+1일 리텐션은 "사용자마다 다른 개인화된 기준일 + 상대적 날짜 오프셋"으로 계산하고, 캘린더월 리텐션은 "모든 사용자가 공유하는 고정된 달력 경계"로 계산한다는 점이 근본적인 차이입니다.

## 3. 예시 쿼리

### 3-1. N+1일(Day-1) 리텐션

```sql
WITH first_visit AS (
  SELECT user_id, MIN(event_date) AS signup_date
  FROM events
  GROUP BY user_id
),
retained AS (
  SELECT
    f.user_id,
    EXISTS (
      SELECT 1 FROM events e
      WHERE e.user_id = f.user_id
        AND e.event_date = f.signup_date + INTERVAL '1 day'
    ) AS is_retained_d1
  FROM first_visit f
)
SELECT
  COUNT(*) AS total_users,
  SUM(CASE WHEN is_retained_d1 THEN 1 ELSE 0 END) AS retained_users,
  ROUND(100.0 * SUM(CASE WHEN is_retained_d1 THEN 1 ELSE 0 END) / COUNT(*), 2) AS retention_rate
FROM retained;
```
- 핵심: `signup_date + INTERVAL '1 day'`처럼 **사용자별 기준일에 오프셋을 더한 값**과 정확히 일치하는 이벤트가 있는지 확인

### 3-2. 캘린더월 리텐션

```sql
WITH monthly_active AS (
  SELECT DISTINCT user_id, DATE_TRUNC('month', event_date) AS active_month
  FROM events
),
with_next_month AS (
  SELECT
    user_id,
    active_month,
    LEAD(active_month) OVER (PARTITION BY user_id ORDER BY active_month) AS next_active_month
  FROM monthly_active
)
SELECT
  active_month,
  COUNT(*) AS total_users,
  SUM(CASE WHEN next_active_month = active_month + INTERVAL '1 month' THEN 1 ELSE 0 END) AS retained_users,
  ROUND(100.0 * SUM(CASE WHEN next_active_month = active_month + INTERVAL '1 month' THEN 1 ELSE 0 END) / COUNT(*), 2) AS retention_rate
FROM with_next_month
GROUP BY active_month
ORDER BY active_month;
```
- 핵심: `DATE_TRUNC`로 월 단위 정규화 후, `LEAD` 윈도우 함수로 **바로 다음 달에도 데이터가 있는지**를 확인 — 사용자별 기준일이 아니라 **월이라는 공통 그리드**로 비교

## 4. 이 둘을 헷갈리면 안 되는 이유 (실무적 함의)

캘린더월 리텐션은 **경과일수가 실제로는 하루 차이일 수도, 59일 차이일 수도 있습니다.** 예를 들어 1월 31일에 방문하고 2월 1일에 재방문하면 "리텐션 유지(1일 차이)"로 잡히지만, 1월 1일에 방문하고 2월 1일에 재방문해도 마찬가지로 "리텐션 유지(31일 차이)"로 잡힙니다. 반대로 N+1일 리텐션은 항상 정확히 N일 경과를 보장합니다. 그래서 **정밀하게 "N일 후 행동"을 보고 싶다면 N+1일 방식**이, **운영·보고용으로 "이번 달 대비 다음 달 활성 비율"처럼 직관적인 월간 지표**가 필요하다면 캘린더월 방식이 적합합니다.

## 5. 면접용 답변 스크립트

> "N+1일 리텐션은 사용자마다 가입일이나 첫 방문일이 다르기 때문에, 그 개인 기준일로부터 정확히 N일 후에 재방문했는지를 봅니다. 쿼리로는 사용자별 기준일을 먼저 구하고, '기준일 + N일'이라는 사용자마다 다른 날짜와 정확히 일치하는 이벤트가 있는지 확인하는 방식입니다.
>
> 반면 캘린더월 리텐션은 모든 사용자가 같은 달력 경계(1월, 2월…)를 공유합니다. 그래서 사용자별 기준일 계산 없이, DATE_TRUNC로 월 단위로 묶은 다음 LEAD 같은 윈도우 함수로 바로 다음 달에도 활동이 있었는지를 봅니다.
>
> 결국 가장 큰 차이는 **기준점이 사용자별로 상대적이냐(N+1일), 모든 사용자에게 고정된 절대적 기준이냐(캘린더월)**입니다. 그래서 캘린더월 방식은 실제 경과일수가 하루일 수도 있고 한 달에 가까울 수도 있다는 걸 감안해서 해석해야 합니다."

---
본 문서는 자가 준비용 SQL 개념 정리 자료입니다.

# N+1/월간 리텐션 이외의 SQL 예상 질문 3가지 — 나올 구간과 근거

> 작성 목적: 리텐션 쿼리 질문 외에, 면접 흐름상 어느 시점에서 어떤 SQL 질문이 추가로 나올 가능성이 높은지 예측하고 대비
> 작성일: 2026-09-26
> 근거자료: `interview-cross-company-pattern-analysis.md`(AB test/SQL 질문 반복 패턴), 포트폴리오(AARRR 퍼널 프로젝트, 홈화면 추천 세그먼트 비교), `mock-interview-kimheejae-analysis.md`(푸시 정책 논의)

## 0. 설계 프롬프트

> 너는 SQL 질문 대비 코치다. 지금까지의 실제·모의 면접 패턴을 보면 SQL 질문은 항상 지원자가 직접 언급한 특정 프로젝트나 데이터 논의 바로 다음에 그 맥락에 맞춰 나왔다(리텐션 질문도 "리텐션이 중요한 플랫폼"이라는 언급 직후 나옴). 이 패턴을 근거로, N+1/월간 리텐션 이외에 어떤 데이터 논의 구간에서 어떤 SQL 질문이 나올 가능성이 높은지 3가지를 예측하고, 각각 ① 왜 그 구간에서 나올 가능성이 높은지 근거, ② 예상 질문 문구, ③ 예시 쿼리와 답변 포인트를 구조화하라.

## 1. 예상 질문 3가지와 근거

### 예상 질문 ① — 이탈률 퍼널(AARRR) 논의 구간: "그 이탈률 퍼널을 SQL로는 어떻게 구현하시겠어요?"

**나올 가능성이 높은 이유**: 포트폴리오에 AARRR 보드로 이탈 구간(70%→26%)을 찾아낸 프로젝트가 명시적으로 있고, Discovery JD 자체가 "데이터 기반 플랫폼 기획"을 강조합니다. 지금까지의 패턴(11번가·GC케어에서 SQL을 언급하자마자 실무형 질문이 이어진 것)을 보면, 퍼널 프로젝트를 설명하는 순간 "그럼 그 단계별 전환율을 쿼리로는 어떻게 뽑나요?"로 이어질 확률이 높습니다.

**예시 쿼리**:
```sql
WITH funnel AS (
  SELECT
    user_id,
    MAX(CASE WHEN event_name = 'app_open' THEN 1 ELSE 0 END) AS step1_open,
    MAX(CASE WHEN event_name = 'marker_set_attempt' THEN 1 ELSE 0 END) AS step2_marker,
    MAX(CASE WHEN event_name = 'analysis_complete' THEN 1 ELSE 0 END) AS step3_complete
  FROM events
  WHERE event_date BETWEEN :start_date AND :end_date
  GROUP BY user_id
)
SELECT
  SUM(step1_open) AS step1_users,
  SUM(step2_marker) AS step2_users,
  SUM(step3_complete) AS step3_users,
  ROUND(100.0 * SUM(step2_marker) / NULLIF(SUM(step1_open), 0), 2) AS step1_to_2_rate,
  ROUND(100.0 * SUM(step3_complete) / NULLIF(SUM(step2_marker), 0), 2) AS step2_to_3_rate
FROM funnel;
```
**답변 포인트**: 사용자별로 각 단계 도달 여부를 `MAX(CASE WHEN...)`으로 한 행에 모으는 것이 핵심입니다(같은 유저가 여러 이벤트를 남겨도 중복 집계되지 않도록). 이후 단계 간 비율을 나눠서 구간별 이탈률을 계산합니다.

### 예상 질문 ② — 홈화면 추천 세그먼트 비교 구간: "즐겨찾기 등록자와 미등록자 CTR 차이를 쿼리로는 어떻게 뽑고, 유의미한지는 어떻게 보시겠어요?"

**나올 가능성이 높은 이유**: `home-recommendation-ctr-rationale-critical-review.md`에서 다룬 CTR 세그먼트 비교(18.2% vs 3.7%)를 설명하면, 자연스럽게 "그 수치를 실제로 어떻게 뽑았나요"로 이어질 가능성이 큽니다. 이미 작년 면접에서도 "리텐션 쿼리"로 SQL을 검증했듯, 이번엔 본인이 가장 자주 언급하는 프로젝트(홈화면 추천)의 핵심 수치 자체를 SQL로 재현할 수 있는지 확인하는 질문이 나올 수 있습니다.

**예시 쿼리**:
```sql
SELECT
  favorite_flag,
  COUNT(*) AS total_impressions,
  SUM(CASE WHEN clicked = 1 THEN 1 ELSE 0 END) AS clicks,
  ROUND(100.0 * SUM(CASE WHEN clicked = 1 THEN 1 ELSE 0 END) / COUNT(*), 2) AS ctr
FROM home_recommend_impressions
WHERE impression_date BETWEEN :start_date AND :end_date
GROUP BY favorite_flag;
```
**답변 포인트**: 이 쿼리로 나온 2×2 형태의 집계(즐겨찾기 여부 × 클릭 여부)를 통계적 유의성 검정(카이제곱 등)의 분할표(contingency table)로 그대로 쓸 수 있다는 것까지 언급하면, "SQL로 집계 → 통계 검정으로 유의성 판단"이라는 전체 파이프라인을 이해하고 있다는 인상을 줄 수 있습니다. (실제 유의성 검정 자체는 SQL보다는 Python/R/BI 툴에서 수행한다고 정직하게 답할 것)

### 예상 질문 ③ — 푸시 정책 논의 구간: "그 조건(예: 최근 7일 미접속 + 즐겨찾기 보유)에 맞는 타겟 유저를 SQL로 어떻게 뽑으시겠어요?"

**나올 가능성이 높은 이유**: 김희재와의 모의면접에서 이미 푸시 정책(피로도 관리, 서버 분산, 운영 고려)에 대해 상세히 답했고, Discovery JD에도 "Push" 모듈이 명시되어 있습니다. 개념적인 정책 답변 이후에는 실무형 질문("그 타겟 그룹을 실제로 어떻게 추출하나요")으로 이어지는 것이 자연스러운 흐름입니다.

**예시 쿼리**:
```sql
SELECT u.user_id
FROM users u
WHERE u.user_id NOT IN (
    SELECT DISTINCT user_id FROM events
    WHERE event_date >= CURRENT_DATE - INTERVAL '7 day'
  )
  AND EXISTS (
    SELECT 1 FROM favorites f WHERE f.user_id = u.user_id
  );
```
**답변 포인트**: `NOT IN` 대신 `NOT EXISTS`를 쓰면 NULL 값이 섞여 있을 때 더 안전하다는 점까지 언급하면 실무 감각을 보여줄 수 있습니다(`NOT IN`은 서브쿼리 결과에 NULL이 하나라도 있으면 전체 결과가 비어버리는 함정이 있음).

## 2. 종합 — 공통 준비 원칙

세 질문 모두 **본인이 직접 언급한 프로젝트/정책 바로 다음에 나온다는 공통 패턴**이 있습니다. 즉 "어떤 프로젝트를 설명하면 그 프로젝트의 핵심 수치를 SQL로 재현할 수 있는지 확인받는다"는 것이 일관된 흐름이므로, 앞으로 면접에서 프로젝트를 언급할 때마다 "이 수치를 어떻게 뽑았을까"를 스스로 먼저 질문해보고 최소한의 쿼리 구조를 마음속으로 정리해두는 습관이 가장 효과적인 대비입니다.

---
본 문서는 기존 준비 문서와 포트폴리오 내용을 근거로 작성된 자가 준비용 SQL 예상 질문 정리입니다.

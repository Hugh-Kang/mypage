# 티빙 2차 면접 — 예상 질문 및 꼬리질문 종합 정리

> 작성 목적: 1차 면접 실제 기록, 모의면접(이중원), 동료 피드백(세령님·형준님·김현우), 교차 회사 패턴 분석 등 이 세션에서 누적된 모든 자료를 종합해, 2차 면접에서 나올 만한 예상 질문과 꼬리질문을 하나의 표로 정리
> 작성일: 2026-10-16
> 근거자료: `tving-1st-interview-actual-transcript-structured.md`, `tving-2nd-mock-interview-leejungwon-2026-10-15-structured.md`, `interview-cross-company-pattern-analysis.md`, `tving-2nd-interview-cpo-hr-panel-expected-questions.md`, `tving-interview-pmf-experience-two-candidates-critique.md`, `tving-chatbot-agent-v3-mvp-tailquestions.md` 외 세션 내 전체 준비 자료

## 핵심 요약 (두괄식)

2차 면접(CPO + 인사 실무진)은 크게 6개 영역으로 나뉠 가능성이 높습니다: ① **커리어·이직 일관성**(가장 반복적으로 공격받은 영역), ② **핵심 프로젝트 심화 추궁**(챗봇·EV충전·건강디저트·사용량 대시보드 — 특히 인과관계·표본크기), ③ **신규 제안(챗봇 에이전트 MVP)**의 완성도, ④ **PM 정체성·PMF 등 개념 질문**, ⑤ **CPO의 전략/비즈니스 임팩트 질문**, ⑥ **인사의 조직적응·장기근속·처우 질문**. 이 중 "인과관계 검증"과 "표본/세그먼트 규모"는 거의 모든 회사에서 반복된 가장 날카로운 공통 약점이므로 최우선으로 점검이 필요합니다.

---

## 1. 커리어·이직 일관성

| 예상 질문 | 예상 꼬리질문 | 상세 참고 |
|---|---|---|
| 여러 차례 이직을 하셨는데 이유가 무엇인가요? | ① 그럼 티빙에서는 장기근속할 수 있다고 보는 근거는? ② 지금 회사도 고용 불안정성 때문에 이직 준비 중인데 같은 패턴이 반복되지 않을까요? | `tving-2nd-interview-cpo-hr-panel-expected-questions.md` #1, #2 |
| 개발자→데이터 사이언티스트→PM으로 커리어를 전환한 계기는? | 순수 기획/PM 경력 연차는 얼마나 되나요? | `tving-2nd-mock-interview-leejungwon-2026-10-15-structured.md` #2~3 |
| 회사를 선택할 때 본인만의 기준이 있나요? | 넷플릭스·쿠팡플레이 같은 경쟁 OTT 제안이 와도 티빙을 택할 이유는? | `tving-2nd-interview-cpo-hr-panel-expected-questions.md` #10 |
| 여러 직무를 거치며 가장 힘들었던 순간은? | 그 경험에서 구체적으로 무엇을 배웠나요? | `tving-2nd-interview-cpo-hr-panel-expected-questions.md` #3 |

## 2. 핵심 프로젝트 심화 추궁

| 프로젝트 | 예상 질문 | 예상 꼬리질문 |
|---|---|---|
| 아이돌 챗봇(블루밍톡) | MAU 5천 명이 신규 출시 성과인가, 기존 대비 증가분인가? | ① 그 정도가 어느 정도 성과인지 비교 사례는? ② 20명 표본으로 유의미하다고 본 근거는? ③ AB테스트(100명)는 어떤 기준으로 집단을 나눴나? ④ 북극성 지표는 무엇이었나? ⑤ 양적 지표(인터랙션Q) 외에 대화의 질적 측면도 봤나? |
| EV 충전 숏컷 추천 | 설명을 들어보면 단순히 즐겨찾기를 앞쪽에 배치한 것 아닌가? | ① 가까운 곳 대신 즐겨찾기를 쓰는 유인이 뭐라고 생각하나? ② 제휴 쿠폰 매출 16% 증가가 실제로 유의미한 변화가 맞나? |
| 건강디저트 추천 플랫폼 | 세그먼트를 4개로 나눈 기준은? 표본(200~300명)이 작은데 의미가 있나? | ① Elbow Method와 세그먼트 확정 로직의 관계는? ② 이게 PMF를 검증한 사례라고 할 수 있나, 아니면 추천 알고리즘 품질 검증인가? ③ coverage 82%의 의미는 — 인기상품만 보여주는 게 매출에 더 좋지 않나? |
| 사용량 대시보드(오비랩) | 대시보드를 만든 것과 매출 상승 간 인과관계를 어떻게 검증했나? | "휴먼리소스 절감 문제인데 왜 매출 KPI로 잡았나?" — **3개 회사에서 거의 동일한 논리로 공격받았고 아직 뚜렷한 개선 답변이 없는 최우선 보완 대상**(`interview-cross-company-pattern-analysis.md` 3절 ① 참고) |

## 3. 신규 제안(챗봇 에이전트 MVP) 완성도

| 예상 질문 | 예상 꼬리질문 | 상세 참고 |
|---|---|---|
| 티빙에 챗봇 에이전트를 만든다면 어떤 방향이 좋을까요? | ① 머신러닝 자체 로직인가, LLM API 활용인가? ② 할루시네이션·타사 작품 추천 같은 리스크는 어떻게 대응하나? | `tving-1st-interview-actual-transcript-structured.md` 9절 |
| 외부 바이럴 트렌드를 어떻게 탐지하나요? | ① 실제 적용 가능한 탐지 방법은? ② 임계치는 어떻게 정하나? ③ 동명이인·오탐은 어떻게 거르나? | `tving-viral-detection-methods-two-examples.md`, `tving-viral-detection-agent-tailquestions.md` |
| 팬톡 리뷰 기반 스포일러 방지는 어떻게 구현하나요? | ① 규칙 기반 필터링으로 암시적 스포일러도 거를 수 있나? ② 리뷰가 적은 신작은 어떻게 하나? | `tving-chatbot-agent-v3-mvp-tailquestions.md` |
| 이 MVP의 대상 세그먼트와 문제정의는 무엇인가요? | ① 왜 "방향감 없는 사용자"가 아니라 "고려 단계 사용자"부터 시작하나? ② 이 세그먼트의 모수가 충분히 큰가? | `tving-chatbot-agent-v3-combined-problem-definition-mvp-segment.md` |
| (구조화/기술 심화 질문 발생 시) 스포일러 판별에 쓸 만한 AI 모델이 있나요? | Jev 같은 비생성형 구조화 판단 모델의 한계(현재 얼리 액세스 단계)는 알고 있나? | `tving-interview-prep-discussion-kimhyunwoo.md` |

## 4. PM 정체성·개념 질문

| 예상 질문 | 예상 꼬리질문 | 상세 참고 |
|---|---|---|
| PM과 AI 엔지니어/모델러의 역할 경계를 어떻게 보나요? | 실제로 의견이 갈렸던 경험이 있나요? | `tving-interview-pm-modeler-boundary-two-answers.md` |
| "PM이냐 DA냐" — 데이터 분석 역할이 더 커보이는데 괜찮나요? | DA 역할이 80%여도 괜찮겠나? | `interview-cross-company-pattern-analysis.md` 3절 ③ — 4개 회사에서 반복, 아직 선명한 입장 정리 필요 |
| Product-Market Fit을 고려한 기획·경험이 있나요? | 그게 정말 시장이 원하는지 검증한 건가, 아니면 알고리즘/기능 품질 검증인가? | `tving-interview-pmf-experience-two-candidates-critique.md` |
| 통계적 유의성을 어떻게 검증했나요? (p-value, 표본크기) | 만족도(p<0.01)와 참여도(p<0.05)의 유의수준이 다른 이유는? | `tving-interview-pvalue-difference-two-answers.md` |

## 5. CPO 전략/비즈니스 임팩트 질문

| 예상 질문 | 예상 꼬리질문 | 상세 참고 |
|---|---|---|
| 디스커버리팀/챗봇 에이전트가 회사 전체 성장에 어떻게 기여하나요? | 콘텐츠 투자(오리지널, 중계권) 대비 왜 지금 이 기능에 투자해야 하나? | `tving-2nd-interview-cpo-hr-panel-expected-questions.md` #5, #6 |
| 과거 프로젝트 중 실패했다고 느낀 경험은? | 거기서 무엇을 배웠나? | 동 파일 #7 |
| 입사 후 90일 안에 가장 먼저 하고 싶은 일은? | — | 동 파일 #8 |

## 6. 인사(조직적응·근속·처우) 질문

| 예상 질문 | 예상 꼬리질문 | 상세 참고 |
|---|---|---|
| 팀 내 갈등을 조직 적응 관점에서 어떻게 해결했나요? | 타협 여지가 안 보일 때는 어떻게 하나요? | `tving-2nd-mock-interview-leejungwon-2026-10-15-structured.md` #29~30 |
| 입사 가능 시점과 희망 연봉은? | — | `tving-2nd-interview-cpo-hr-panel-expected-questions.md` #4 |
| 5년 뒤 어떤 모습이 되고 싶나요? | 10~15년 뒤는? | `tving-2nd-mock-interview-leejungwon-2026-10-15-structured.md` #33 |

## 7. 역질문 (지원자 → 면접관)

- 입사하게 된다면 구체적으로 어떤 업무/영역에 배치될 가능성이 있는지
- 챗봇 에이전트 아이디어가 실제로 추가될 계획이 있는지, 있다면 어느 시점을 보고 있는지

---

## 최우선 보완 포인트 Top 3 (아직 완성되지 않은 약점)

1. **사용량 대시보드(오비랩) 매출 인과관계** — 3개 회사에서 동일 논리로 공격받았고 아직 완전히 설득력 있는 답변이 정리되지 않음(`interview-cross-company-pattern-analysis.md` 3절 ① 참고, 별도 보완 필요)
2. **"PM이냐 DA냐" 정체성** — 4개 회사 반복, "둘 다 잘한다"는 애매한 답을 "1차적으로 PM, 데이터는 차별화 무기"로 통일 필요
3. **PMF 질문** — 후보 소재(아이돌 챗봇/건강디저트) 모두 구조적 허점이 있으므로, 질문의 정확한 의도(PMF를 찾은 경험 vs 키운 경험)를 먼저 파악하고 답하는 연습 필요

---
본 문서는 2차 면접 전체를 대비한 예상 질문·꼬리질문 종합 정리이며, 세부 답변은 각 참고 파일을 통해 확인할 수 있습니다.

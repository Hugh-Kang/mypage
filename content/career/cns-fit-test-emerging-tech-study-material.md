# CNS Fit Test 학습자료 — Emerging Technology 구조화 정리

> 자료 출처: LG CNS가 지원자에게 제공한 "Emerging Technology" 학습자료(PDF, 16p, Confidential)
> 정리일: 2026-10-03
> 성격: CNS Fit Test의 "전 직무 공통 — 글로벌 기술·산업 트렌드 이해도" 파트를 겨냥한 **공식 학습자료**이므로, 기존에 추정으로 채워뒀던 `lg-cns-fit-test-prep.md` §3보다 훨씬 신뢰도 높은 1차 자료입니다.
> 참고: `lg-cns-fit-test-prep.md`(필기전형 전체), `lg-cns-company-research.md`(LG CNS 자체 실적/전략), `lg-cns-2026-shinnyeonsa-analysis.md`(2026 신년사)

## 0. 전체 구조 한눈에

| 대분류 | 세부 구성 |
|---|---|
| 1부. '26년 IT Trends | Gartner(AI/Human Readiness, 2026 전략기술 Top10) + CES(Physical AI 등 5대 의제) + 향후 1~3년 주목 기술 Top5 |
| 2부. 세부 기술 동향 | Top5 기술 각각을 배경·정의·주요동향·사례로 심층 설명: ①Agentic AI ②AI-Native Software Engineering ③Physical AI ④Stablecoin ⑤양자컴퓨팅 |

자료 자체가 "1부(넓고 얕게) → 2부(Top5만 좁고 깊게)" 구조이므로, **이 문서가 꼽은 Top5가 사실상 출제 우선순위**라고 봐도 무방합니다.

---

## 1. '26년 IT Trends 개관

### 1-1. Gartner: AI Readiness·Human Readiness로 가치 창출

| 축 | 핵심 내용 |
|---|---|
| **AI Readiness** (기술적 준비) | ① 기술 준비도: AI 정확도 관리 + 전문가 수준 자율형 AI Agent 도입(관심이 "얼마나 빨리 도입하나"→"어디서 실질적 가치를 만드나"로 이동) <br>② 비용 관리: 구축비용 외 교육·조직변화·운영 단계 숨은 비용(토큰 과금 구조 특히 주의) <br>③ AI 벤더 선정과 AI 주권(AI Sovereignty): 목적에 맞는 파트너 전략 + 데이터·모델·생성결과를 기업이 통제·보호하는 역량 |
| **Human Readiness** (조직적 준비) | 인력 감축보다 **재훈련(Re-skill)과 조직 재설계**에 초점. AI Agent를 조직 내 하나의 역할 단위로 관리(권한·책임·성과 명확화) |
| **Autonomous Business(자율 비즈니스)** | 위 두 가지가 충족되면 도달하는 단계 — 단순 자동화를 넘어 AI가 상황을 판단·실행·지속개선. 기반 기술 4가지: ①IAM(Identity and Access Management, AI Agent를 조직 구성원처럼 관리) ②체화된 AI(Embodied AI, 로봇·자율주행용 인지-세계모델-행동조정) ③Digital Twin & Intelligent Simulation ④Tokenization(토큰화, 프로그램 가능 경제의 기반) |

### 1-2. Gartner — 2026년 전략 기술 Top 10

| # | 기술 | 한줄 요약 |
|---|---|---|
| 1 | AI-Native Development Platform | AI와 개발자가 협업해 애플리케이션을 신속 구현하는 차세대 개발환경 |
| 2 | AI Supercomputing Platform | CPU·GPU·ASIC 통합 고성능 컴퓨팅 인프라 |
| 3 | Confidential Computing | 데이터 처리 중에도 민감정보를 하드웨어 기반으로 보호 |
| 4 | Multi-Agent Systems | 다수의 전문화된 AI Agent가 역할을 나눠 협업 |
| 5 | Domain-Specific Language Models(DSLMs) | 특정 산업·기능에 특화된 고정확도·규제준수 AI 모델 |
| 6 | Physical AI | 로봇·드론·스마트장비 등과 결합해 물리세계에서 판단·행동 |
| 7 | Preemptive Cybersecurity | 공격을 사전에 예측·차단하는 예방형 AI 보안 |
| 8 | Digital Provenance | SW·데이터·AI 콘텐츠 출처 검증으로 디지털 신뢰 확보 |
| 9 | AI Security Platform | 제3자 AI서비스+자체 AI 앱을 통합 보호·관리 |
| 10 | Geopatriation | 데이터를 자국/지역 인프라로 이전해 데이터 주권·규제 대응 강화 |

### 1-3. CES 2026 — 5대 의제

1. **Physical AI** — NVIDIA 젠슨 황 "Physical AI의 ChatGPT 순간 도래" 선언. 현대차그룹 인수 보스턴다이내믹스 '아틀라스'(Best Robot상, 로봇 중심 기업 전환+2028년 연 3만대 생산 목표), LG전자 가정용 로봇 'CLOiD'(Zero Labor Home 비전)
2. **Industrial AI** — Siemens "AI가 산업의 새 운영체제" 선언, NVIDIA와 협업한 Digital Twin Composer로 공장·설비·라인 단위 실시간 디지털트윈 구현
3. **AIDV(AI Defined Vehicle)** — 차량을 AI 에이전트가 적용된 이동형 AI 플랫폼으로 재정의. NVIDIA 자율주행 플랫폼 '알파마요', Google의 AAA(차량용 AI Agent, Mercedes-Benz 협업 시연)
4. **양자컴퓨팅** — IBM·IonQ·QCI 등이 "완벽한 범용 양자컴퓨터를 기다리기보다 현재 가능한 기술로 산업 문제 해결"을 메시지로 제시, 하이브리드 구조(고전+양자) 확산
5. **휴먼 인터페이스** — 음성·뇌파 기반 차세대 제어 기술, AI 안경이 결제·쇼핑·광고 등 커머스 경험으로 확장

### 1-4. 향후 1~3년 주목 기술 Top 5 (2부에서 심층 다룸)
① Agentic AI ② AI-Native Software Engineering ③ Physical AI ④ Stablecoin ⑤ 양자컴퓨팅

---

## 2. 세부 기술 동향 (Top 5 심층)

### ① Agentic AI

- **배경**: 생성형 AI는 개인 생산성엔 도움 됐지만 조직 전체 성과로는 잘 안 이어지는 한계("생산성 누수, Productivity Leakage")가 있었음 → 이를 보완하려 목표 설정→계획 수립→실행→검증까지 스스로 하는 Agentic AI 등장
- **정의**: 최종 목표만 주어지면 계획-실행-결과검증까지 스스로 수행. 핵심은 **"계획-실행-검증"의 반복되는 자율 실행 구조**이며, 현재는 완전 독립이 아니라 사람의 감독(Human-in-the-loop) 하에 일정 수준 자율성을 갖는 형태가 일반적
- **주요 동향**
  1. **검증된 Pre-built Agent 확산** — 영업·고객상담·재무보고·IT운영·인사관리 등 특정 업무에 최적화된 Agent를 패키지로 도입(직접 설계 안 해도 됨). Accenture 'AI Refinery'가 대표 사례
  2. **단일 Agent → 다중 Agent(Multi-Agent) 오케스트레이션 구조로 진화** — 역할을 분담한 여러 전문 Agent가 협업(예: 대출심사에서 신용분석/소득검증/사기탐지 Agent가 각자 처리 후 의사결정 Agent가 종합)
  3. **엔터프라이즈 앱이 Agentic AI 중심 구조로 전환** — "메뉴 클릭·데이터 입력" 중심에서 "목표만 제시하면 Agent가 알아서 수행"하는 '목표 중심 서비스'로, UX도 클릭 기반에서 자연어·대화형으로 확장
- **대표 사례**
  - **Anthropic Claude Cowork**: 데스크톱 업무 실행형 AI, 자연어 목표 입력→로컬 파일 분석·보고서 작성·데이터 정리까지 수행하는 'AI 동료'형 도구
  - **OpenClaw**: 로컬 환경에서 파일정리·이메일발송·웹작업 등 실제 행동을 자연어 지시로 수행하는 오픈소스 Agent (사용자 권한을 직접 활용하므로 보안·권한관리·감사로그 설계가 중요)
  - **Accenture AI Refinery**: 산업·기능별 Agentic AI를 설계·운영하는 엔터프라이즈 플랫폼. Orchestrator-Super Agent-Utility Agent 계층 구조로 구성

### ② AI-Native Software Engineering

- **배경·정의**: 기존 AIDD(AI-Driven Development)가 설계보조·코드자동완성 등 "부분적" 생산성 개선이었다면, AI-Native Software Engineering은 **요구사항 정의부터 설계·개발·테스트·배포·운영까지 SDLC 전 과정**을 AI Agent가 수행하는 패러다임. LG CNS도 'AIND(AI-Native Development)' 개념을 도입해 추진 중
- **주요 동향**
  1. **바이브 코딩(Vibe Coding) 확산과 시민 개발자 부상** — 2025년 Andrej Karpathy가 명명. "이런 느낌의 앱을 만들어줘"처럼 자연어로 의도를 설명하면 AI가 코드로 구현 → 비전문가(기획자·도메인 전문가)도 직접 개발하는 시민 개발자(Citizen Developer) 확대
  2. **자율 코딩 Agent(Autonomous Coding Agent) 도입 확산** — Anthropic Claude Code가 대표 사례. 기능 요구사항을 자연어로 제시하면 작업을 분해해 실행계획 수립→코드 작성/수정→테스트 생성/실행→오류 시 원인분석·수정까지 반복
  3. **개발자 역할 변화** — 코드 작성자 → 시스템 설계자+AI와 협업을 조율하는 Orchestrator로 확장. AI가 생성한 코드 품질 검증, 전체 아키텍처 이해, 비즈니스 요구 해석 역량이 더 중요해짐
  4. **기업의 SW 구매 개념 변화** — 개발 속도·비용 장벽이 낮아지며 기존 SaaS 라이선스·구독 비용 재검토, 자체 구축 전환 사례 증가(글로벌 SaaS 기업 주가 하락 배경 중 하나로 지목)
- **AI-Native Development Platform**: 요구사항 정의부터 배포까지 자동화·가속하는 플랫폼(단일 Prompt 코드생성~바이브코딩~자율코딩 Agent 포괄). Gartner는 2030년까지 상당수 기업용 앱이 이 플랫폼 기반으로 구축될 것으로 전망

### ③ Physical AI

- **배경**: 과거 공장자동화 로봇은 정해진 환경에서 반복작업만 가능했지만, 최근 AI 인지·추론+강화학습으로 복잡한 동작을 학습 → 변화 많은 비정형 환경에서도 스스로 상황을 이해·개선하는 지능형 시스템으로 발전
- **정의**: 로봇·드론·스마트장비 등 물리 기계장치에 AI를 탑재해 **인지-판단-행동**의 전 과정을 AI가 수행. 구성은 HW(센서+구동장치)와 AI SW(환경이해+행동결정 알고리즘) 2부분
- **성공적 적용의 핵심요소 3가지**: ①데이터 기반 학습 체계 구축(현장 데이터 수집→학습→지속개선) ②다수 로봇의 통합 운영 역량 ③현장 맞춤형 로봇 배치 및 안전성 확보
- **주요 동향**
  1. **Sim2Real(Simulation to Reality)** — 가상환경에서 대규모 학습 후 현실 적용(현실 실험은 비용·위험 큼). 시뮬레이터-실제환경 간 괴리(성능저하) 해결을 위해 마찰·질량·조명 등을 무작위화하는 Domain Randomization 기법과 디지털트윈 병행
  2. **VLA(Vision-Language-Action) 모델 고도화** — 로봇의 "두뇌" 역할. 언어를 행동으로 변환하는 수준을 넘어 인지-판단-행동 통합 수행, 물리법칙 학습으로 물체 움직임 예측·실패가능성 고려, 촉각/힘 센서 등 멀티모달 정보로 정밀 조작까지 발전
  3. **로봇 학습 데이터 확보 기법 다양화** — Teleoperation(VR/조이스틱 원격조작), 가상 시뮬레이션 환경에서 데이터 생성, 인간 행동영상을 로봇 관절구조에 맞게 변환하는 Retargeting
  4. **월드 모델(World Model)** — 환경 상태변화 학습+미래상황 예측(예: 공을 던졌을 때 궤적, 젖은 노면에서 제동거리 예측). NVIDIA 'Cosmos'(로보틱스·자율주행용 월드 파운데이션 모델), Waymo도 자율주행에 월드모델 활용
  5. **이기종 로봇 통합 운영 플랫폼+오케스트레이션** — AMR·사족보행·이족보행 휴머노이드 등이 동시 운영되는 현장에서, 단일 로봇 제어를 넘어 전체 로봇 시스템을 효율 운영하는 역량(작업할당·경로최적화·충돌방지·배터리관리)이 중요. 오케스트레이션 = 각 로봇을 Agent로 보고 실시간 상태·작업 상황 분석해 최적 실행순서 결정·재배분하는 지능형 조정 기술
  6. **휴머노이드 로봇 대량생산·보급 확대** — 중국 유니트리 2025년 수천대 양산, 현대차·테슬라도 자동차 생산라인 투입 파일럿 진행(테슬라 '옵티머스' 연 100만대 생산 계획, 현대차 아틀라스 대량생산 목표 제시)

### ④ Stablecoin

- **배경·정의**: 달러·유로 등 법정화폐 가치에 연동해 가격 변동성을 최소화한 디지털 자산. 비트코인 등 기존 가상자산의 "변동성이 커서 결제수단으로 쓰기 어렵다"는 한계를 보완, 가상자산 생태계와 전통 금융시스템을 연결. 대표 사례: 테더(USDT, 최대 유동량), USD Coin(USDC, Circle사 발행, 투명한 준비금 공시 강조)
- **주요 동향**
  1. **규제 명확화를 통한 제도권 편입 가속** — EU의 MiCA(암호자산 규제안), 미국 'GENIUS Act' 등으로 발행자 준비금 요건·공시의무 규정. 한국은 한국은행이 CBDC 실험을 병행하면서 금융위원회 중심으로 스테이블코인 제도화 방안 논의 중
  2. **글로벌 결제망 편입 확대** — Mastercard가 Circle 발행 USDC를 자사 결제망에 통합하는 파일럿 진행, Visa도 일부 금융기관과 USDC 기반 정산 시험
  3. **CBDC와의 공존·역할분담 논의** — "CBDC는 공공·도매 거래 중심, 민간 스테이블코인은 소매결제·혁신서비스 중심"이라는 구조 형성 가능성
  4. **AI Agent 시대의 Programmable Money로서 역할 확대** — 사전 정의된 조건 충족 시 자동으로 결제·정산되는 스마트계약 기반 디지털화폐. AI Agent가 인간 대신 계약체결·결제·정산·자산운용을 수행하는 환경이 확대되면 스테이블코인이 이를 구현하는 핵심 금융 인프라가 될 가능성 (궁극적으로 Programmable Economy로 확장 전망)

### ⑤ 양자컴퓨팅

- **배경·정의**: 양자중첩·양자얽힘 원리로 정보를 처리하는 차세대 계산기술. 기존 컴퓨터는 0/1의 비트, 양자컴퓨터는 0과 1의 중첩상태를 가지는 큐비트 활용. 소인수분해, 복잡한 분자구조 시뮬레이션, 조합최적화 문제 등에서 기존 컴퓨터보다 훨씬 효율적인 계산 가능 — 암호체계, 신약개발, 신소재 연구 등에 영향
- **주요 동향**
  1. **실험 단계를 넘어 실용적 양자컴퓨팅(Useful Quantum Computing)으로 전환** — 2026년을 실험실 연구→실제 산업 적용 전환점으로 평가. 금융(리스크분석/포트폴리오 최적화), 물류(경로최적화/재고관리), 제약(분자시뮬레이션) 등에서 시범 적용 확대, 투자도 연구중심 스타트업→기업으로 이동
  2. **양자 AI(Quantum AI) 연구 확대** — 양자컴퓨팅으로 AI의 일부 계산을 개선·가속. 최적화·확률계산 등 특정 연산에서 양자알고리즘 적용 시도
  3. **고전-양자 결합형 하이브리드 아키텍처와 QaaS(Quantum-as-a-Service) 확산** — 일반 연산은 고전컴퓨터, 고난도 최적화·시뮬레이션은 양자컴퓨터가 수행하는 역할분담. 클라우드 기반 양자컴퓨팅 자원 제공(QaaS)도 확대
  4. **오류 보정 기술 고도화를 통한 내결함성(Fault-Tolerant) 양자컴퓨팅 경쟁 심화** — 큐비트는 외부환경에 민감해 연산 중 오류 발생이 쉬움. 오류보정 적용된 내결함성 양자컴퓨터 확보가 대규모·장시간 연산(본격 상용화)의 전제조건
  5. **양자 위협 대응을 위한 양자 안전 보안(Quantum-Safe Security) 체계 전환 가속** — 양자컴퓨터가 기존 공개키 암호체계를 위협할 가능성 제기됨에 따라, 양자내성암호(Post-Quantum Cryptography, PQC) 표준화와 양자키분배(QKD) 기반 통신망 구축 가속

---

## 3. 암기 우선순위 제안

학습자료 자체의 구조(1부 넓게 vs 2부 Top5 깊게)를 근거로 우선순위를 매기면:

| 순위 | 항목 | 이유 |
|---|---|---|
| 1 | **Top5 기술 5개의 정의 한 줄씩 + 각 기술의 대표 사례 1개씩** | 자료가 가장 많은 분량(10p/16p)을 할애한 핵심. 정의를 정확히 말할 수 있어야 함 |
| 2 | **Gartner 2026 전략기술 Top10 명칭 전체 암기** (한글 설명은 대략) | 객관식 문제라면 "다음 중 2026 전략기술이 아닌 것은?" 류 출제 가능성 |
| 3 | **Agentic AI의 "계획-실행-검증" 구조 + Pre-built Agent·Multi-Agent 개념 차이** | Top5 중 LG CNS 자체 전략(에이전틱 AI 플랫폼)과 가장 직접 연결됨 |
| 4 | **Physical AI 핵심요소 3가지 + VLA/World Model 개념** | LG CNS의 RX(로봇전환) 전략과 직접 연결됨 |
| 5 | CES 5대 의제, Stablecoin, 양자컴퓨팅 세부 동향 | 상대적으로 비중 낮지만 객관식 보기로 등장 가능 |

## 4. Entrue 컨설팅 관점 연결 포인트 (자소서·면접 소재로도 활용 가능)

| 이 자료의 기술 | LG CNS 자체 전략과의 연결 (기존 리서치 참고) |
|---|---|
| Agentic AI | 2026 컨퍼런스콜의 "에이전틱 AI 플랫폼" 비계열 사업 확대 전략과 직결 (`lg-cns-company-research.md`) |
| Physical AI | 2026 신년사의 "RX(로봇전환)" 신규 축, 피지컬 AI 투자(`lg-cns-2026-shinnyeonsa-analysis.md`) |
| AI-Native Software Engineering(바이브코딩) | "AI 서비스 기획 시 문제정의가 먼저"라는 본인 자소서 철학과 직결 — 비개발자도 자연어로 개발하는 시대엔 "무엇을 만들지 정의하는 역량"이 더 중요해진다는 논리로 자소서/면접에 활용 가능 |
| DSLM(산업특화 모델) | Entrue의 "산업별 특화 컨설팅"이라는 포지셔닝과 개념적으로 연결 |

## 5. 빠른 점검용 한 줄 정의 체크리스트

- [ ] Agentic AI = 목표만 주면 계획·실행·검증까지 스스로 수행하는 AI (사람 감독 하 자율성)
- [ ] AI-Native Software Engineering = SDLC 전 과정(요구정의~운영)을 AI Agent가 수행하는 개발 패러다임
- [ ] Physical AI = 인지-판단-행동을 물리 기계장치에서 수행하는 AI (HW+AI SW)
- [ ] Stablecoin = 법정화폐 연동으로 가격변동성을 낮춘 디지털자산, AI 시대엔 Programmable Money로 확장
- [ ] 양자컴퓨팅 = 큐비트의 중첩·얽힘으로 특정 문제를 고전컴퓨터보다 효율적으로 계산하는 차세대 패러다임
- [ ] AI Readiness ≠ Human Readiness — 기술 준비와 조직 준비는 별개 축이며 둘 다 충족돼야 Autonomous Business 도달
- [ ] Pre-built Agent(기성 패키지) vs Multi-Agent(역할분담 협업 구조) 구분
- [ ] Sim2Real, VLA, World Model — Physical AI의 3대 핵심 키워드

## 6. 객관식(Emerging Tech Knowledge Test, 8문항) 유형별 체크리스트 — D-1 최종점검

`cns-fit-test-mock-questions.md`(Q1~50, R1~10)·`cns-fit-test-platform-prep.md`(P1~20) 총 80문항을 풀어보며 드러난 **출제 유형 6가지**와 유형별 주의점입니다.

### 유형 A — 단순 정의형 ("~은 무엇을 의미하는가")
**대상**: Agentic AI, Physical AI, Stablecoin, 양자컴퓨팅, DSLM, AI Sovereignty, Quantum AI 등
**주의점**: 정확한 한 줄 정의를 외우되, "완전 자동", "인간 개입 전혀 없음", "독립적으로만" 같은 **극단적 표현은 오답 함정**으로 반복 등장합니다. Agentic AI는 "Human-in-the-loop 하 일정 자율성"이 정답이지 "완전 독립"이 아닙니다.
**참고**: Q1, R1, P1, Q43

### 유형 B — "다음 중 포함되지 않는 것은" 리스트형
**대상**: Gartner Top10(10개), Autonomous Business 4대 기반기술(4개)
**주의점**: 리스트를 통암기해야 하며, **그럴듯하게 지어낸 가짜 항목**이 오답 함정으로 나옵니다 — 'Blockchain-as-a-Service', 'Agentic Workforce Platform', 'Blockchain Consensus Protocol' 같은 이름은 실제로 자료에 없습니다. "블록체인/에이전트가 들어간 단어니까 있을 것 같다"는 느낌만으로 고르지 말 것.
**참고**: Q4, Q44, R6, Q11, P5

### 유형 C — "옳지 않은 것을 고르시오" 부정형
**대상**: 거의 모든 주제에 적용 가능
**주의점**: 보기 중 1개가 **예외조항을 거꾸로 적용**하거나 **방향을 반전**시킨 경우가 많습니다(예: "양자컴퓨팅은 완벽한 범용컴퓨터 상용화 후에야 적용 시작" — 실제는 정반대). "~한 뒤에야", "전혀", "반드시 ~해야만" 같은 단정적 표현이 보이면 자료와 대조해보는 습관이 필요합니다.
**참고**: P2, P6, P7, R7, R8, R9, R10

### 유형 D — 사례·개념 매칭형 (헷갈리는 짝)
아래 짝은 이름이나 맥락이 비슷해 혼동하기 쉬우므로 **반드시 짝으로 구분 암기**:

| 헷갈리는 짝 | 구분 포인트 |
|---|---|
| Claude Cowork vs Claude Code | Cowork=데스크톱 업무실행 'AI동료' / Code=자율 코딩 Agent |
| Teleoperation vs Retargeting | Teleoperation=VR·조이스틱 원격조작 / Retargeting=인간행동영상→로봇관절 변환 |
| NVIDIA 알파마요 vs NVIDIA Cosmos | 알파마요=AIDV 자율주행 플랫폼 / Cosmos=Physical AI 월드 파운데이션 모델 |
| Siemens Digital Twin Composer vs Google AAA | Siemens=Industrial AI(공장) / Google AAA=AIDV(차량) |
| 보스턴다이내믹스 아틀라스 vs LG전자 CLOiD | 아틀라스=Best Robot상·2028년 3만대 목표 / CLOiD=Zero Labor Home 가정용 |
| Pre-built Agent vs Multi-Agent | 전자=기성 패키지형 / 후자=역할분담 협업 구조 |
| MiCA vs GENIUS Act | MiCA=EU 규제 / GENIUS Act=미국 입법 |
| PQC vs QaaS vs Quantum AI | PQC=양자내성암호 표준화 / QaaS=클라우드 양자자원 제공 / Quantum AI=AI계산 가속 연구 |

**참고**: R5, P14, Q39, Q47, Q42

### 유형 E — 순서·구조형
**대상**: Accenture AI Refinery 계층구조(Orchestrator→Super Agent→Utility Agent), AI Readiness·Human Readiness 2축 구분(둘 다 충족해야 Autonomous Business 도달)
**주의점**: 순서를 뒤바꾼 보기가 오답으로 등장. "~가 먼저"처럼 선후관계를 묻는 문제는 구조를 정확히 외워야 함
**참고**: R3, R4, Q50

### 유형 F — 숫자·전망형
**대상**: Gartner 2030년 전망(AI-Native Dev Platform), 테슬라 옵티머스 연 100만대 계획, 유니트리 2025년 수천대 양산, 현대차 아틀라스 2028년 3만대 목표
**주의점**: "이미 완료"와 "목표로 제시"를 혼동하는 보기가 함정 — 테슬라·현대차는 아직 파일럿 단계이지 유니트리처럼 양산을 완료한 게 아님
**참고**: Q45, P7, P15

### 시험 당일 운용 전략
1. 8문항은 **출제비중이 가장 높은 Top5 기술(Agentic AI·AI-Native SW Eng·Physical AI·Stablecoin·양자컴퓨팅) 정의부터** 머릿속에 정리하고 입실
2. 객관식엔 **AI 사용이 금지**되므로, 순수 암기로 가능한 한 빨리(목표 10분 내외) 끝내고 남은 시간을 서술형에 투입
3. 헷갈리면 유형C(부정형)의 "극단적 표현" 패턴과 유형D(매칭형) 비교표를 떠올려 소거법 적용
4. 확신이 안 서는 리스트형(유형B) 문제는 "자료에 없는 그럴듯한 이름"부터 제외하는 방식으로 접근

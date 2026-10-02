# Contribution Matrix — 신경호

이 문서는 팀 프로젝트에서 **내가 책임 있게 설명할 수 있는 범위**와 **팀이 구현한 범위**를 분리하기 위해 작성했습니다.

## 1. 근거 기준

기여 범위는 다음 세 가지를 함께 확인해 정리했습니다.

1. 최종 팀 README의 역할 표
2. WBS의 담당자 표기
3. 최종 ZIP의 실제 Frontend 코드와 화면 흐름

최종 README에는 다음과 같이 기록되어 있습니다.

- 신경호: **프론트엔드 · 발표자료**
- 담당 업무: **서비스 화면 구현, 사용자 인터페이스 구성, 발표자료 준비**
- WBS 프론트엔드 구현: **신경호·류지예**
- WBS AI 챗봇 구현: **김형준·프론트엔드**

따라서 파일 단위의 단독 저작권을 주장하기보다, **기능 단위로 기여 성격을 구분**했습니다.

---

## 2. Contribution Matrix

| 영역 | 최종 구현에서 확인한 내용 | 내 기여 표현 | 팀 구현/협업 범위 | 신뢰도 |
|---|---|---|---|---|
| 공통 Layout | profile rail, topbar, bookmark navigation, 공통 data ribbon | UI 구성·고도화 | Django context, auth | 높음 |
| HOME | 운동방, quick recommendation, 기록/레벨 상태, 친구 한마디 | 화면/interaction 공동 구현 | 기록 API, 레벨 계산, room state 저장 | 높음 |
| 추천 Form | 지역/GPS mode, 종목, 시간, 이동수단 입력 | Frontend UX·상태 처리 | 추천 API/DB | 높음 |
| 추천 결과 | score, reasons, operation notice, paging | 결과 카드/상태 UI | 추천 점수 산출 | 높음 |
| 추천 상세 | breakdown, 환경 수치, AED/안전정보 | explainability UI | 환경/안전 데이터 제공 | 높음 |
| 장소 결정 | 선택 저장 → 카카오맵 새 탭 | browser interaction/API 연동 | 선택 저장 API | 높음 |
| AI 코치 | NPC launcher, chat panel, quick prompt, typing, recommendation card | UI/interaction/front API integration | OpenAI, 처방 DB, prompt/server context | 높음 |
| 프로필 | 캐릭터/분위기/지역/종목/이동 설정 UI | Frontend 공동 구현 | 저장 로직 | 높음 |
| 친구 | 친구 코드 조회/요청 UI, 요청 modal | Frontend 공동 구현 | friend model/API | 높음 |
| 방 꾸미기 | drag/drop, item/skin UI, level lock 표현 | Frontend interaction 공동 구현 | server persistence/level API | 중~높음 |
| 공공데이터 출처 | 5개 기관 data provenance ribbon | UI 표현/링크 구성 | 실제 데이터 수집 | 높음 |
| 발표자료 | 문제→데이터→추천→파이프라인→결과 시각화 | 자료 구성 공동 담당 | 팀 기술 내용 검토 | 높음 |
| 데이터 파이프라인 | RAW/PROCESSED/DQ/Scheduler | **내 구현으로 주장하지 않음** | 데이터 엔지니어링 담당 | 명확 |
| 추천 알고리즘 | 규칙 기반 score | **내 구현으로 주장하지 않음** | Backend/팀 | 명확 |
| DB/PostGIS | Supabase PostgreSQL, spatial query | **내 구현으로 주장하지 않음** | Data/Backend | 명확 |
| OpenAI server logic | prescription DB search + Responses API | **내 단독 구현으로 주장하지 않음** | Backend + Frontend 협업 | 명확 |

---

## 3. 면접에서 사용하는 표현

### 적절한 표현

- “추천 알고리즘을 **사용자가 이해할 수 있는 카드와 상세 근거 UI로 연결했습니다.**”
- “AI 코치의 **Frontend 인터랙션과 Django API 연동 UI를 구현·고도화했습니다.**”
- “프론트엔드 2명이 공동 담당했고, 저는 특히 **서비스 화면 구성, 추천 결과 표현, 캐릭터 기반 UI와 발표자료**에 집중했습니다.”
- “Backend가 계산한 데이터가 화면에서 어떤 의미로 보일지 고민했습니다.”

### 피해야 할 표현

- “추천 알고리즘을 제가 개발했습니다.”
- “공공데이터 파이프라인을 제가 구축했습니다.”
- “AI 운동처방 시스템을 제가 전부 개발했습니다.”
- “Frontend 전체를 혼자 만들었습니다.”

---

## 4. 코드 리뷰 포인트

면접에서 코드 질문을 받으면 다음 순서로 설명하는 것이 좋습니다.

1. `recommend.js` — 입력 → 요청 → 카드 → 상세 → 결정
2. `chatbot.js` — 안전한 출력 → NPC layout → async API
3. `base.html` — 서버 context + 공통 UI shell
4. `home.js` — local/server state가 섞이는 실제 제품형 Frontend의 trade-off

이 저장소의 `snippets/`는 위 흐름을 빠르게 리뷰하도록 만든 **최종 코드 발췌본**입니다.

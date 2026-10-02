# Improvement Roadmap

최종 프로젝트를 포트폴리오 관점에서 다시 개발한다면, 기능을 더 많이 넣기보다 **Frontend 구조·품질·측정 가능성**을 먼저 개선하고 싶습니다.

## 1. 단기 — Frontend 구조 개선

### 1-1. JavaScript module 분리
현재는 화면별 IIFE와 `window.USIMUNKKA` 전역 객체를 통해 기능을 공유합니다. 빠른 프로젝트에는 실용적이지만 기능이 늘수록 상태 추적이 어려워질 수 있습니다.

개선:
- `api/`, `state/`, `components/`, `pages/` 단위 ES Module 분리
- 공통 fetch wrapper에서 timeout/error/CSRF 처리
- profile, recommendation, room state의 source of truth 명확화

### 1-2. Design token 정리
현재 CSS는 미니홈피 콘셉트를 빠르게 구현하기 위해 큰 스타일 파일과 세부 selector가 많습니다.

개선:
- color, radius, shadow, spacing, typography token 정의
- 버튼/카드/form/modal/NPC panel을 component class로 통합
- CSS cascade 의존도를 줄이고 responsive rule을 component 단위로 배치

### 1-3. Legacy template 정리
최종 ZIP에는 `frontend/templates/frontend/`와 `frontend/templates/pages/`가 함께 존재하고, legacy route 호환 코드도 남아 있습니다.

개선:
- 실제 사용 route/template inventory 작성
- 미사용 template과 legacy view 제거
- 화면별 URL → view → template → JS/CSS dependency를 문서화

---

## 2. 단기 — UX/Accessibility 개선

- chat/dialog open 시 focus management 강화
- 모든 custom control keyboard 조작 점검
- `prefers-reduced-motion` 적용
- 색 대비와 200% zoom 테스트
- error/loading/empty state를 공통 component로 통합
- 모바일에서 NPC와 본문 충돌을 device matrix로 검증

목표:
- Lighthouse Accessibility 95+
- 주요 Flow keyboard-only 완주

---

## 3. 중기 — 추천 신뢰도 표현 강화

현재 추천 UI는 점수와 이유를 설명합니다. 다음 단계에서는 “데이터가 얼마나 최신인지”까지 보여주고 싶습니다.

추가 UI:
- 운영공지 확인 시각
- 데이터 출처 badge
- 실시간/최근 수집/확인 불가 상태
- 추천 점수 confidence 또는 data completeness

또한 이동시간은 현재 단순 추정이므로, 실제 경로 API를 사용해 **거리와 소요시간의 정확도**를 개선할 수 있습니다.

---

## 4. 중기 — Feedback loop

추천을 보여주는 것에서 끝나지 않고 실제 유용성을 측정합니다.

수집 후보:
- 추천 카드 노출
- 상세 보기
- 시설 선택
- 지도 이동
- 운동 기록 전환
- “추천이 도움 됐나요?” feedback

주의:
클릭을 실제 방문이나 운동 완료로 간주하지 않고, 각 이벤트 의미를 구분합니다.

---

## 5. 중기 — AI Coach UX 고도화

현재 Frontend는 request/response 형태입니다.

개선:
- streaming response
- 요청 취소(AbortController)
- retry / offline state
- 근거가 있는 답변에 source badge
- 시설추천과 일반 운동방법 답변의 UI type 구분
- 위험 신호 안내를 일반 답변과 시각적으로 분리

Backend AI 구조는 팀 영역이므로, Frontend에서는 **응답 상태와 근거 전달 방식**을 책임지는 방향으로 확장합니다.

---

## 6. 중장기 — Test automation

### E2E
Playwright 기준 핵심 시나리오:

1. 로그인 → HOME
2. 추천 조건 입력 → 결과
3. 상세 → 결정 → 지도 새 탭
4. AI 코치 open → 질문 → 응답 → clear
5. 칼로리 기록 → level UI 갱신
6. 친구 조회 → 요청 modal

### Visual regression
- HOME room
- recommendation card
- AI coach panel
- profile form

캐릭터 중심 UI는 CSS 변경 시 시각적 regression이 발생하기 쉬워 screenshot test 효과가 큽니다.

---

## 7. 중장기 — Product 확장

- PWA 설치 및 운동 알림
- 개인 추천 history
- 즐겨찾기/나중에 가기
- 시설 운영정보 사용자 제보 + 검증 상태
- 운동 후 실제 만족도 기록
- 지역별 운동수요 dashboard

다만 기능 확장보다 먼저 **추천 품질 측정과 Frontend 품질 자동화**를 갖춘 뒤 진행하는 것이 우선이라고 생각합니다.

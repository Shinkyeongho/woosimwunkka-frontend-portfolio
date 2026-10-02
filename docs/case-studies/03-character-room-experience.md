# Case Study 03 — 운동 기록을 캐릭터/방 성장과 연결하기

## Problem

시설을 한 번 추천받는 것만으로는 사용자가 서비스를 다시 방문할 이유가 약합니다.

## Decision

운동 기록 → 누적 칼로리 → 레벨 → 캐릭터/방 보상으로 이어지는 시각적 피드백을 HOME에 배치했습니다.

## Frontend focus

- 프로필 rail에서 사용자 상태 요약
- 운동방 item/character visual
- 기록 입력과 progress UI
- unlock/locked 상태 표현
- 꾸미기 panel과 draggable layout
- server state가 있으면 동기화하고 local UI state를 보완적으로 활용

## Boundary

레벨 계산 공식과 저장 API는 Backend 영역입니다. Frontend에서는 해당 상태를 **사용자가 즉시 이해할 수 있는 진행도/보상 UI**로 표현합니다.

# Case Study 01 — 추천을 설명 가능한 UI로 바꾸기

## Problem

점수만 높은 시설을 나열하면 사용자는 추천을 믿기 어렵습니다. 특히 날씨와 대기질처럼 눈에 보이지 않는 조건이 순위에 영향을 주면 근거가 더 필요합니다.

## Decision

카드는 빠른 선택을 위한 핵심 정보만 유지하고, 상세 dialog에서 계산 근거와 원시 환경 수치를 확인할 수 있도록 **2단계 정보 계층**을 사용했습니다.

## Implementation

- 카드: 순위, 종목, 시설명, 이동시간, indoor/outdoor, score, reasons, 운영공지
- 상세: score breakdown, 기온, 습도, 강수, 풍속, PM10, PM2.5, AED, 안전점검
- 서버 문자열은 escape 후 렌더링
- 데이터가 없으면 빈 값을 숨기기보다 “확인 가능한 데이터 없음”으로 표시

## Result

사용자는 “83점”이라는 숫자뿐 아니라, **거리/환경/운영정보 중 무엇이 점수에 영향을 줬는지** 확인할 수 있습니다.

## What I learned

Explainable recommendation은 Backend의 계산식만으로 끝나지 않습니다. Frontend가 근거의 우선순위와 상태를 제대로 표현해야 설명 가능성이 실제 사용자 경험이 됩니다.

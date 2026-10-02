# Case Study 02 — AI 코치를 서비스 맥락 안에 배치하기

## Problem

AI 기능을 별도 페이지로 이동시키면 추천 조건과 결과를 보던 사용자가 맥락을 잃습니다. 반대로 일반적인 floating chat window는 본문을 가릴 수 있습니다.

## Decision

AI 코치를 **게임 NPC처럼 페이지 오른쪽에 상주**시키고, 넓은 화면에서는 메인 프레임 우측의 남는 공간을 계산해 chat panel을 배치했습니다.

## Implementation

- launcher / teaser / panel로 상태 분리
- wide viewport: `shellRect.right`부터 scrollbar 직전까지 실제 폭 계산
- narrow viewport: fixed width fallback
- draggable dock + localStorage persistence
- typing indicator, quick prompt, recommendation card
- assistant text HTML escape 후 제한된 formatting 적용

## Result

추천/프로필 화면을 그대로 보면서 질문할 수 있고, NPC가 서비스 캐릭터 경험을 이어갑니다.

## What I learned

AI 기능은 모델 정확도만으로 UX가 결정되지 않습니다. **어디에 배치하고, 언제 열리고, 기존 작업 흐름을 얼마나 방해하지 않는지**도 제품 경험의 일부입니다.

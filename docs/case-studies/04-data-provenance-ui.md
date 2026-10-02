# Case Study 04 — 데이터 출처를 서비스 UI에 노출하기

## Problem

우심운까의 핵심은 공공데이터 결합이지만, 화면에서 출처가 보이지 않으면 사용자는 서비스가 어떤 데이터를 기반으로 하는지 인지하기 어렵습니다.

## Decision

공통 shell 하단에 source ribbon을 두고 주요 기관을 5개로 정리했습니다.

1. KSPO
2. DATA.GO.KR
3. CULTURE DATA
4. KMA
5. AirKorea

## UI considerations

- 프로젝트 목적과 가장 직접적인 기관을 앞에 배치
- 복잡한 설명 대신 짧은 기관명과 source category 사용
- 카드 전체를 공식 사이트 link로 구성
- 전체 서비스 색상과 맞는 green/cream tone 유지
- responsive grid로 5 → 3 → smaller layout 대응

## What I learned

Data provenance는 문서에만 적는 항목이 아니라 **사용자 신뢰와 프로젝트 정체성을 화면에서 전달하는 정보**가 될 수 있습니다.

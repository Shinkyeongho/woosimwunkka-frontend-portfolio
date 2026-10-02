# Portfolio Construction Plan

## 분석 결론

최종 ZIP을 코드 기준으로 확인했을 때, 개인 포트폴리오는 팀 프로젝트 전체를 다시 복제하기보다 **Frontend contribution을 문서화하고, 실제 코드 발췌와 최종 화면을 증거로 연결하는 구조**가 가장 적합합니다.

그 이유는 다음과 같습니다.

1. 최종 README에서 신경호의 역할이 `프론트엔드 · 발표자료`로 명확함
2. Frontend는 신경호·류지예의 공동 담당이므로 전체 Frontend 파일을 단독 작업으로 표시하면 과장될 수 있음
3. ZIP에는 `.git` history가 없어 line-by-line 개인 저작을 증명할 수 없음
4. 반면 추천 UI, AI 코치 UI, 공통 shell, 캐릭터 interaction은 실제 코드에서 충분히 기술적으로 설명 가능함

## 포트폴리오 전략

### 포함
- 대표 서비스 screenshots
- 추천/AI Coach/UI case study
- 실제 final code excerpt
- contribution matrix
- 발표 협업 산출물
- 개선 roadmap
- 기술면접 Q&A
- 보안 검수 결과

### 제외
- 전체 Backend 복제
- 전체 데이터 파이프라인 복제
- 모든 캐릭터/음원 대용량 asset
- 실제 secrets/env
- “Frontend 전체 단독 구현”처럼 오해될 수 있는 표현

## 읽는 사람 기준 1~2분 동선

`README hero` → `My Role` → `Key Contribution 01/02` → `Contribution Matrix` → 필요 시 code snippet/case study

## Repository name

추천: `woosimwunkka-frontend-portfolio`

명확한 이유:
- 원본 프로젝트와 혼동되지 않음
- 역할(Frontend)이 즉시 보임
- backup repo와 목적이 구분됨
- 채용 담당자가 repository name만 보고도 성격을 이해하기 쉬움

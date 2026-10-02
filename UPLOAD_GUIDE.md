# GitHub Upload Guide

이 포트폴리오는 기존 백업 저장소 `Shinkyeongho/WooSimWunKka`와 **완전히 별도**로 업로드해야 합니다.

추천 저장소 이름:

`woosimwunkka-frontend-portfolio`

## 1. GitHub에서 새 Public Repository 생성

- Owner: `Shinkyeongho`
- Repository name: `woosimwunkka-frontend-portfolio`
- Visibility: `Public`
- README / .gitignore / License: **초기 생성 시 추가하지 않음**

## 2. Git Bash

ZIP을 원하는 폴더에 푼 뒤 해당 폴더에서:

```bash
git init
git add .
git commit -m "docs: publish WooSimWunKka frontend contribution portfolio"
git branch -M main
git remote add origin https://github.com/Shinkyeongho/woosimwunkka-frontend-portfolio.git
git push -u origin main
```

## 3. 업로드 후 확인

- README 이미지가 모두 표시되는지
- Mermaid diagram이 렌더링되는지
- Team Repository 링크가 동작하는지
- `snippets/`가 “sole authorship”으로 오해되지 않도록 안내문이 보이는지
- `.env`, API key, DB URL이 없는지

## 4. 기존 백업 Repository

`Shinkyeongho/WooSimWunKka`에는 **아무 작업도 하지 않습니다.**

두 저장소의 목적:

- `WooSimWunKka` → 팀 프로젝트 전체 장기 백업
- `woosimwunkka-frontend-portfolio` → 채용/면접용 개인 기여 포트폴리오

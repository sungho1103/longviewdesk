# 롱뷰 데스크 (Longview Desk)

중장기 관점의 종목 리서치 & 보유 포트폴리오 관리 대시보드.
빌드 과정 없이 순수 HTML/CSS/JS 한 파일로 동작하는 [Claude Artifact](https://claude.ai/code/artifact/a4915ac4-982d-4ebc-8b97-a990688cb7a0)입니다.

## 라이브 버전

https://claude.ai/code/artifact/a4915ac4-982d-4ebc-8b97-a990688cb7a0

이 저장소는 위 라이브 아티팩트 소스의 백업/버전 관리 용도입니다. 실제 사용 및 데이터 갱신은 위 링크에서 이루어집니다.

## 구조

- `index.html` — 전체 앱 (마크업 + 스타일 + 로직)이 한 파일에 들어있습니다. 별도 빌드/번들링 없음.

## 데이터 저장 방식

앱은 [Claude Artifact `db`/`user` capability](https://claude.ai)를 통해 클라우드(계정 기준)에 관심 종목·보유 종목 데이터를 저장합니다 (`window.claude.use("db")`). 이 API는 claude.ai 아티팩트 iframe 안에서만 제공되므로, 이 파일을 GitHub Pages나 로컬에서 그냥 열면 `db` capability가 없어 자동으로 브라우저 `localStorage` 저장으로 대체(fallback)됩니다 — UI 확인용으로는 문제없지만, 클라우드 동기화는 되지 않습니다.

## 갱신 자동화

가격/이슈 라이트 갱신은 Claude 대화창에서 "갱신해줘"라고 요청하거나, 매일 새벽 자동으로 도는 클라우드 루틴을 통해 이루어집니다 (이 저장소의 코드와는 별도로 운영).

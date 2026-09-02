# Module 01 미션 보드

모든 학생은 **Core 미션**, 아래 **선택 미션 중 최소 1개**, **팀 미션**을 수행합니다. 시간이 남는 팀은 선택 미션을 2개 이상 진행하세요.

## 0. 명령 준비 운동

프로젝트를 열기 전에 다음 명령을 직접 실행하고, 각 결과가 무엇인지 짝에게 설명합니다.

~~~bash
pwd
ls
cd team-intro-팀번호
git remote -v
git status
git branch
~~~

- `pwd`: 현재 폴더의 전체 주소
- `ls`: 현재 폴더 안의 항목
- `remote -v`: 연결된 GitHub 원격 주소
- `status`: 현재 Branch와 변경 상태
- `branch`: Local Branch 목록. `*`가 현재 위치

## 1. Core — 개인 소개 페이지

**수정 위치**: `members/member-번호.html`

**채울 TODO**

- `<title>`과 `<h1>`에 실제 이름
- 2~3문장의 소개
- 관심 기술 3개
- 실제 GitHub 주소
- `projects/project-번호.html`로 가는 링크

**사용할 명령**

~~~bash
git branch feature/member-번호
git checkout feature/member-번호
git status
git diff -- members/member-번호.html
git add members/member-번호.html
git diff --staged
git commit -m "feat: 번호번 팀원 소개 페이지 완성"
git log --oneline --graph --all -8
git push -u origin feature/member-번호
~~~

**완료 기준**: 모바일에서 읽을 수 있고, 팀 홈·GitHub·프로젝트 링크가 동작하며, PR에 변경 이유와 확인 방법이 적혀 있습니다.

## 2A. 선택 — 미니 프로젝트 기획 페이지

**수정 위치**: `projects/project-번호.html`과 내 `members/member-번호.html`

프로젝트가 해결하는 문제, 예상 사용자, 핵심 기능 3개, 다음 버전 아이디어를 채웁니다. 두 파일이 하나의 기능을 완성하므로 파일명을 모두 지정해 Stage합니다.

~~~bash
git branch feature/project-번호
git checkout feature/project-번호
git diff
git add projects/project-번호.html members/member-번호.html
git diff --staged
git commit -m "feat: 번호번 미니 프로젝트 소개 추가"
~~~

## 2B. 선택 — 버그 재현과 수정

**수정 위치**: 내 페이지의 링크 또는 텍스트 한 곳

잘못된 상대경로를 하나 만들어 어떤 클릭에서 실패하는지 확인한 뒤 고칩니다. Issue와 PR에 `재현 순서 → 원인 → 수정 → 확인`을 기록합니다.

~~~bash
git branch fix/member-번호-link
git checkout fix/member-번호-link
git diff -- members/member-번호.html
git add members/member-번호.html
git commit -m "fix: 번호번 페이지 프로젝트 링크 경로 수정"
~~~

상대경로는 **현재 HTML 파일 위치를 기준으로 목적지까지 가는 주소**입니다. `members/`에서 한 단계 위로 갈 때는 `../`를 사용합니다.

## 2C. 선택 — 접근성 QA

**수정 위치**: 내 `members/member-번호.html`, 필요하면 `styles.css`

- `<title>`과 `<h1>`이 페이지 목적을 설명하는가?
- Tab 키만으로 모든 링크에 이동할 수 있는가?
- 현재 초점이 화면에서 보이는가?
- “여기” 대신 목적지를 설명하는 링크 문구인가?
- 새 창 링크에 `rel="noreferrer"`가 있는가?

공통 `styles.css`를 수정하기 전 Issue에 영향 범위를 알리고 팀원의 승인을 받습니다.

## 2D. 선택 — 테스트 문서 작성

**작성 위치**: `docs/test-report-번호.md` (`docs/test-report-template.md` 복사)

~~~bash
mkdir -p docs
cp docs/test-report-template.md docs/test-report-번호.md
git add docs/test-report-번호.md
git commit -m "docs: 번호번 페이지 테스트 결과 기록"
~~~

`mkdir -p`는 폴더가 없어도 만들고, 이미 있어도 오류 없이 넘어갑니다. `cp 원본 복사본`은 파일을 복사합니다.

## 2E. 선택 — 작은 UI 개선

프로젝트 버튼, 키보드 포커스, 모바일 여백 중 하나를 개선합니다. 코드부터 고치지 말고 Issue에 아래를 먼저 작성합니다.

1. 현재 문제 또는 불편
2. 바꾸려는 파일과 예상 영향
3. 데스크톱·모바일 확인 방법

## 3. 팀 미션 — Review와 순차 Merge

다른 학생의 PR에서 범위, 링크, 모바일, 설명을 검토하고 구체적인 질문을 하나 남깁니다. Merge 뒤 다음 학생은 최신 `main`을 반영합니다.

~~~bash
git checkout main
git pull origin main
git checkout feature/member-번호
git merge main
git status
~~~

## 4. 팀 도전 — 의도적인 Conflict

두 학생이 서로 다른 Branch에서 `index.html`의 팀 슬로건 한 줄을 다르게 수정하고 첫 PR부터 Merge합니다. 두 번째 학생은 `main`을 Merge해 충돌을 확인합니다.

충돌 표시는 양쪽의 변경을 보여주는 경계선입니다. 팀이 최종 문장에 합의한 뒤 `<<<<<<<`, `=======`, `>>>>>>>` 표시를 모두 지우고 저장합니다.

~~~bash
git add index.html
git commit -m "fix: 팀 슬로건 충돌 해결"
git push
~~~

## AI 사용 규칙

AI에게 완성 코드를 요구하기 전에 `문제 위치 → 이유 → 확인 방법`을 요청합니다. 적용 후 반드시 `git diff`를 읽고 PR에 AI 사용 위치와 본인이 검증한 내용을 적습니다.

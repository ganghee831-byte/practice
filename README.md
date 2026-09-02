# Team Intro — Module 01 Starter

한 팀이 하나의 Repository를 공유하고, 각자 다른 Branch에서 개인·선택·팀 미션을 수행하는 GitHub 협업 실습입니다. 자세한 과제는 [TASKS.md](TASKS.md), 최종 점검은 [CHECKLIST.md](CHECKLIST.md)를 확인하세요.

## 시작 전: 용어 세 줄 복습

- **Repository**: 프로젝트 파일과 Git 변경 기록을 함께 보관하는 단위
- **Branch**: 안정적인 `main`과 분리해 작업하는 독립 작업선
- **Commit**: 의미 있는 변경을 이름 붙여 남긴 체크포인트

## 팀장: 공유 Repository 준비

1. 이 Starter로 `team-intro-팀번호` Repository를 만듭니다.
2. Settings → Collaborators에서 팀원을 초대합니다.
3. 팀원에게 **같은 HTTPS Repository URL**을 공유합니다.
4. `.github/ISSUE_TEMPLATE/member-page.md`를 사용해 팀원별 Issue를 만듭니다.
5. 모든 Pull Request를 한 번에 합치지 말고, 한 명씩 Review 후 Merge합니다.

## 팀원: Clone → Branch → 편집

~~~bash
mkdir -p ~/projects
cd ~/projects
git clone https://github.com/팀계정/team-intro-팀번호.git
cd team-intro-팀번호
git remote -v
git branch feature/member-번호
git checkout feature/member-번호
git branch
code .
~~~

명령을 실행한 뒤 `git status`로 현재 Branch와 변경 상태를 확인하세요. Core 미션에서는 자신에게 배정된 `members/member-번호.html`만 수정합니다.

## 담당 파일

| 학생 | 파일 | 브랜치 |
|---|---|---|
| 1번 | members/member-01.html | feature/member-01 |
| 2번 | members/member-02.html | feature/member-02 |
| 3번 | members/member-03.html | feature/member-03 |
| 4번 | members/member-04.html | feature/member-04 |
| 5번 | members/member-05.html | feature/member-05 |
| 6번 | members/member-06.html | feature/member-06 |

팀원이 적으면 사용하지 않는 페이지는 그대로 두거나 팀장이 마지막에 카드를 숨깁니다.

## 기본 Git 루프

~~~bash
git status
git diff
git add members/member-번호.html
git diff --staged
git commit -m "feat: 번호번 팀원 소개 페이지 완성"
git log --oneline --graph --all -8
git push -u origin feature/member-번호
~~~

`git add .` 대신 파일명을 직접 적으면 다른 학생의 파일이나 불필요한 변경이 Commit에 섞이는 것을 줄일 수 있습니다.

## Pull Request 이후

1. PR 템플릿에 변경 이유, 파일 위치, 확인 방법, AI 사용 여부를 적습니다.
2. 다른 팀원의 PR에 근거 있는 질문 또는 Review를 하나 남깁니다.
3. 앞선 PR이 Merge되면 최신 `main`을 받아 내 Branch에 반영합니다.

~~~bash
git checkout main
git pull origin main
git checkout feature/member-번호
git merge main
~~~

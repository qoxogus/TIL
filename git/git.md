# Git 명령어 정리
📌 쓰여진 코드는 대부분 예시 입니다.
- 이 명령어를 이용하면 명령어 사용법을 볼 수 있다
```bash
git --help
```
## Git 시작하기
- 새 저장소를 만들고 시작하기
```bash
git init
```
- 원격 저장소(repository)를 가져와서 시작하기
```bash
git clone <원격 저장소 주소>
```
## remote
- 현재 프로젝트에 등록된 리모트 저장소를 확인할 수 있다.   
리모트 저장소가 여러개 있다면 등록된 전부를 보여준다.
```bash
git remote
```
- 주어 단축이름과 URL을 함께 볼 수 있다.
```bash
git remote -v
```
- 원격저장소(repository)에 연결하기
```bash
git remote add origin <원격저장소 url>
```
- 리모트 저장소가 저장됬는지 확인 할 수 있다.
```bash
git remote get-url origin url
```
- 새로운 리모트 저장소를 설정할 수 있다.
```bash
git remote set-url origin url
```
- 원격저장소를 잘못 연결했을 때
```bash
gir remote remove origin
```
## branch
- branch 목록보기
```bash
git branch
```
- branch 생성
```bash
git branch <branchname>
```
- branch 전환하기
```bash
git checkout <branchname>
```
- branch 삭제
```bash
git branch -D <branchname>
```
- github
```bash
git branch -M main
```
## 스테이징
- 스테이징(add) : 변경사항을 저장하는 것.
```bash
git add <파일명>
```
- 모든 파일 스테이징
```bash
git add .
```
## commit
- commit
```bash
- git commit -m "<커밋메세지>"
```
## push
- 로컬저장소에 있는 파일들을 깃허브 저장소에 올리는 것이다.
```bash
git push origin <branchname>

git push origin main
```
## pull
- origin에 master에 있는 파일들을 받아온다.  
pull을 통해서 리모트 저장소에 있는 파일들을 받아올 수 있다.  
다른 사람이 작업한 내용을 내 로컬에 반영해 주는 것이다.
```bash
git pull origin master
```
## fetch
- pull과 비슷하지만 merge작업을 포합하지 않은 것이다.
```bash
git fetch
```
## reflog
- 지금까지 실행한 명령들을 모두 볼 수 있다.
```bash
git reflog
```
## reset
- 스테이징 & commit을 잘못했을때 또는 취소할 때 (unstaging 상태로 돌아감)
```bash
git reset <취소할 파일명>
```
- `HEAD` : 현재 작업하고있는 브랜치를 가리키는 포인터이며, 가장 마지막 커밋을 가리킨다.  
- 현재 커밋에서 한번 되돌아가고싶다.
```bash
git reset HEAD~1
```     
- 커밋했던 기록이 아예 사라지기 때문에 실수커밋을 push하고 reset을 사용해야 한다. 
- `reset`을 사용하면 3가지의 상태로 되돌아갈 수 있다.  
`git reset HAED~1 --mixed` : unmodified(변형되지않은/변경되지않은) 로 돌아간다.   
`git reset HAED~1 --soft` : staged으로 돌아간다.  
`git reset HAED~1 --hard` : 커밋되지 않은 모든 변경사항을 제거한다.

`git reset --mixed` : 헤드없이 하는 것은 수정사항을 모두 삭제할 때  
`git reset <lognum>` : 커밋의 고유한 로그번호를 이용해서 원하는 커밋으로 되돌릴 수 있다.

## revert
- reset과는 다르게 실수내용을 새로운 커밋으로 남긴다.
```bash
git revert
```
- `revert` 와 `reset` 언제 사용해야할까?
    - `reset`은 로컬에서 실수했을 때 
    - `revert`는 실수한 내용을 원격저장소에 올리고 다시 되돌리고 싶을 때

## [Github으로 협업하기](./githubcollaboration.md)

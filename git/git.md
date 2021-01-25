# Git 명령어 정리
## Git 시작하기
- 새 저장소를 만들고 시작하기
```bash
git init
```
- 원격 저장소(repository)를 가져와서 시작하기
```bash
git clone <원격 저장소 주소>
```
## 연결하기
- 원격저장소(repository)에 연결하기
```bash
git remote add origin <원격저장소 url>
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
- 스테이징을 잘못했을 때 또는 취소할 때 (unstaging 상태로 돌아감)
```bash
git reset <취소할 파일명>
```
## commit
- commit
```bash
- git commit -m "<커밋메세지>"
```
- commit을 잘못했을 때 또는 취소할 때 (unstaging 상태로 돌아감)
```bash
git reset <취소할 파일명>
```
## push
- push
```bash
git push origin <branchname>

git push origin main
```

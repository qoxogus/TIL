# Github으로 협업하기

> Github에 생성한 레포를 프로젝트의 원격으로 추가
```
git remote add (원격명) (Github 레포 주소)

//ex) git remote add origin https://github.com/{github-id}/{repository-name}.git
```
<hr>  

> 원격 레포 확인
```
git remote
```
<hr>

> github에 commit 내역 업로드
```
git push -u (원격명) (원격 브랜치명)

//ex) git push -u origin master
```
- 이후에는 `git push` 만 입력해도 됨
- github에 해당 이름의 브랜치가 없을 때는 새로 생성됨
<hr>

> github에 있는 프로젝트를 새로 내려받기
```
git clone (원격명)      

//ex) git clone https://github.com/{github-id}/{repository-name}.git
```
<hr>

> 원격 브랜치의 커밋 상태(새 업데이트 내역) 확인
```
git fetch
```
<hr>

> github에서 새로 업데이트 된 내역을 받아와 적용
```
git pull (원격명) (원격 브랜치명)

//ex) git pull origin master
```
- 이후에는 `git pull` 만 입력해도 됨
- 코드를 작성하기 전 업데이트 사항이 있던 없던 항상 입력하고 코드를 작성해보자. (좋은 습관)
<hr>

> github의 원격 브랜치까지 확인하기
```
git branch -a
```
<hr>

> 새 브랜치를 만들어 원격의 특정 브랜치로부터 내용 받기
```
git checkout -b (새 브랜치명) (원격명)/(원격의 브랜치명)

//ex) git checkout -b my-idea origin/my-idea
```
<hr>

> 원격의 브랜치 지우기
```
git push -d (원격명) (브랜치명)

//ex) git push -d origin my-idea
```
<hr>

## 🔑 merge
> 다른 브랜치의 변경사항 가져오기 (병합)
```
git merge (대상 브랜치명)
```
- 변경사항을 가져올 브랜치에서 입력하기❗️
<hr>
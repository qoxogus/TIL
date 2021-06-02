# Git Flow
* 브랜치 종류
	* feature
	* develop
	* release
	* hotfixs
	* master
	
## feature/{function}
> Feature 브랜치는 새로운 기능을 추가하기 위해 사용되는 브랜치이다.
> origin에는 업로드하지 않고, 개발자의 local에서만 존재한다
> feature 브랜치는 특정 기능 개발이 필요할 때 develop 브랜치로부터 파생되며 기능 개발이 완료되면 다시 develop 브랜치로 병합한다.
> 
> 기능개발이 완료되었다고 무작정 develop브랜치로 merge하면 안된다
> 추후 배포단계를 거치면서 release브랜치가 나뉘는데 이때 아직 배포하면 안될 기능이 있을 수 도 있다
> 이 경우 develop브랜치에 merge하지 않고, feature브랜치에 대기한다.

## develop
> 이 브랜치로부터 feature브랜치를 파서 작업
> feature브랜치에서 기능개발을 완료하면 merge하는 브랜치이다

## release
> 배포를 앞둔단계에서 QA를 진행하는 브랜치
> QA팀이 구현한 코드의 기능이 정상적인지 테스트하고 
> 이슈가 일어났을 시 보고

## master 
> 실제로 운영, 배포가되어 사용자가 사용(하게 될)하는 코드가 있는 브랜치 

## hotfixs
> 긴급수정 브랜치
> master브랜치 코드 즉 이미 운영되고 있는 서비스에서 긴급한 이슈가 발견되면 급하게 고치는 것

## Git Flow를 활용한 협업 방법
1. 저장소를 clone
2. 브랜치 생성
3. 로컬에서 작업
4. 커밋, 푸시(생성한 브랜치로) 
5. PR
6. Code Review
7. merge(develop branch) -> merge(master branch)

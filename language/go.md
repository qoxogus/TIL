# Go
### Go
- Go는 2009년 구글에서 일하는 로버트 그리즈머, 롭 파이크, 켄 톰프슨이 개발한 프로그래밍 언어이다. 가비지 컬렉션 기능이 있고, 병행성을 잘 지원하는 컴파일 언어다. 구문이 C와 비슷하지만 메모리 보안, 쓰레기 수집, 구조 타이핑, CSP 스타일 병행성을 제공한다.
### Go의 역사
2007년 3명의 구글의 개발자들이 C++의 복잡성이 싫어 개발을 시작

- 켄 톰프슨 : 유닉스 , B언어, C언어, UTF8 개발
- 롭 파이크 : 인페르노, UTF8 개발
- 로버트 그리즈머 : 크롬 자바스크립트 엔진 개발
### Go언어의 특징
1. 컴파일 속도가 매우 빠른 컴파일 언어
    - 컴파일 언어이지만 컴파일러가 소스 코드를 해석하는 pass 수를 줄여서 인터프리터 언어처럼 빠르게 동작
2. 언어의 문법이 간결하여 높은 성능과 생산성을 낼 수 있다
    - Go는 기본 라이브러리가 풍부하며, 써드파티 라이브러리가 많고, 코드가 간결하고, 키워드는 약 25개 정도로 적음
3. 객체지향 언어들과 표현 방식이 매우 다르다
    - 문법 자체는 익히기 쉽지만 Go로 제대로된 객체지향 프로그래밍을 하기 위해선 많은 숙련이 필요하다
4. 고루틴이라는 비동기 매커니즘을 제공하여 이벤트 처리 및 병렬 프로그래밍 작성이 쉽다
    - 고루틴은 OS에서 관리하는 경량 스레드보다 더 가볍기 때문에 CPU 코어갯수와 무관하게 수백, 수천만 고루틴을 작성해도 성능에 문제가 발생하지 않는다.
### Go를 사용한 객체지향 프로그래밍
- 제정민's Github Blog Link : [Go를 사용한 객체지향 프로그래밍][github blod link]

[github blod link]: https://jjmin321.github.io/development/GO를-사용한-객체지향-프로그래밍/ "Go github blog"
### Go의 키워드 25가지
```
break, default, func, interface, select, case, defer, go, map, struct, chan, else, goto, package, switch, const, fallthrough, if, range, type, continue, for, import, return, var
```
### Go의 터미널 명령어
- go build : 소스 파일 자체의 정보만을 사용하여 Go 바이너리를 빌드한다. 별도의 makefile은 없다.
- go test : 유닛 테스트 및 마이크로벤치마크
- go fmt : 코드 서식 지정
- go get : 원격 패키지의 검색 및 설치
- go vet : 코드 내의 잠재적인 오류를 찾아내는 정적 분석기
- go run : 코드를 빌드하고 실행하는 바로 가기
- godoc : HTTP를 통해 문서 확인
- gorename : 변수, 함수 등을 type-safe 방식으로 이름 변경
- go generate : 코드 생성기를 호출하는 표준 방식
### Go를 이용한 서비스
- Google
- Netflix
- Twitch
- Twitter
- Dropbox
- Uber
- Docker
- MongoDB
- Paypal

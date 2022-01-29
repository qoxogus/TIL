# Tech-Interview
## 객체지향이란 무엇인가요 ?
객체지향은 컴퓨터 프로그래밍 패러다임 중 하나로,  
프로그래밍에서 **필요한 데이터를 추상화시켜 상태와 행위를 가진 객체를 만들고  
그 객체들 간의 유기적인 상호작용을 통해 로직을 구성하는 프로그래밍** 방법입니다.

## SOLID 원칙에 대해 설명해주세요
SRP, OCP, LSP, ISP, DIP가 있으며  
시간이 니자도 **유지보수와 확장이 쉬운 시스템을 만들고자 할 때** 이 원칙들을 적용할 수 있습니다.

## Spring과 Spring Boot의 차이 ?
Spring Boot는 **내부에 Tomcat이 포함되어있어 따로 설치하거나 버전관리를 해주지 않아도 됩니다.**  
또한 **starter를 이용하여 개발 시작단계에 필요한 의존성들을 쉽게 관리**할 수 있습니다. (환경설정을 편하게 해준다.)

## 프레임워크와 라이브러리의 차이가 무엇인가요 ?
먼저 **프레임워크는 정해진 틀에서 프로그래밍을 하는 방식**이며,  
**라이브러리는 먼저 만들어진 코드를 가져다 쓰는 방식**입니다.

## JPA가 무엇인가요 ?
현재 **자바진영의 ORM 기술 표준으로 인터페이스의 모음**입니다.

## JPA의 장점은 무엇인가요 ?
**관계형 데이터베이스와 객체의 패러다임 불일치 문제를 해결할 수 있다는 점과  영속성 컨텍스트 제공이 큰 특징**입니다.

## 영속성 컨텍스트가 무엇인가요 ?
영속성 컨텍스트란 **엔티티를 영구 저장하는 환경이라는 뜻**이며,  
**크게 1차캐시와 쿼리문저장소로 나뉘어집니다.**

### 영속성 컨텍스트의 이점에는 뭐가 있나요 ?
* 1차캐시
* 더티체킹
* 동일성보장
* 쓰기 지연
* 지연로딩

## Hibernate는 무엇인가요 ?
**JPA의 구현체 중에 하나로 JPA의 대부분이 Hibernate로  
구현되었으며 내부적으로 JDBC API를 사용**합니다.

## 즉시로딩과 지연로딩이 무엇인가요 ?
**즉시로딩은 연관된 객체를 한번에 가져오며 쿼리가 날아가는 방식**이고,  
**지연로딩은 연관된 객체를 proxy로 가져와 직접 접근할 때 쿼리가 날아가는 방식**입니다.  
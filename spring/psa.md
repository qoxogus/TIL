# PSA란 ? (Portable Service Abstraction)
그대로 번역해보면 **호환성있는 서비스 추상화**이다.  
조금 더 이해하기 쉽게 설명하면 **잘 만든 인터페이스**이다.  

여기서 인터페이스에 대해 조금 짚고 가보자면
> 인터페이스란 ?  
머릿속으로는 아는데 설명하긴 어려운 단어인거같습니다.  
인터페이스는 **메서드는 작성할 수 있지만 로직은 구현할 수 없죠**  
인터페이스로 **N개의 클래스를 그룹화할 수 있고 인터페이스에서 implements한 클래스는 반드시 인터페이스에서 구현된 메서드를 Override하여 로직을 작성**해야합니다.

우리는 이렇게 잘 만들어진 인터페이스 덕분에 우리의 소스를 변경하지 않고 내부적으로 동작하는 로직을 변경할 수 있습니다.

대표적으로 `build.gradle`에서  
`spring-boot-starter-web` 을 주입하면 tomcat으로 실행되고  
`spring-boot-starter-webflux` 를 주입하면 Netty로 실행됩니다.  
위와 같이 간단하게 의존성만 변경하여 사용할 수 있습니다.  

또한 내부 기술 스택이 바뀌어도 어노테이션 매핑이 달라지지 않습니다.  
> Transaction(JPA, JDBC etc..),  
> Cache(Ehcache, Redis etc...) 등등  
> 각각 사용하는 내부 라이브러리는 달라져도 사용하는 어노테이션은 같죠.

우리가 Low Level의 코드를 직접 제어하지 않고 손쉽게 변경할 수 있죠.  
실제 데이터베이스에 connection하고, 트랜잭션 관리하는 작업은 Spring한테 맡기고 개발자는 로직에만 집중할 수 있습니다.  

이게 바로 **PSA**입니다.

### 결론
Spring은 특정 기술에 직접적 영향을 받지 않게끔 객체를 POJO 기반으로 한번씩 더 추상화한 Layer를 갖고 있으며,  
이를통해 일관성있는 Service Abstraction(서비스 추상화)를 만들어 냅니다.
> 코드는 더 견고해지고 기술이 바뀌어도 유연하게 대처할 수 있게 됩니다.

# Elastic Beanstalk 환경에서 Spring Boot Profile 적용해서 서버 돌리는 방법

**구성**에 들어가면 **카테고리**에 **소프트웨어**가 보일 것이다.

편집을 눌러서

![](../../img/eb-profile.png)

이와같이 추가해주면 된다.
> 아 물론 SpringBoot 내에서 프로필에 따라 설정을 해놔야한다.  
필자는 운영프로필 설정엔 RDS를 연결하고  
Swagger, h2-console을 막았다.

필자는 `prod`라는 별칭을 운영프로필 별칭으로 사용했고  
`dev`라는 별칭을 개발할 때 사용할 프로필 별칭으로 사용했다.
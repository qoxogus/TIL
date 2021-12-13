# Elastic Beanstalk란?

Elastic Beanstalk란 개발자인 사용자가 개발에만 집중할 수 있도록 인프라 구축을 알아서 해주는 서비스 이다.

보통 웹서비스를 배포하는 과정은
1. EC2 생성
2. 미들웨어 설치 및 설정
3. Database 설치 및 설정 그리고 구축
4. 신뢰성을 위한 서버 확장 및 부하분산을 위한 로드밸런싱

이정도로 진행이 되는데 Elastic Beanstalk는 배포 할 어플리케이션만을 구축하면 이러한 모든 과정(위의 과정들과 용량 프로비저닝 등)을 알아서 진행해주는 정말 편리한 서비스이다.  
> 실제로 사용 해 보고 이 글을 적고있지만 정말 편리했다.

Elastic Beanstalk은 Go, Java, .NET, Node.js, PHP, Python 및 Ruby에서 개발된 애플리케이션을 지원합니다.
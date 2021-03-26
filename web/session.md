# Session

### Session이란?
- 세션은 쿠키를 기반하고 있지만, 사용자 정보 파일을 브라우저에 저장하는 쿠키와 달리 세션은 서버 측에서 관리합니다.

- 서버에서는 클라이언트를 구분하기 위해 세션ID를 부여하며 웹 브라우저가 서버에 접속해서 브라우저를 종료할 때까지 인증상태를 유지합니다.

- 물론 접속시간에 제한을 두어 일정시간 응답이 없다면 정보가 유지되지 않게 설정이 가능합니다.

- 사용자에 대한 정보를 서버에 두기 때문에 쿠키보다 보안에 좋지만, 사용자가 많아질수록 서버 메모리를 많이 차지하게됩니다.

- 즉 동접자 수가 많은 웹 사이트인 경우 서버에 과부하를 주게 되므로 성능 저하의 요인이 됩니다.

- 클라이언트가 Request를 보내면, 해당 서버의 엔진이 클라이언트에게 유일한 ID를 부여하는 데 이것이 세션ID입니다.

### 세션의 동작 방식
1. 클라이언트가 서버에 접속 시 세션ID를 발급받습니다.

2. 클라이언트는 세션 ID에 대해 쿠키를 사용해서 자장하고 가지고 있습니다.

3. 클라이언트는 서버에 요청할 때, 이 쿠키의 세션ID를 서버에 전달해서 사용합니다.

4. 서버는 세션ID를 전달 받아서 별다른 작없없이 세션ID로 세션에 있는 클라이언트 정보를 가져옵니다.

5. 클라이언트 정보를 가지고 서버 요청을 처리하여 클라이언트에게 응답합니다.

### 세션의 특징
- 각 클라이언트에게 고유ID를 부여

- 세션ID로 클라이언트를 구분해서 클라이언트의 요구에 맞는 서비스를 제공

- 보안 면에서 쿠키보다 우수

- 사용자가 많아질수록 서버 메모리를 많이 차지하게 됨

### 세션의 사용 예
- 로그인 같이 보안상 중요한 작업을 수행할 때 사용

<hr>

# [쿠키와 세션의 차이](./cookiesessiondifference.md)
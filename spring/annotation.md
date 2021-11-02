# SpringBoot에서 사용하는 Annotation정리

### 모르거나 헷갈리는 SpringBoot에서 사용하는 어노테이션을 정리해보자!

### 

# Java

### @Override
- 부모 클래스로부터 상속받은 메소드를 자식 클래스에서 재정의

### @Overloading
- 자바의 한 클래스 내에 이미 사용하려는 이름과 같은 이름을 가진 메소드가 있더라도 매개변수의 개수 또는 타입이 다르면, 같은 이름을 사용해서 메소드를 정의할 수 있다.

# Spring Framework

### @Configuration
- 설정파일, Bean으로 등록, 싱글톤이 되도록 보장해준다

# Lombok

### @NoArgsConstructor 
- 파라미터가 없는 생성자를 생성한다.

### @AllArgsConstructor
- 클래스에 존재하는 모든 필드에 대한 생성자를 자동으로 생성한다.

# Jackson

### @JsonProperty
- 객체의 JSON변환 시 key의 이름을 개발자가 원하는대로 설정하게 해준다.(jackson 라이브러리를 다운받아야 함)  
`@JsonProperty` 선언 후 ObjectMapper의 `writeValueAsString()` 메소드를 이용하여 JSON으로 변환하여 출력하게 되면 다음과 같이 key 이름이 변경되는 것을 확인할 수 있다.(`??.setName(??); 등으로 넣은 키의 이름을 원하는대로 설정 후 sout을 찍으면 json형식으로 잘 찍히는걸 확인 할 수 있다.`  
```java
ex)
user.setId("qoxogus");
user.setPassword("1234");
System.out.println(new ObjectMapper.writeValueAsString(user));
```
`{"user_id" : "qoxogus", "user_password":"1234"}`
# Jackson 라이브러리 알아보기

### Jackson이란 ?
jackson은 자바진영 json 라이브러리로 잘 알려져 있지만 json뿐만 아니라 XML,YAML, CSV 등 다양한 형식의 데이터를 지원하는 data-processing 툴이다.  
스트림 방식이므로 속도가 빠르며 유연하며 다양한 third party 데이터 타입을 지원하며 annotation 방식으로 메타 데이터를 기술할 수 있으므로 json의 약점중 하나인 문서화 데이터 validation 문제를 해결할 수 있다.

### Jackson은 어떻게 동작하나요 ?
`Spring 3.0` 이후로 컨트롤러 리턴 방식이 `@RequestBody`형식이라면, Spring은 `MessageConverter` API를 통해, 컨트롤러가 리턴하는 객체를 후킹할 수 있다.  
`Jackson`은 `json`데이터를 출력하기 위한 `MappginJacksonHttpMessageConverter`를 제공합니다.  
만약 우리가 스프링 `MessageConverter`를 위의 `MappingJacksonHttpMessageConverter`로 등록한다면, 컨트롤러가 리턴하는 객체를 다시 뜯어(**자바 리플렉션 사용**) `Jackson`의 `ObjectMapper` API로 `json`객체를 만들고 난 후 , 출력하여 `json`데이터를 완성한다.  
더욱 편리해진 점은 `Spring 3.1` 이후로 만약 클래스패스에 `Jackson` 라이브러리가 존재한다면, (**`Jackson`을 설치했는지 안했는지에 따라**) 자동적으로 `MessageConverter`가 등록된다는 점이다.  
덕분에 우리는 아래와 같이 매우 편리하게 사용할 수 있다.  
```java
@RequestMapping("/json")
@ResponseBody()
public Object printJSON() {
    Person person = new Person("Mommoo", "Developer");
    return person;
}
``` 
그냥 데이터 인스턴스만 리턴하더라도 `json`데이터가 출력된다.  

### Jackson 주요 Annotation
* `@JsonIgnoreProperties` : json으로 변환(직렬화, 역직렬화)시 제외시킬 속성을 지정. VO class 위에서 선언
* `@JsonIgnore` : VO의 멤버변수 위에 선언해서 제외처리 (비밀번호같은거)
* `@JsonProperty` : json으로 변환 시에 사용할 이름이다. (DB컬럼과 이름이 다르거나 api응답과 이름이 다르지만 매핑시켜야할 때)
* `@JsonInclude` : 값 존재 유무에 따라 직렬화 시 동작을 지정 (default는 ALWAYS)
    * `ALWAYS` : 속성의 값에 의존하지 말고 항상 포함
    * `NOT_EMPTY` : NULL 또는 값이 빈 경우가 아니면 포함
    * `NOT_NULL` : NULL이 아니면 포함
    * `NOT_DEFAULT` : bean의 기본생성자로 정의된 필드값과 다르게 변경된 필드만 포함
* `@JsonAnyGetter` : Map 타입의 멤버변수의 getter 위에 선언한다. json 변환시 "key":"value" 형식으로 나온다.
* `@JsonAnySetter` : 역직렬화 때
* `@JsonGetter` : 어떤 필드값을 가져올 때 이 메소드로 접근해서만 가져오라고 jackson에게 명시적으로 알린다.
* `@JsonSetter` : 위와 동일, 역직렬화 때
* `@JsonAutoDetect` : 매핑 법칙을 바꿀 수 있다.
* `@JsonUnwrapped` : 어떤 필드에 대해 중첩 구조로 넣는다면, 그러지 말라고 명시적으로 알린다.
* `@JsonRootName` : VO class 위에 선언해서 wrapping 해서 json 변환
* `@JsonFormat` : 날짜, 시간값을 직렬화할 때 형식을 지정
    > ex) `JsonFormat(shape = JsonFormat.Shape.STRING, pattern = "dd-MM-yyyy hh:mm:ss)`
# Container


## container란
주입을 이용하여 객체를 관리하는 컨테이너이다.   
컨테이너의 사전적 의미는 무언가를 담는 용기, 즉 그릇을 의미한다.   
이를 통해 접급하자면 컨테이너는 객체관리를 주로 수행하는 그릇정도로 이해할 수 있다.   
빈의 생성과 관계, 사용, 생명 주기등을 관장한다.   
컨테이너를 통해 시스템 전반에서 언제는 사용가능하다.

> Container 는 개발자를 대신하여, Bean 을 생성 / 관리 / 제거합니다.  
> Container 가 Bean 을 관리해주기 때문에, 개발자는 모듈 간에 의존 및 결합으로 인해 발생하는 문제로부터 자유로워 졌습니다.   
> 아래와 같이 독립적인 코드를 작성해서 Annotaion 만 남겨주면 Container 가 개발자가 원하는 상황에 코드를 실행합니다.   
> 따라서 개발자는 메서드가 언제, 어디서 호출되어야 하는지 그리고 메서드를 호출하기 위해 필요한 매개 변수를 준비해서 전달하지 않습니다.   
>Container 가 개발자 대신 알아서 호출합니다.

```java
@GetMapping("/greeting") public Greeting greeting(@RequestParam(value = "name", defaultValue = "World") String name) { return new Greeting(counter.incrementAndGet(), String.format(template, name)); }
```

개발자가 Container 개념 즉, Spring framework 의 설계를 이해해야 하는 이유는 Container 가 겉으로 드러나지 않기 때문에 처음 Spring 을 접하면 작동 원리를 이해할 수 없습니다. 왜냐하면 일반적으로 모듈 간에 상호작용은 메서드로 이루어져야 하는데 코드를 보면 이러한 작업을 수행하는 코드가 없기 때문입니다.
```java
    public static void main(String[] args) { 
        SpringApplication.run(ConsumingRestApplication.class, args); // 개발자가 run 메서드를 호출하지 않지만, Container 에 의해 run 메서드가 수행됩니다. 
    } 
    @Bean 
    public RestTemplate restTemplate(RestTemplateBuilder builder) { 
        return builder.build(); 
    } 

    @Bean 
    public CommandLineRunner run(RestTemplate restTemplate) throws Exception { 
        return args -> { 
            Quote quote = restTemplate.getForObject( 
                "https://gturnquist-quoters.cfapps.io/api/random", Quote.class); 
            log.info(quote.toString()); 
        }; 
    } 
}
```

이렇게 Container 가 개발자를 대신하여 메서드가 호출될 때와 메서드가 필요한 자원을 전달하는 설계 구조를 [Inversion of Control (IOC)](./ioc.md) 이라 합니다.   
IOC 는 메서드가 필요로 하는 자원을 코드가 실행되는 타임에 전달하는데, 이를 [Dependency Injection (DI)](./di.md) 이라 합니다.  
예를 들어 Container가 알아서 greeting 메서드가 필요로 하는 name 매개변수를 전달하는 과정과 run 메서드가 필요로 하는 RestTemplate 매개변수를 전달하는 과정 모두 [Dependency Injection (DI)](./di.md) 입니다.

## 왜? 쓰는걸까
사실, 프로그래밍에서 그릇, 또는 용기로 이해될 수 있는 비슷한 요소들이 많이 있다.   
그렇다면 왜 Spring에서는 굳이 스프링 컨테이너 기능을 제공하는 것일까?  
우리는 객체를 사용하기 위해서 new 생성자를 이용하거나 `getter/setter` 기능을 써야만 했다.   
한 어플리케이션에는 이러한 객체가 무수히 많이 존재하고 서로 참조하고 있을 것이다.   
그 정도가 심할 수록 의존성이 높다고 표현한다. 낮은 결합도와 높은 캡슐화로 대변되는 객체지향프로그래밍에서 높은 의존성은 아니꼬울 수 밖에 없다.   
의존성 제어, 즉 객체 간의 의존성을 낮추기 위해 바로 Spring 컨테이너가 사용된다.
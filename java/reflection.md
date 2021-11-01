# Reflection
리플렉션이란 객체를 통해 클래스의 정보를 분석해 내는 프로그램 기법을 말한다  
> 투영, 반사 라는 사전적인 의미를 지니고 있다.

리플렉션은 **구체적인 클래스 타입을 알지 못해도, 그 클래스의 메소드, 타입, 변수들을 접근할 수 있도록 해주는 자바 API** 이다.

### 구체적인 클래스 타입을 알지 못하면 메소드를 실행할 수 없나 ?
> Yes

```java
public class Car {
    
    public void drive() {
        //doSomeThing
    }
    
    public class Main{
        public static void main(String[] args) {
            Object car = new Car();
            car.drive(); // 컴파일 에러
        }
    }
}
```

위의 코드에서 컴파일 에러가 나는 이유는 모든 클래스의 조상 클래스인 `Object`라는 타입으로  
`Car` 클래스의 인스턴스를 담을 수는 있지만  
**사용 가능한 메소드는 Object의 메소드와 변수들 뿐이기 때문**이다.

그러므로 car의 메소드는 사용하지 못하는 것이다.  

이런식으로 구체적인 타입의 클래스를 모를 대 사용하는게, 리플렉션이라고 합니다.  

그런데 여기서 의문이 생깁니다.  

"내가 만드는 프로그램의 코드 흐름인데, 내가 사용할 클래스의 이름과 타입을 모르는 경우가 있나 ?"

일반적인 경우로는 만나기 힘든 경우입니다.  

하지만 코드를 작성할 시점에는 어떤 타입의 클래스를 사용할지 모르는 경우가 있습니다.  
이럴 때에는 실행할 시점, 그러니까 런타임에 지금 실행되고 있는 클래스를 가져와서 실행을 해야되는 것입니다.  

대표적으로 프레임워크나 IDE에서 이러한 동적 바인딩을 이용한 기능을 제공하는데 IntelliJ의 자동완성, 스프링 프레임워크의 어노테이션과 같은 기능이 바로 설계할 때는 사용 될 클래스가 어떤 타입인지 모르지만 리플렉션을 이용해서 일단 코드를 작성하고 실행 시점에 확인해서 활용할 수 있도록 하는 매커니즘입니다.

### 어떻게 이게 가능해 ?
자바 클래스 파일은 바이트코드로 컴파일되어 Static 영역에 위치하게 됩니다.
(`.java` -> `.class` -> `실행` 이라는 2단계 매커니즘)  
때문에 클래스 이름만 알고있다면, 언제든지 이 영역을 뒤져서 클래스에 대한 정보를 가져올 수 있는 것입니다.  

아래는 가져올 수 있는 클래스의 정보들입니다.
```
ClassName
Class Modifiers (publicm private, synchronized 등)
Package Info
Superclass
Implemented Interfaces
Constructors
MethodsFiedls
Annotations
```

아래 레퍼런스는 리플렉션에 대한 사용 방법에 대한 레퍼런스입니다.  
* [[Java Reflection 개념 및 사용법]](https://gyrfalcon.tistory.com/entry/Java-Reflection)  
* [[Trail: The Reflection API (The Java Tutorials)]](https://docs.oracle.com/javase/tutorial/reflect/)
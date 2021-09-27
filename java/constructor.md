# 생성자란?
객체 지향 프로그래밍에서 객체의 초기화를 담당하는 서브루틴을 가리킨다.  
생성자는 객체가 처음 생성될 때 호출되어 멤버변수를 초기화하고, 필요에 따라 자원을 할당하기도 한다.  
객체의 생성시에 호출되기 때문에 생성자라는 이름이 붙었다.

> 생성자는 대체로 멤버함수와 같은 모양을 하고있지만 값을 반환하지 않는다는 점에서 엄밀한 의미의 함수는 아니다.

### 생성자의 규칙
* 클래스명과 메소드명이 동일해야한다.
* 리턴 타입을 정의하지 않는다.

**생성자는 객체가 생성될 때 호출**되며,  
객체가 생성될 때는 `new`라는 키워드로 객체가 만들어질 때이다.

즉 생성자는 다음과 같이 `new`라는 키워드가 사용될 때 호출된다.
```java
new 클래스명(입력항목)
```

생성자는 메소드와 마찬가지로 입력을 받을 수 있다.  

아래처럼 만든 생성자는 입력값으로 문자열을 필요로 하는 생성자이다.
```java
public HouseDog(String name) {
    this.setName(name);
}
```

따라서 다음과 같이 `new`키워드로 **객체를 만들 때 문자열을 전달**해야만 한다.
```java
HouseDog dog = new HouseDog("happy"); //생성자 호출 시 문자열을 전달해야한다.
```

만약 다음처럼 코딩하면 컴파일 오류가 발생할 것이다.
```java
HouseDog dog = new HouseDog();
```

오류가 발생하는 이유는 객체 생성방법이 생성자의 규칙과 맞지 않기 때문이다.  
생성자가 선언된 경우 생성자의 규칙대로만 객체를 생성할 수 있다.

생성자가 적용된 HouseDog Class
```java
public class HouseDog extends Dog {
    public HouseDog(String name) {
        this.setName(name);
    } 

    public void sleep() {
        System.out.println(this.name+" zzz in house");
    } 

    public void sleep(int hour) {
        System.out.println(this.name+" zzz in house for " + hour + " hours");
    } 

    public static void main(String[] args) {
        HouseDog dog = new HouseDog("happy");
        System.out.println(dog.name);
    }
}
```

출력결과
```
happy
```

이렇듯 생성자를 사용했을 때 얻게되는 이득은 자원을 할당하는 행동 등을 객체 생성시에 제어할 수 있게된다는 점이다.

> [🙂참고한 자료입니다🙃](https://wikidocs.net/281)
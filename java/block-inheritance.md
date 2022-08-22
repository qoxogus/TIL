# 자바에서 상속을 막는 방법
1. 기본 생성자를 private로 만든다.
2. 클래스를 final로 만든다.

```java
public class Parent {
    private Parent() {
    }

    ...
}

public final class Parent {
    ...
}
```

> 상속하게되면 하위 클래스에서 부모클래스의 생성자를 호출하게 되어있다.   
> (그러므로 기본 생성자를 private로 만들면 서브 클래스 생성이 불가하다)
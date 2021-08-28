# Lambda
### 람다함수란 ?
람다 함수는 프로그래밍 언어에서 사용되는 개념으로 익명함수를 지칭하는 용어이다.  
현재 사용되고 있는 람다의 근간은 수학과 기초 컴퓨터 과학 분야에서의 람다 대수이다. 람다 대수는 간단히 말하자면 수학에서 사용하는 함수를 보다 **단순하게 표현하는 방법**이다.

### 람다의 특징
람다 대수는 이름을 가질 필요가 없다. - 익명함수  
두개 이상의 입력이 있는 함수는 최종적으로 1개의 입력만 받는 람다 대수로 단순화 될 수 있다 - 커링(Curring)

> 익명함수? : 익명함수란 말 그대로 함수의 이름이 없는 함수이다.  
익명 함수들은 공통으로 `일급객체`라는 특징을 가지고 있다.  
이 일급객체란 일반적으로 다른 객체들에 적용 가능한 연산을 모두 지원하는 개체를 가르킨다. 함수를 값으로 사용 할 수도 있으며 파라미터로 전달 및 변수에 대입하기와 같은 연산들이 가능하다.

### 람다의 장단점
* 장점
1. 코드의 간결성 - 람다를 사용하면 불필요한 반복문의 삭제가 가능하며 복잡한 식을 단순하게 표현할 수 있다.
2. 지연연산 수행 - 람다는 지연연산을 수행 함으로써 불필요한 연산을 최소화 할 수 있다.
3. 병렬처리 가능 - 멀티쓰레드를 활용하여 병렬처리를 사용할 수 있다.

* 단점
1. 람다식의 호출이 까다롭다. 
2. 람다 stream 사용 시 단순 for문 혹은 while문 사용 시 성능이 떨어진다.
3. 불필요하게 너무 사용하게되면 오히려 가독성을 떨어뜨릴 수 있다.
> 적절한 상황에 람다를 적당히 사용하길 바란다.

### 람다의 표현식
* 람다는 매개변수 화살표(->) 함수 몸체로 이용하여 사용할 수 있다.
* 함수 몸체가 단일 실행문이면 괄호{}를 생략할 수 있다.
* 함수 몸체가 return문으로만 구성되어있는 경우 괄호{}를 생략할 수 없다.
```
() -> {}

() -> 1

() -> { return 1; }
```

### 람다식 예제
* 기존 자바 문법
```java
new Thread(new Runnable() {
    public void run() {
        System.out.println("Hello taehyeon");
    }
 }).start();
```

* 람다식 문법
```java
new Thread(() -> {
    System.out.println("Hello taehyeon");
}).start();
```

### 함수형 인터페이스와 람다
`@FunctionalInterface` 는 일반적으로 구현해야 할 추상메소드가 하나만 정의된 인터페이스를 가리킵니다.  

자바 컴파일러는 이렇게 명시된 함수형 인터페이스에 두개 이상의 메소드가 선언되면 오류를 발생시킵니다.

```java
//구현해야 할 메소드가 한개이므로 Functional Interface이다.
@FunctionalInterface
public interface Math {
    public int Calc(int first, int second);
}

//구현해야 할 메소드가 두개이므로 Functional Interface가 아니다. (오류 사항)
@FunctionalInterface
public interface Math {
    public int Calc(int first, int second);
    public int Calc2(int first, int second);
}
```

* 함수형 인터레이스 람다 사용 예제
> 함수형 인터페이스 선언
```java
@FunctionalInterface
interface Math {
    public int Calc(int first, int second);
}
```

> 추상 메소드 구현 및 함수형 인터페이스 사용
```java
public static void main(String[] args){

   Math plusLambda = (first, second) -> first + second;
   System.out.println(plusLambda.Calc(4, 2));

   Math minusLambda = (first, second) -> first - second;
   System.out.println(minusLambda.Calc(4, 2));

}
```

> 실행결과
```
6
2
```
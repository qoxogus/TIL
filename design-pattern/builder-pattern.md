# Builder Pattern

* 객체를 생성할 때 흔히 사용하는 패턴이다.

Builder Pattern에 대해 이 두 책이 설명이 조금 다르다.
* GoF-Design-Pattern : 소프트웨어 디자인 패턴의 원조라 할 수 있는 책
    * GoF의 빌더 패턴
        * 객체의 생성 알고리즘과 조립 방법을 분리하는 것이 목적이다.
* 이펙티브 자바(Effective Java) : 조슈아 블로흐가 직접 쓴 자바 코딩 스타일 책.
    * GoF의 빌더 패턴보다 좀 더 코딩 위주의 활용법을 설명한다.
        * 코드 읽기/유지보수가 편해지므로 빌더 패턴을 쓰라고 한다.
    * GoF가 책을 썼을 때에는 상대적으로 덜 중요했던 객체 일관성, 변경 불가능성 등의 특징을 설명한다.

> 두 책의 관점이 다르고, 이펙티브자바(2001년)가 GoF의 디자인패턴(1994년)보다 나중에 나왔기때문인 것 같다.
---
## Effective Java의 빌더 패턴
> * 생성자 인자가 많을 때는 Builder 패턴 적용을 고려하라
> * 생성자에 매개변수가 많다면 빌더를 고려하라
: 이펙티브 자바에서 말하는 빌터패턴은 객체생성을 깔끔하고 유연하게 하기 위한 기법이다.

### 객체생성을 깔끔하게
### : 점층적 생성자 패턴
점층적 생성자 패턴을 만드는 방법
1. 필수 인자를 받는 필수 생성자를 하나 만든다.
2. 1개의 선택적 인자를 받는 생성자를 추가한다.
3. 2개의 선택적 인자를 받는 생성자를 추가한다.
4. ...반복
5. 모든 선택적 인자를 다 받는 생성자를 추가한다.
```java
// 점층적 생성자 패턴 코드의 예 : 회원가입 관련 코드
public class Member {

    private final String name;      // 필수 인자
    private final String location;  // 선택적 인자
    private final String hobby;     // 선택적 인자

    // 필수 생성자
    public Member(String name) {
        this(name, "출신지역 비공개", "취미 비공개");
    }

    // 1 개의 선택적 인자를 받는 생성자
    public Member(String name, String location) {
        this(name, location, "취미 비공개");
    }

    // 모든 선택적 인자를 다 받는 생성자
    public Member(String name, String location, String hobby) {
        this.name = name;
        this.location = location;
        this.hobby = hobby;
    }
}
```
: 장점  
* `new Member("홍길동", "출신지역 비공개", "취미 비공개")` 같은 호출이 빈번하게 일어난다면, `new Member("홍길동")`로 대체할 수 있다.    

: 단점  
* 다른 생성자를 호출하는 생성자가 많으므로, 인자가 추가되는 일이 발생하면 코드를 수정하기 어렵다.
* 코드 가독성이 떨어진다.
    * 특히 인자 수가 많을 때 호출 코드만 봐서는 의미를 알기 어렵다.
```java
// 호출 코드만으로는 각 인자의 의미를 알기 어렵다.
NutritionFacts cocaCola = new NutritionFacts(240, 8, 100, 3, 35, 27);
NutritionFacts pepsiCola = new NutritionFacts(220, 10, 110, 4, 30);
NutritionFacts mountainDew = new NutritionFacts(230, 10);
```
### 빌더 패턴 (Effective Java)
```java
// Effective Java의 Builder Pattern
public class NutritionFacts {
    private final int servingSize;
    private final int servings;
    private final int calories;
    private final int fat;
    private final int sodium;
    private final int carbohydrate;

    public static class Builder {
        // Required parameters(필수 인자)
        private final int servingSize;
        private final int servings;

        // Optional parameters - initialized to default values(선택적 인자는 기본값으로 초기화)
        private int calories      = 0;
        private int fat           = 0;
        private int carbohydrate  = 0;
        private int sodium        = 0;

        public Builder(int servingSize, int servings) {
            this.servingSize = servingSize;
            this.servings    = servings;
        }

        public Builder calories(int val) {
            calories = val;
            return this;    // 이렇게 하면 . 으로 체인을 이어갈 수 있다.
        }
        public Builder fat(int val) {
            fat = val;
            return this;
        }
        public Builder carbohydrate(int val) {
            carbohydrate = val;
            return this;
        }
        public Builder sodium(int val) {
            sodium = val;
            return this;
        }
        public NutritionFacts build() {
            return new NutritionFacts(this);
        }
    }

    private NutritionFacts(Builder builder) {
        servingSize  = builder.servingSize;
        servings     = builder.servings;
        calories     = builder.calories;
        fat          = builder.fat;
        sodium       = builder.sodium;
        carbohydrate = builder.carbohydrate;
    }
}
```
위와 같이 하면 다음과 같이 객체를 생성할 수 있다.
```java
NutritionFacts.Builder builder = new NutritionFacts.Builder(240, 8);
builder.calories(100);
builder.sodium(35);
builder.carbohydrate(27);
NutritionFacts cocaCola = builder.build();
```
또는
```java
// 각 줄마다 builder를 타이핑하지 않아도 되어 편리하다.
NutritionFacts cocaCola = new NutritionFacts
    .Builder(240, 8)    // 필수값 입력
    .calories(100)
    .sodium(35)
    .carbohydrate(27)
    .build();           // build() 가 객체를 생성해 돌려준다.
```
: 장점
* 각 인자가 어떤 의미인지 알기 쉽다.
* `setter`메소드가 없으므로 변경 불가능 객체를 만들 수 있다.
* 한번에 객체를 생성하므로 객체 일관성이 깨지지 않는다.
* `build()`함수가 잘못된 값이 입력되었는지 검증하게 할 수도 있다.

### Lombok @Builder
Lombok의 `@Builder`어노테이션으로 쉽게 사용할 수 있다.

다음과 같이 클래스 또는 생성자에 `@Builder`어노테이션을 붙여주면 이펙티브 자바 스타일과 비슷한 빌터 패턴 코드가 빌드된다.
```java
@Builder
public class NutritionFacts {
    private final int servingSize;
    private final int servings;
    private final int calories;
    private final int fat;
    private final int sodium;
    private final int carbohydrate;
}
```
사용은 다음과같이 한다
```java
NutritionFacts.NutritionFactsBuilder builder = NutritionFacts.builder();
builder.calories(230);
builder.fat(10);
NutritionFacts facts = builder.build();
```
물론 `.`체인도 된다!
```java
NutritionFacts facts = NutritionFacts.builder()
    .calories(230)
    .fat(10)
    .build();
```

### 객체 생성을 유연하게
빌더 패턴을 사용하면 하나의 빌더 객체로 여러 객체를 만드는 것도 가능하다
> 인자가 설정된 빌더는 훌륭한 추상적 팩토리다.

위의 인용구는 이펙티브 자바의 저자인 조슈아 블로흐가 GoF책의 빌더 패턴 부분을 인용한 것이다.

다음과 같은 인터페이스를 만들고, 빌더 클래스가 `implements`하게 하면 된다.
```java
public interface Builder<T> {
    public T build();
}
```

## GoF 디자인 패턴의 빌더 패턴
빌더 패턴의 의도는 다음과 같다
> 복잡한 객체를 생성하는 방법과 표현하는 방법을 정의하는 클래스를 별도로 분리하여 서로 다른 표현이라도 이를 생성할 수 있는 동일한 구축 공정을 제공할 수 있도록 한다.

* 참여 객체
    * Builder : 빌더 인터페이스
    * ConcreteBuilder : 빌더 인터페이스 구현체. 부품을 합성하는 방식에 따라 여러 구현체를 만든다.
    * Director : Builder를 사용해 객체를 생성한다,
    * Product : Director가 Builder로 만들어낸 결과물

즉 다음과 같은 조합이 가능하다
![](../img/builder-ex.png)

GoF책에서는 이해를 돕기 위해 미로 만드는 코드를 예제로 삼는다

* Builder 인터페이스
```java
/* Builder 인터페이스 */
class MazeBuilder {
    public :
        virtual void BuildMaze() { }
        virtual void BuildRoom(int room) { }
        virtual void BuildDoor(int roomFrom, int roomTo) { }
        virtual Maze* GetMaze() { return 0; }
    protected :
        MazeBuilder();
}
```
* Builder 구현체
    * Builder구현체는 방과 문, 미로를 만든다
    * 방과 문을 몇개를 만들고 어떤 순서로 조합하는지를 아는 것은 Director의 일이다
    * 다음과 같이 목적에 따라 여러가지로 만들 수 있다.
```java
/* 표준적인 방, 문, 미로를 만드는 Builder 구현체 */
class StandardMazeBuilder : public MazeBuilder {
    public :
        StandardMazeBuilder();
        virtual void BuildMaze();
        virtual void BuildRoom(int);
        virtual void BuildDoor(int, int);

        Virtual Maze* GetMaze();
    private :
        Direction CommonWall(Room*, Room*);
        Maze* _currentMaze;
};

/* 미로는 만들지 않고 방과 문의 숫자를 세는 Builder 구현체 */
class CountingMazeBuilder : public MazeBuilder {
    public :
        CountingMazeBuilder();
        virtual void BuildMaze();
        virtual void BuildRoom(int);
        virtual void BuildDoor(int, int);
        virtual void AddWall(int, Direction);
        void GetCount(int &, int &) const;
    private :
        int _doors;
        int _rooms;
}
```
* Director
    * Director는 Builder에게 방을 몇개 만들고, 문을 몇 개 만들 것을 지시하여 미롤를 완성한다.
    * Builder는 시키는대로 방과 문만 잘 만들면 된다.
```java
/* 기본 미로를 만드는 Director */
Maze* MazeGame::CreateMaze(MazeBuilder& builder) {
    builder.BuilderMaze();
    builder.BuildRoom(1);
    builder.BuildRoom(2);
    builder.BuildDoor(1, 2);

    return builder.GetMaze();
}

/* 복잡한 미로를 만드는 Director */
Maze* MazeGame::CreateComplexMaze(MazeBuilder& builder) {
    builder.BuildRoom(1);
    // ...
    builder.BuildRoom(1001);

    return builder.GetMaze();
}
```
* 사용법
```java
Maze * maze;                    /* product */
MazeGame game;                  /* director */
StandardMazeBuilder builder;    /* builder */
game.CreateMaze(builder);
maze = builder.GetMaze();
```

* 위의 것들을 토대로 케이크와 주스를 Build해보자
```java
// 케이크를 build 한다
Builder builder = new CakeBuilder("초콜릿", "딸기");
Director director = new Director(builder);
Product cake = director.build();

// 주스를 build 한다
Builder builder = new JuiceBuilder("당근").ice(true);
Director director = new Director(builder);
Product juice = director.build();
```
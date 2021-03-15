# Ioc (Inversion of Control : 제어의 역전)

프로그램 제어권을 Framework가 가져가는 것으로 DI를 통해 달성됨.

생성된 객체의 생명주기 '전체' 에 대한 권한과 관리를 프레임워크에 주어, 개발자는 비즈니스 로직에만 신경쓰면 됨.

개발자가 annotation, xml 등을 통해 설정을 해놓으면 Container가 알아서 처리함.

> 의존성 주입 방법

**Field Injection : 멤버 변수를 통한 전달**  
Bean으로 등록된 객체를 사용하고자 하는 클래스에 Field로 선언한 뒤 `@Autowired` 키워드를 붙여주면 자동으로 주입됨

```java
@Autowired
@Qualifier("myBoardDao") // Qualifier는 동일한 class의 bean이 여러개 존재할 경우 사용함
  private BoardDAO boardDao;
  ```

>    단점  
>
> 1. 단일 책임의 원칙 위반
>
>       의존성 주입이 쉬움
>
> 2. 의존성이 숨음
>
> 3. DI 컨테이너의 결합성과 테스트 용이성
>
>       필요한 의존성을 가진 클래스를 곧바로 인스턴스화 시킬 수 없음
>
> 4. 불변성 (Immutability)
>
>       final을 선언할 수 없기 때문에 객체가 변할 수 있음.
>
> 5. 순환 의존성
>
>       순환참조 발생 가능

**Method(Setter) Injection : setter() 를 통한 전달**  
외부에서 생성된 객체를 setter를 통해 사용하는 방법.

순환 참조, coupling (결합도) 등의 문제로 인해 constructor injection 권장함

```java
// java
@Service
public class BoardService{
  private BoardDAO boardDao;
  
  @Autowired
  public void setBoardDao(BoardDao boardDao){
    this.boardDao = boardDao;
  }
}
```

```XML
// XML
<property name="myName" value="poodle"></property>
```

**Constructor Injection : 생성자를 통한 전달**  
생성자에 `@Autowired` 어노테이션을 붙여 의존성을 주입하는 방법.

의존관계에 있는 객체들은 반드시 의존관계 주입이 되어야 하기 때문에 이 방법을 권장
```java
// java
//Spring 4.3 버젼 부터 @Autowired 생략가능
// @Autowired 
    public BoardService(BoardDao boardDao) {
        this.boardDao = boardDao;
}
```

```XML
//XML
<constructor-arg ref = "cat"></constructor-arg>
```

> 장점  
>
> 1. 결합도 제거  
>
>       - 종속성이 감소해 변경에 민감하지 않음.  
>
> 2. 재사용 코드  
>
>       - 일부 인터페이스의 다른 구현이 필요한 경우, 해당 구현을 사용해 components를 구성할 수 있음
> 3. 테스트 코드  
>
> - 더 많은 테스트 코드 생성 가능함.  
>
> - Mock 객체는 실제 구현의 테스트로 사용하는 객체로, 종속성을 components에 주입할 수 있을 > 경우, mock 구현 주입이 가능함.  
>
> 4. 가독성 코드  
>
> - components의 종속성을 보다 쉽게 파악 가능  


![ioc](../img/ioc.png)
**필요한 클래스를 직접 생성하는 것이 아니라 주입함으로써 객체 간의 결합도를 줄이고 유연한 코드 작성 가능함.**
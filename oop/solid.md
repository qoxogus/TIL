# SOLID (좋은 객체지향 설계의 5가지 원칙)

> SPR, OCP, LSP, ISP, DIP 를 하나로 부르는 말 이다

## S | SPR 단일 책임 원칙 (Single responsibillity principle)
: 생성된 클래스는 하나의 기능만 가지며, 클래스가 제공하는 모든 서비스는 그 하나의 책임을 수행하는데 집중되어 있어야 한다
- 한 클래스는 하나의 책임만을 가져야 한다
- 변화에 대한 유연성 확보
- 낮은 결합도, 높은 응집도 추구


## O | OCP 개발-폐쇄 원칙 (Open/closed principle)
: 소트트웨어의 구성요소(컴포넌트, 클래스, 모듈, 함수)는 확장에 열려있고, 변경에는 닫혀있어야 한다.  
- 상위 클래스 또는 인터페이스를 중간에 둠으로써, 자신의 변화에 대해서 폐쇄적이지만, 인터페이스는 외부의 변화에 대해서 확장을 개방해 줄 수 있다
- 이러한 부분은 JDBC, Hibernate등 JAVA Stream(I,O)에서 찾아볼 수 있다

## L | LSP 리스코프 치환 원칙 (Liskov substitution principle)
: 서브 타입은 언제나 기반타입으로 교체할 수 있어야 한다
- 프로그램의 객체는 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야 한다
- 즉 인터페이스만 알면 구현체를 몰라도 사용가능 해야한다
- 예) 자동차 인터페이스의 엑셀은 앞으로 가라는 기능이다. 뒤로 가게 구현한다면 LSP를 위반한 것! 느리더라도 앞으로 가야함
> (단순히 구현여부만 따지는 것이 아님, 기능적으로 올바르게 구현했느냐를 보는 것임)

## I | ISP 인터페이스 분리 원칙 (Interface segregation principle)
: 자신이 사용하지 않는 인터페이스는 구현하지 말아야한다
- 인터페이스를 다시 작게 나누어 만든다
- 두 개 이상의 인터페이스가 필요한 경우 다중 인터페이스 상속으로 구현하는 것이 좋다

## D | DIP 의존관계 역전 원칙 (Dependency inversion principle)
: 상위 모듈은 하위 모듈에 의존해선 안된다
- 구현클래스에 의존하지 않고 인터페이스에 의존
- 상위, 하위 모듈은 모두 추상화에 의존해야한다
- 세부사항이 추상화에 의존해야한다
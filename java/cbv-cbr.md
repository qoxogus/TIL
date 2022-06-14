# Call By Value, Call By Reference

### Call By Value (CBV)
기본 자료형과 같이 대상에 주소값을 가지지 않고 값을 할당받아 사용됩니다.  
예를 들어 `int p = 1`이라고 했을 때 메소드에 인자를 받을 때 p의 주소값을 받는 것이 아닌 p의 값 1을 직접 받는 것을 말합니다.
* 기본자료형  
정수형 : byte(1), short(2), int(4), long(8)  
실수형 : float(4), double(8)  
문자형 : char(2)  
논리형 : boolean(1)

### Call By Reference (CBR)
대상을 선언할 때 주소값이 부여되어 그 객체를 호출했을 때 그 객체의 주소값을 불러오기 때문에  
`==`으로는 주소값이 달라 비교 연산을 할 수 없지만 `equals`와 같이 해당 주소에 있는 값에 대한 비교연산은 가능합니다.  
* Class, Object

`==` : 주소 값을 비교  
`equals` : 해당 주소의 value를 비교  

**기본 자료형(Primitive type)은 stack영역에 실제 값을 저장**하기 때문에 `==`비교 연산을 할 수 있습니다.  
**참조 자료형(Reference type)은 stack영역에 메모리 주소만 저장하고, 실제 인스턴스는 heap영역에 저장**하기 때문에 `equals`로 비교 연산을 할 수 있습니다.
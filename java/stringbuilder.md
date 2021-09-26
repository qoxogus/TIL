# String 대신 StringBuilder를 사용해야하는 이유 (StringBuffer)
`String`에서 값을 이어붙일 때 `.concat(value)` 또는 `+ "value"`를 사용해 붙일 수 있다.  
**StringBuilder**와 **StringBuffer**는 `concat`또는 `+`를 사용하지 않으려고 사용하는 것이다.  

**`String`은 불변(immutable)하기 때문에 값을 변경할 수 없다.**
> 즉, `.concat()` 또는 `+`를 이용한 값 변경은 기존 String에 들어있던 값을 버리고 새로 값을 할당하는 것이다. (객체를 새로 할당한다)  
따라서 `concat`이나 `+`를 많이 사용할 경우 속도가 현저히 느려진다.

`String`에 `concat` 혹은 `+`를 1000번이상 하게되면 속도가 너무 느려져 비효율적이므로 그때는 **StringBuffer**나 **StringBuilder**를 사용하라는 것이다.

**StringBuilde**r와 **StringBuffer**는 변하기(mutable) 때문에 `.append()`, `.delete()`등을 통해서 값을 변경할 수 있다.

### StringBuilder와 StringBuffer 뭘 사용해야하는데 ?
**StringBuffer**는 공통 메소드가 동기화되므로 멀티쓰레드 환경에서는 **StringBuffer**를 사용하는것이 안전하다(값이 예상치 못하게 변경되는 것 방지)

그 외에는 **StringBuilder**가 성능이 뛰어나기에 **StringBuilder**를 사용해주면 된다.  
### StringBuilder, StringBuffer의 주요메소드
* `.append(value)` : StringBuilder, StringBuffer 뒤에 값을 붙인다.
* `.insert(index, value)` : 특정 인덱스부터 값을 삽입한다.
* `.delete(index, index)` : 특정 인덱스부터 인텍스까지 값을 삭제한다.
* `.indexOf(value)` : 값이 어느 인덱스에 들어있는지 확인한다.
* `.substring(index, index)` : 인덱트부터 인덱스까지 값을 잘라온다.
* `.length()` : 길이 확인
* `.replace(index, index, value)` : 인덱스부터 인덱스까지 값으로 변경
* `.reverse()` : 글자 순서를 뒤집는다.
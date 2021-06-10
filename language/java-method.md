# Java Method 정리

### 코딩테스트를 하며 또는 궁금한 메소드를 구글링하며 정리합니다.
: 자바 메소드 정리 사전 😎

### String 관련
* `String.toCharArray()` : 문자열을 한 글자씩 쪼개서 이를 char타입의 배열로 집어넣어주는 친절한 메소드이다.  
* `length()` : 문자열의 길이를 알고자 할 때 사용되는 메소드이다. (배열은 `array.length`처럼 괄호없이 쓴다)  
* `isEmpty()` : 빈 문자열인지 체크하는 메소드.
* `replace(char old, char new)` : old의 문자를 new로 변환
* `split(String str)` : str문자열을 기준으로 문자열 분리
* `toUpperCase()` : 모두 대문자로
* `toLowerCase()` : 모두 소문자로
* `trim()` : 문자열의 앞, 뒤 공백 제거 (한쪽만 제거는 불가능하다)
* `charAt(int index)` : String에서 해당 index의 character를 반환합니다. (char형으로)   
`ex) String str = 'abcde' / str.charAt(2) == 'c'`
* `substring(int start, int end)` : start index부터 end index까지의 부분문자열을 반환합니다. (start index만 작성한다면 start index부터 문자열 끝까지 반환)  
`ex) String str = 'abcde' / str.substring(2, 5) == 'cde'`
* `equals()` : 문자열이 같은지 판단한다 (같은지 틀린지)
* `compareTo()` : 문자열이 같은지 판단한다 (사전순으로 어떤게 앞서는지 비교가능)  
ex) `str1.compareTo(String str2)` return value  
    * 0 : 같은 문자열
    * return value > 0 : str2가 사전순으로 앞에 존재
    * return value < 0 : str1이 사전순으로 앞에 존재
* `compareToIgnoreCase()` : 대소문자 구별없이 비교
* `equalsToIgnoreCase()` : 대소문자 구별없이 비교
* `indexOf(int ch)` : 해당 문자열에서 처음으로 발견되는 index 반환
* `indexOf(int ch, int fromIndex)` : 만약 문자열 상에 a가 3개 있을 때, fromIndex로 몇번째 a의 인덱스를 반환할 지 정해줍니다.
* `indexOf(String str)` : str이 나오는 처음 인덱스를 반환
* `lastIndexOf(int ch)` : 마지막부터 탐색합니다.
    ```
    ex)
    String str1= "abade"
    str1.indexOf("a") == 0  
    str1.indexOf("a", 1) == 2
    str1.lastIndexOf("a") == 2
    ```


### Collection 관련
* `size()` : 컬렉션 프레임워크 타입의 길이를 알고자 할 때 사용되는 메소드이다.
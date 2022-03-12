# List 형태를 Page 형태로 변경하는 방법

해결한 코드부터 보자면 아래와 같은 방법을 사용했다.  
자신의 상황과 맞게 코드를 변경해서 사용하자.

```java
// List To Page
final int start = (int)pageable.getOffset();
final int end = Math.min((start + pageable.getPageSize()), allRequestList.size());
final Page<GetRequestListResDTO> requestListPages = new PageImpl<>(allRequestList.subList(start, end), pageable, allRequestList.size());
```

* `pageble.getOffset();` : [스프링 프레임워크 Pageble 공식 문서](https://docs.spring.io/spring-data/commons/docs/current/api/org/springframework/data/domain/Pageable.html)를 보면 이렇게 적혀있다.
    > Returns the offset to be taken according to the underlying page and page size.  
    > 기본 페이지 및 페이지 크기에 따라 취할 오프셋을 반환합니다.

    즉 이걸 시작점으로 잡는거다.

* `Math.min()` : 입력받은 두개의 인자 값 중에 작은 값을 리턴하는 메서드이다.  
인자 값으로는 `int`, `float`, `long`, `double` 등을 사용할 수 있다.

* `PageImpl<>()` : Page 인터페이스를 구현한 구현체로 수동으로 Page 타입을 만들 수 있다.

* `subList()` : 말 그대로 array를 자르는 메서드다.

추가로 Page로 처리했을 때 반환되는 값을 정리합니다.
```json
"pageable": {
            "sort": {
                "sorted": false, // 정렬상태 (클라이언트에서 파라미터로 설정가능)
                "unsorted": true,
                "empty": true
            },
            "pageNumber": 0,  // 현재 페이지 번호
            "pageSize": 7, // 한 페이지에서 나타내는 데이터 수
            "offset": 0, // 해당 페이지에서 첫번째 글 idx (지금은 0번째 페이지라 첫 글 idx가 1이라 0으로 표시, 1번째 페이지라면 8번째 게시물이 이 페이지에서 첫번째 글임 하지만 배열처럼 0부터 시작이라 7로 표시될 것)
            "paged": true,
            "unpaged": false
        },
        "last": false,  // 마지막 페이지 여부
        "totalPages": 6,  // 전체 페이지 갯수
        "totalElements": 42,  // 모든 페이지에 존재하는 총 글의 수
        "numberOfElements": 7, // 요청 페이지에서 조회 된 데이터 갯수
        "sort": {
            "sorted": false,
            "unsorted": true,
            "empty": true
        },
        "number": 0, // 현재 페이지 number
        "size": 7, // 한 페이지에서 보여줄 데이터 갯수, (클라이언트에서 설정가능)
        "first": true, // 첫페이지 여부
        "empty": false // 리스트가 비어있는지 여부
    }
```
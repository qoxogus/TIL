# default_batch_fetch_size 옵션
Hibernate에는 여러 자식들이 있을 때 N + 1 문제를 피하기 위해 `hibernate.default_batch_fetch_size`라는 옵션이 있습니다.  

yml에 이러한 형식으로 추가해주면 적용됩니다.  
```yml
spring:
    jpa:
        properties:
            hibernate:
                default_batch_fetch_size: 1000
```

위의 옵션은 하위 엔티티를 로딩할 때 한번에 상위 엔티티를 지정한한 숫자만큼 in query로 로딩해줍니다. (한방쿼리)

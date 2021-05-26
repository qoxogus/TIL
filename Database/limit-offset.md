# Limit, offset
: `Limit`이란 단어는 "한계", "한도" 라는 단어 뜻을 가지고 있다.
[MySQL, Oracle 등에서 사용 할 수 있다]

Select쿼리문에서 Limit을 사용하면 테이블 데이터 조회시 **한계를 지정**할 수 있다. (페이징)

- 테이블에서 10개의 데이터만 가져오기
```sql
SELECT idx, username, age FROM member LIMIT 10;
```

`offset` 옵션을 이용하면, **가져오고자 하는 데이터 행의 시작점을 지정**할 수 있다.

- `limit`, `offset`을 이용하여 11번째부터 20번째행까지의 데이터를 가져와보자
```sql
SELECT idx, username, age FROM member LIMIT 10, 10;
```
(`offset`의 값은 0부터 시작하므로 첫번 째 행 데이터를 가리키는 값은 0이다  (`첫번째 데이터 행 == offset(0)`)
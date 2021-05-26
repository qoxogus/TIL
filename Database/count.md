# Count
: 테이블에 존재하는 데이터의 개수를 가져오고 싶을 때 사용하는 데이터베이스 함수이다. **(NULL인 데이터는 제외하고 계산한다)**
[MySQL, Oracle 등 사용가능]

### 전체 행 개수 가져오기
```sql
SELECT COUNT(*) FROM {TABLE_NAME};
```
> 전체 행 개수를 가져올 때는 컬럼 대신에 `*`을 지정합니다.

### 컬럼 데이터 개수 가져오기
```sql
SELECT COUNT(column) FROM {TABLE_NAME};
```

8명의 회원이 저장되어있는 테이블이 있다고 가정해보자  (`name`컬럼 8개중에 하나는 `NULL`이다)

- 전체 행 개수 가져오기
```sql
SELECT COUNT(*) as cnt FROM member;
```
- 결과

![](../img/count-image.png)

- 이름 개수 가져오기
```sql
SELECT COUNT(name) as cnt FROM member;
```
- 결과

![](../img/count-name-img.png)
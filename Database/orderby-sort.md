# order by와 정렬
:테이블에서 select로 데이터를 조회할 때, order by를 추가하여 지정된 컬럼을 기준으로 정렬할 수 있다.
[MySQL, Oracle 등에서 사용가능]
오름차순(ASC)과 내림차순(DESC) 두가지 정렬방법이 있습니다.
default값은 오름차순(ASC)입니다.
> 컬럼명이 아닌 컬럼번호로 정렬을 지정할 수도 있습니다.

- 기본 조회
```sql
SELECT * FROM member;
```

- 오름차순 정렬 (ASC default값이라 생략 가능)
```sql
SELECT * FROM member ORDER BY age  ASC;
```

- 내림차순 정렬
```sql
SELECT * FROM member ORDER BY age DESC;
```

- 여러 컬럼으로 정렬
```sql
SELECT * FROM {TABLE_NAME} ORDER BY {컬럼1 [, 컬럼2, 컬럼3, ...]};
```

- 조건식이 있는 경우 정렬
```sql
SELECT username, age FROM member WHERE age > 10 ORDER BY age DESC;
```

- 컬럼 번호로 정렬
```sql
SELECT * FROM {TABLE_NAME} WHERE {조건식} ORDER BY {컬럼번호1 [, 컬럼번호2, 컬럼번호3, ...]};
```

- age내림차순, username오름차순 정렬
```sql
SELECT username, age FROM member ORDER BY age DESC, username;
```

- age내림차순, username오름차순 컬럼번호로 정렬
```sql
SELECT username, age FROM member ORDER BY 1, DESC 2;
```
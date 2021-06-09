# DDL, DML, DCL이란?

### DDL(Data Definition Language)
: 데이터베이스의 스키마 객체를 **생성(CREATE)**, **변경(ALTER)**, **제거(DROP)** 하거나 권한의 부여나
**박탈(GRANT, REVOVE)**, **주석(COMMENT)**, **자료의 버림(TRUNCATE)** 등을 수행하는 문장의 집단을 의미한다.  
> 각 문장은 `CREATE, ALTER, DROP, TRUNCATE, GRANT, REVOKE, COMMENT`등으로 시작한다.

### DML(Data Manipulation Language)  [Manipulation = 교묘한처리, 조종]
: 스키마 객체의 데이터를 **입력(INSERT)**, **수정(UPDATE)**, **조회(SELECT)**, **삭제(DELETE)** 하거나 **테이블에 잠금을 설정하거나 (LOCK TABLE)**, **SQL문의 처리의 절차에 대한 정보를 얻거나 (EXPLAIN PLAN)**, **PL/SQL 모듈을 호출하는 작업(CALL)** 의 집단이다.  
> 각 문장은 `INSERT, UPDATE, DELETE, SELECT, LOCK TABLE, EXPLAIN PLAN, CALL`등으로 시작된다.

### DCL(Data Control Language)
: 트랜잭션의 성격을 제어하는 것으로서 
> `SET TRANSACTION, COMMIT, ROLLBACK, SAVEPOINT`와 같은 종류가 있다.
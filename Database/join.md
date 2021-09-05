# Join
`JOIN`은 **DB내의 여러 테이블의 레코드를 조합하여 하나의 결과 집합으로 만드는 것**이다.  

`INNER JOIN`, `OUTER JOIN`이 있으며    
`INNER JOIN`에는 `EQUI JOIN`, `NON EQUI JOIN`, `NATURAL JOIN`, `CROSS JOIN`  
`OUTER JOIN`에는 `LEFT`, `RIGHT`, `FULL`로 종류가 있다.  
> `FULL OUTER JOIN`은 **일부 DBMS에서만 지원**한다.

### INNER JOIN과 OUTER JOIN의 차이점
* INNER JOIN  
: 교집합으로, JOIN대상이 되는 컬럼에서 A/B 양쪽 다 있는 경우  
    > 두 테이블에 공통으로 존재하는 컬럼을 이용하는 방식  

    * EQUI JOIN  
    : 공통 존재 컬럼의 값이 같을 경우 추출  
        > 흔히 사용하는 JOIN의 형태이며 주로 Primary Key와 Foreign Key컬럼이 서로 JOIN될 때 이용되는 형태이다.  
        (조건 절에 조인되는 두 테이블의 컬럼을 Equal 연산자(=)로 연결하는 경우)

    * NON EQUI JOIN  
    : 특정 컬럼을 범위로 JOIN시키는 방식  
    조인 조건이 Equal 연산자 이외의 >, >=, <, <=, BETWEEN … AND 등의 연산자들을 이용하여 조인을 하는 경우 이다.
        > 한 테이블의 어떠한 칼럼도 JOIN 할 테이블의 컬럼에 직접적으로 일치하지 않는 경우에 사용 한다.

    * NATURAL JOIN  
    : 두 테이블의 모든 컬럼을 비교하여 같은 컬럼명을 가진 모든 컬럼값이 같은 경우를 추출

    * CROSS JOIN  
    : 조인 조건이 없는 모든 데이터의 조합을 추출
        > 쓰레기값이 많다.

* OUTER JOIN  
: 종류에 따라 결과물이 조금씩 달라진다.  
    > 특정 테이블의 모든 데이터를 기준으로 다른 테이블의 정보를 추출하는 방식  
    (다른 테이블에 값이 없어도 출력가능)

    * LEFT OUTER JOIN  
    : A의 모든 열과 B에 있는 공통 부분을 얻게되고,  
    A에 있지만 B에 없는 내용의 경우 우측은 NULL로 처리  
        > 왼쪽 테이블의 모든 데이터와 오른쪽 테이블의 동일 데이터를 추출

    * RIGHT OUTER JOIN  
    : B의 모든 열과 A에 있는 공통 부분을 얻게되고,  
    B에는 있지만 A에는 없는 내용의 경우 좌측은 NULL로 처리  
        > 오른쪽 테이블의 모든 데이터와 왼쪽테이블의 동일 데이터를 추출

    * FULL OUTER JOIN  
    : A와 B의 합집합
        > 양쪽의 모든 데이터를 추출한다.
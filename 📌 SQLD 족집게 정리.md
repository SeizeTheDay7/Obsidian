## 1. 연산 순서 정리

FROM - WHERE - GROUP BY - HAVING - SELECT - ORDER BY

## 2. 명령어 분류

DML : SELECT, INSERT, DELETE, UPDATE
DDL : ALTER, CREATE, MODIFY, DROP
TCL : ROLLBACK, COMMIT
DCL : GRANT, REVOKE

## 3. DISTINT

중복되는 값을 묶는다
DISTINCT DEPTNO, MGR 이라면 DEPTNO, MGR에 괄호 묶여 있다고 생각
= GROUP BY (DEPTNO, MGR) 비슷하다

## 4. AS

SELECT에선 AS 생략 가능하다.
칼럼 명에 띄어쓰기 있으면 "직원 이름" 이렇게 묶어줘야 한다.

FROM에는 AS 쓰면 안된다. (띄어쓰기로 별칭)

## 5. CONCAT

SQL server 에서는 +, ORACLE에서는 = 사용

## 6. 연산 순위

1. NOT
2. AND
3. OR

NAO로 두문자 암기

## 7. ROWNUM, TOP

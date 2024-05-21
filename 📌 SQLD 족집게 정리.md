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

ROWNUM : ORACLE에서 사용됨.  SELECT해온 데이터에 일련번호를 붙임
```MYSQL
SELECT * FROM EMP WHERE ROWNUM <= 10;
```
WHERE 옆에 사용되고, 1부터 시작됨.

TOP : SQL server에서 사용됨. 상위 n개 보여줌.
```MYSQL
SELECT TOP [조회할 레코드 수] [컬럼명]
FROM [테이블명]
WHERE [조건절]
ORDER BY [컬럼명]
```

ORDER BY는 가장 마지막에 실행되기 때문에 일단 상위 N개 뽑고 난 후에 정렬됨.

## 8. NULL 관련 함수

**NVL(값1, 값2)** : 값1이 NULL이면 값2
**NVL2(값1, 값2, 값3)** : 값1이 NULL이 아니면 값2, NULL이면 값3
**ISNULL(값1, 값2)** : NVL과 동일함
**NULLIF(값1, 값2)** : 같으면 NULL, 다르면 값1
**COALESCE(값1, 값2, ...)** : NULL 아닌 첫번째 값

## 9. 정렬

- 가장 마지막에 실행
- 성능이 느려질 수 있다
- 출력되는 컬럼의 수보다 큰 값 불가능
- SAL DESC, ENAME ASC : SAL이 같으면 ENAME 오름차순 정렬
- 출력되지 않은(SELECT하지 않은) 컬럼으로 정렬 가능

## 10. CASE WHEN

```MYSQL
CASE WHEN 칼럼이름 = 조건식1 THEN 값1
		WHEN 칼럼이름 = 조건식2 THEN 값2
```

```MYSQL
CASE 칼럼이름 WHEN 조건식1 THEN 값1
			WHEN 조건식2 THEN 값2
```

ELSE가 없을 때 조건식1, 조건식2 만족하지 않으면 NULL 출력됨

## 11. NULL 문제 예시

| A    | B    | C   | A+B+C |
| ---- | ---- | --- | ----- |
| NULL | NULL | 1   | NULL  |
| 3    | 2    | 2   | 7     |
| NULL | 2    | 3   | NULL  |
`COUNT(A)` = 1
`COUNT(*)` = 3
`SUM(A+B+C)` = 7

## 12. JOIN

NATURAL JOIN과 USING은 중복된 컬럼을 하나로만 출력한다. 제일 앞에 등장한다.
**USING은 별칭 사용 불가능하다.**

A LEFT OUTER JOIN B는
A.COL1 = B.COL1 (+)와 의미가 같다.

FROM A, B, C 로 JOIN을 한다면 A,B를 JOIN한 결과를 C와 또다시 JOIN

## 13. 서브쿼리

| 절        | 서브쿼리       | 비고              |
| -------- | ---------- | --------------- |
| SELECT   | 스칼라 서브쿼리   |                 |
| FROM     | 인라인 뷰      | 메인 쿼리의 컬럼 사용 가능 |
| WHERE    | 거의 모든 서브쿼리 | 중첩 서브 쿼리 가능     |
| GROUP BY | **사용 불가**  |                 |
| HAVING   | 거의 모든 서브쿼리 | 중첩 서브 쿼리 가능     |
| ORDER BY | 스칼라 서브쿼리   |                 |

## 14. 조건 연산자

IN : 서브쿼리나 목록에 있는 값들과 일치하는지 확인
```MYSQL
SELECT employee_id, first_name
FROM employees
WHERE department_id IN (10, 20, 30);
```

ANY/SOME : 서브쿼리에서 반환된 값 하나라도 조건을 만족하는지
```MYSQL
SELECT employee_id, first_name
FROM employees
WHERE salary > ANY (SELECT salary FROM employees WHERE department_id = 30);
```

ALL : 서브쿼리에서 반환된 모든 값이 조건을 만족하는지
```MYSQL
SELECT employee_id, first_name
FROM employees
WHERE salary > ALL (SELECT salary FROM employees WHERE department_id = 30);
```

EXISTS : 서브쿼리가 한 개 이상의 행을 반환하면 TRUE
```MYSQL
SELECT employee_id, first_name
FROM employees e
WHERE EXISTS (SELECT 1 FROM departments d WHERE e.department_id = d.department_id AND d.location_id = 1700);
```

## 15. 집합 연산자

- UNION :  중복 허용 안한다. 정렬 작업을 해야해서 느리다.
- UNION ALL : 중복 허용 한다. 정렬 작업 안해서 빠르다.
- INTERSECT : 교집합
- MINUS : 교집합 뺀다

## 16. DDL

- TRUNCATE vs DROP : TRUNCATE는 구조 남음(입주민 퇴거), DROP은 전부 지움(건물 철거)

 - TRUNCATE vs DELETE : TRUNCATE는 DDL이고, DELETE는 DML이다.

## 17. 제약 조건

- PK = UNIQUE + NOT NULL
- UNIQUE
- NOT NULL

## 18. DCL

- GRANT : 특정 데이터베이스 사용자에게 특정 작업에 대한 수행 권한을 부여
- REVOKE : 수행 권한 박탈
- COMMIT
- ROLLBACK

## 19. VIEW

독편보
- 독립성
- 편리성
- 보안성

## 20. 그룹 함수

빵꾸 뚫고 ROLLUP인지 CUBE인지 뭔지 찾는 문제

- ROLLUP : GROUP BY에 소계 추가. ROLLUP(A, B)와 ROLLUP(B, A)는 결과가 다름.
- CUBE : 명시되지 않은 소계 추가. CUBE(A, B)와 CUBE(B, A)는 결과가 같다.
- GROUPING SETS : 특정 항목에 대한 소계.
- GROUPING : 집계되면 1, 아니면 0

## 21. 윈도우 함수

- ROWS, RANGE 차이점 : RANGE에는 중복된 값 존재
- RANK, DENSE_RANK 차이점 : RANK는 등수 건너 뛰고 DENSE_RANK는 안 건너뛴다.

## 22. 계층형 질의

- PRIOR 자식데이터 = 부모데이터 (부모에서 자식으로 가는 질의)
- 부모에서 자식으로 가면 순방향

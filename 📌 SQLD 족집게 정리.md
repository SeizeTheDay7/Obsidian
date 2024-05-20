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
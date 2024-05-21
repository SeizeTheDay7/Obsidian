- [[#MySQL|MySQL]]
	- [[#MySQL#단축키|단축키]]
	- [[#MySQL#MySQL에서 주석 작성 방법|MySQL에서 주석 작성 방법]]
	- [[#MySQL#강의에 나왔던거 일단 정리|강의에 나왔던거 일단 정리]]
		- [[#강의에 나왔던거 일단 정리#ALTER|ALTER]]
		- [[#강의에 나왔던거 일단 정리#DROP|DROP]]
		- [[#강의에 나왔던거 일단 정리#TRUNCATE|TRUNCATE]]
	- [[#MySQL#명령어|명령어]]
		- [[#명령어#CREATE TABLE|CREATE TABLE]]
			- [[#CREATE TABLE#AUTO_INCREMENT|AUTO_INCREMENT]]
		- [[#명령어#SELECT|SELECT]]
		- [[#명령어#FROM|FROM]]
		- [[#명령어#WHERE|WHERE]]
		- [[#명령어#GROUP BY|GROUP BY]]
			- [[#GROUP BY#집계함수|집계함수]]
		- [[#명령어#ORDER BY|ORDER BY]]
		- [[#명령어#LIMIT|LIMIT]]
		- [[#명령어#DISTINCT|DISTINCT]]
		- [[#명령어#INDEX|INDEX]]
		- [[#명령어#VIEW|VIEW]]
		- [[#명령어#INSERT|INSERT]]
		- [[#명령어#UPDATE|UPDATE]]
		- [[#명령어#DELETE|DELETE]]
		- [[#명령어#INNER JOIN|INNER JOIN]]
		- [[#명령어#OUTER JOIN|OUTER JOIN]]
		- [[#명령어#CROSS JOIN|CROSS JOIN]]
		- [[#명령어#SELF JOIN|SELF JOIN]]
		- [[#명령어#Stored Procedure|Stored Procedure]]
			- [[#Stored Procedure#IF|IF]]
			- [[#Stored Procedure#IF~ELSE|IF~ELSE]]
				- [[#IF~ELSE#IF문 예시|IF문 예시]]
			- [[#Stored Procedure#CASE|CASE]]
				- [[#CASE#case문 예시|case문 예시]]
			- [[#Stored Procedure#WHILE|WHILE]]
				- [[#WHILE#while문 예시|while문 예시]]
			- [[#Stored Procedure#ITERATE, LEAVE|ITERATE, LEAVE]]
		- [[#명령어#동적 SQL (PREPARE, EXCUTE)|동적 SQL (PREPARE, EXCUTE)]]
- [[#SQLD 이론|SQLD 이론]]



## MySQL
<hr>

### 단축키

`Ctrl+Enter` : 커서가 있는 1개의 SQL문 실행 (세미콜론 끝날때까지)
`Ctrl+Shift+Enter` : 모든 SQL문 실행 (드래그하면 그 부분만 실행)

### MySQL에서 주석 작성 방법

1. `#` 으로 작성
2. `--` : 마이너스 기호 2번 작성
3. `/* ~ */` : 여러 개의 줄을 한번에 주석 처리 

### 강의에 나왔던거 일단 정리
#### ALTER
```mysql
alter table 테이블이름 rename column 칼럼이름 to 칼럼이름2;
alter table 테이블이름 modify 칼럼이름 char(5) not null;
alter table 테이블이름 drop primary key;
alter table 테이블이름 add constraint 어쩌구저쩌구
```
 - 테이블이나 칼럼의 구조를 변경하는 명령
 - 제약조건을 추가하거나 삭제하는 명령
#### DROP
```mysql
drop table 테이블명 (cascade constraint);
```
- 테이블이나 특정 객체를 삭제하는 명령
- 테이블 내 데이터와 구조를 삭제
- cascade constraint 옵션은 종속된 제약 조건도 모두 삭제
#### TRUNCATE
```mysql
truncate table 테이블명;
```
- 테이블 구조는 남겨두고 내부의 데이터, 행만 삭제하는 명령어.
- 테이블이 차지하던 저장공간을 반납한다.


### 명령어

```mysql
SHOW DATABASES; # 데이터베이스 전부 보여줌
```

```mysql
CREATE SCHEMA '데이터베이스이름'; # 데이터베이스 만듦
```

```mysql
USE 데이터베이스이름; # 앞으로 모든 SQL 문이 해당 데이터베이스에서 수행됨
# 아니면 MySQL에서 데이터베이스 더블클릭해도 됨.
```
#### CREATE TABLE
```mysql
CREATE TABLE `shop_db`.`member` ( # 'shop_db'에 'member'테이블을 만든다.
  `member_id` CHAR(8) NOT NULL,
  `member_name` CHAR(5) NOT NULL, # 그 안에 칼럼 3개를 만든다.
  `member_addr` VARCHAR(45) NULL, # NOT NULL은 NULL값 허용 안한다는 뜻
  PRIMARY KEY (`member_id`)); # PK는 'member_id'이다.
```
##### AUTO_INCREMENT
```mysql
create table 테이블이름 (
	toy_id int auto_increment primary key, # 자동으로 1씩 증가시키며 값 설정 (pk여야함)
    toy_name char(4),
    age int);

insert into 테이블이름 values (null, '바보', 22); # 이후엔 null로 설정해도 값 자동 부여됨

alter table 테이블이름 auto_increment=100; # 시작 값 초기화
set @@auto_increment_increment=3; # 3씩 증가하게 변경
```
[정리글](https://velog.io/@ejayjeon/MYSQL-autoincrement-%EC%83%9D%EC%84%B1-%EC%B6%94%EA%B0%80-%EC%82%AC%EC%9A%A9-%EB%93%B1-%EC%A0%95%EB%A6%AC)
#### SELECT
```mysql
SELECT 칼럼이름 # 순서가 맞지 않으면 오류 발생
	FROM 테이블이름
	WHERE 조건식
	GROUP BY 칼럼이름
	HAVING 조건식
	ORDER BY 칼럼이름
	LIMIT 숫자
```
#### FROM
```mysql
SELECT * FROM 데이터베이스이름.테이블이름; # 모든 데이터 가져옴

SELECT 칼럼이름1, 칼럼이름2 FROM 테이블이름; # 특정 속성만 가져옴
SELECT 칼럼이름1 별칭1, 칼럼이름2 '별칭 2' FROM 테이블이름; # 칼럼 이름을 별칭으로 표시
```
#### WHERE
```mysql
SELECT * FROM 테이블이름 WHERE 칼럼이름='특정값'; # 특정 속성값만 가져옴 
SELECT * FROM 테이블이름 WHERE 칼럼이름>=값 AND 칼럼이름2<값 ; # 조건 2개 만족하는거 조회
	# 조건 : AND, OR, BETWEEN 값1 AND 값2

SELECT * FROM 테이블이름 WHERE 칼럼이름 IN('값1', '값2', '값3'); # 조건에 포함되는거 조회
SELECT * FROM 테이블이름 WHERE 칼럼이름 LIKE '우%'; # 우설, 우산꽂이 등 조회
SELECT * FROM 테이블이름 WHERE 칼럼이름 LIKE '__핑크'; # 무적핑크, 블랙핑크 등 조회
```
#### GROUP BY
```mysql
SELECT 집계함수(칼럼이름) FROM 테이블이름 GROUP BY 칼럼이름; # 속성 값 별로 묶여서 계산됨
# group by를 쓸 땐 where을 쓰면 안된다. having을 써야 한다. (where과 having은 비슷함)
```
##### 집계함수
| 함수명             | 설명                            |
| --------------- | ----------------------------- |
| AVG()           | 평균을 구함                        |
| MIN()           | 최소값을 구함                       |
| MAX()           | 최대값을 구함                       |
| COUNT()         | 행의 개수를 세어 반환                  |
| COUNT(DISTINCT) | 행의 개수를 세어 반환. 중복되는 값은 1개만 인정됨 |
| STDEV()         | 표준편차를 계산                      |
| VAR_SAMP()      | 표본 분산을 계산                     |
#### ORDER BY
```mysql
SELECT * FROM 테이블이름 ORDER BY 칼럼이름; # 특정 칼럼 기준으로 정렬
SELECT * FROM 테이블이름 ORDER BY 칼럼이름 DESC; # 내림차순 정렬 
SELECT * FROM 테이블이름 ORDER BY 칼럼이름1 DESC, 칼럼이름2 ASC; # 동률일 경우 처리
```
#### LIMIT
```mysql
SELECT * FROM 테이블이름 LIMIT 3; # 3개 행만 보여줌
SELECT * FROM 테이블이름 LIMIT 3,2; # 3번째부터 2개 행 보여줌
```
#### DISTINCT
```mysql
SELECT DISTINCT 칼럼이름 FROM 테이블이름; # 중복 없이 속성 값 보여줌
```
#### INDEX
```mysql
CREATE INDEX 인덱스이름 ON 데이터베이스이름.테이블이름(칼럼이름); 
# 인덱스를 만들어서 더 빠르게 조회
```
#### VIEW
```mysql
CREATE VIEW 뷰이름 # 뷰(유저에게 보여줄 쿼리의 변수명) 만들기
AS
	SELECT * FROM 테이블이름;

SELECT * FROM 뷰이름; # 뷰 불러오기
```
#### INSERT
```mysql
insert into 테이블이름 values (1, '우디', 25); # 새로 데이터를 추가함

insert into 테이블이름(toy_id, toy_name) values (2, '버즈'); # 특정 열에만 데이터 넣기

insert into 테이블이름(toy_name, age, toy_id) values ('제시', 20, 3); # 순서 바꿔도 됨
```

```mysql
insert into 테이블이름 (열이름1, 열이름2)
	select 문; # select한 데이터 가져와서 테이블에 넣어라
```
#### UPDATE
```mysql
update 테이블이름 # 기존에 입력된 값을 수정함
	set 열1=값1, 열2=값2, ...
	where 조건; # where 안 붙이면 테이블 전체 수정해버림
```

>[!bug] update 안됨
>Edit - Preferences - SQL Editor - (맨 밑) - Safe Updates 체크 해제 - workbench 끄고 재실행
#### DELETE
``` mysql
delete from 테이블이름 # 데이터 삭제
	where 조건;
```
#### INNER JOIN
```mysql
select <열 목록>
from <첫 번째 테이블>
	inner join <두 번째 테이블> # 그냥 join이라고 해도 기본은 inner join
	on <조인될 조건>
[where 검색 조건] # 생략 가능
```

INNER JOIN은 교집합이다. 두 테이블에 모두 데이터가 있어야만 결과가 나온다.

```mysql
select * # 전부 고른다
	from buy # buy 테이블에서
		inner join member # member 테이블을 합친 걸
        on buy.mem_id = member.mem_id # mem_id 기준으로
	where buy.mem_id = 'GRL'; # 'GRL'인 것만
```

>[!bug] 두 곳에 모두 있는 칼럼명을 select로 골랐을 때
>select mem_id, ... ← 오류 발생함
>select buy.mem_id, ... ← 테이블 지정해서 해결
#### OUTER JOIN
```mysql
select <열 목록>
from <첫번째 테이블(left 테이블)>
	<left | right | full> outer join <두 번째 테이블(right 테이블)>
	# left : left 테이블에 있는 건 전부 포함시키겠다.
	# right : right 테이블에 있는 건 전부 포함시키겠다
	# full : left, rigth 테이블에 있는 거 전부 포함시키겠다.
	on <조인될 조건>
[where 검색 조건];
```

OUTER JOIN은 한쪽에만 데이터가 있어도 결과가 나온다.

```mysql
select 테이블별칭1.칼럼이름
	from 테이블이름1 테이블별칭1
		inner join 테이블이름2 테이블별칭2
		on 테이블별칭1.칼럼이름 = 테이블별칭2.칼럼이름
```

테이블 별칭을 통해 쿼리문을 짧게 줄일 수 있다.

```mysql
select M.mem_id, M.mem_name, B.prod_name, M.addr
	from member M # left 테이블인 member 테이블을 기준으로
		left outer join buy B # 외부 조인 한다
		on M.mem_id = B.mem_id
	order by M.mem_id;
```
#### CROSS JOIN
```mysql
select *
	from 테이블이름1
		cross join 테이블이름2;
```

상호 조인은 한쪽 테이블의 모든 행과 다른 쪽 테이블의 모든 행을 조인시킨다.
상호 조인 결과의 전체 행 개수는 두 테이블의 각 행의 개수를 곱한 수가 된다.
간단하게 말해서 무지성으로 다 곱하는 조인이다.
테스트하기 위해 대용량의 데이터를 생성할 때 쓰인다.
#### SELF JOIN
```mysql
select <열 목록>
from <같은 테이블> 별칭A
	inner join <같은 테이블> 별칭B
	on <조인될 조건>
[where 검색 조건]
```

![](Pasted%20image%2020240519154706.png)

(실무에서 별로 안 쓰인다)
같은 테이블에서 또 데이터를 찾을 때 쓰인다.
똑같은 테이블을 하나 복사 한 후에 JOIN한다고 생각해도 된다.
#### Stored Procedure
```mysql
drop procedure if exists 프로시저이름; # 기존에 만든 적이 있다면 삭제

DELIMITER //  # 스토어드 프로시저를 묶어주는 양식
CREATE PROCEDURE 프로시저이름()
BEGIN
	실행하고자하는쿼리들;
END // # 스토어드 프로시저 종료
DELIMITER ; # 종료 문자를 다시 세미콜론으로 변경

CALL 프로시저이름(); # 프로시저 호출
```

스토어드 프로시저는 MySQL에서 프로그래밍 기능이 필요할 때 사용하는 데이터베이스 개체.

##### IF
```mysql
if <조건식> then
	실행하고자하는쿼리들
end if;
```

두 문장 이상이 처리될 땐 `BEGIN~END`로 묶어줘야 한다.

```mysql
delimiter $$ # 종료 문자를 $$로 바꾼다
create procedure ifProc1()
begin 
	if 100 = 100 then # mysql에서 비교문은 그냥 =
		select '100은 100과 같습니다.';
		select '당연한 이야기입니다.';
	end if;
end $$ # $$로 프로시저 끝낸다
delimiter ; # 종료 문자를 ;으로 되돌린다.

call ifProc1();
```
##### IF~ELSE
```mysql
delimiter $$
create procedure ifPRoc2()
begin
	declare myNum int; # 변수 선언
	set myNum = 200; # 변수에 값 대입
	if myNum = 100 then
		select '100입니다.';
	else
		select '100이 아닙니다.';
	end if;
end $$
delimiter ;
```
###### IF문 예시
```mysql
drop procedure if exists ifProc3;
delimiter $$
begin
	declare debutDate date;
	declare curDate date;
	declare days int;

	select debut_date into debutDate # debut_date 결과를 debutDate에 대입
		from marker_db.member
		where mem_id = 'APN';

	set curDate = current_date(); # 현재 날짜
	set days = datediff(curDate, debutDate); # 날짜의 차이, 일 단위

	if (days/365) >= 5 then # 5년이 지났다면
		select concat('데뷔한지',days,'일이 지났습니다');
	else
		select '데뷔한지'+days+'일밖에 안됐습니다.';
	end if;
end $$
delimiter ;
call ifProc3();
```
##### CASE
```mysql
delimiter $$
begin
	case
		when 조건1 then
			SQL문장들;
		when 조건2 then
			SQL문장들;
		when 조건3 then
			SQL문장들;
		else
			SQL문장들;
	end case;
end $$
delimiter ;
```
###### case문 예시
```mysql
select B.mem_id, M.mem_name, sum(price*amount) "총구매액",
	case
		when (sum(price*amount) >=1500) then '최우수고객'
        when (sum(price*amount) >=1000) then '우수고객'
        when (sum(price*amount) >=1) then '일반고객'
        else '유령고객'
	end "회원등급" # 별칭
	from buy B
		right outer join member M
        on B.mem_id = M.mem_id
	group by M.mem_id
    order by sum(price*amount) desc;
```
##### WHILE
```mysql
while <조건식> do
	SQL문장들
end while;
```
###### while문 예시
```mysql
drop procedure if exists whileProc;
delimiter $$
create procedure whileProc()
begin
	declare i int;
    declare hap int;
    set i = 1;
    set hap = 0;
    
    while (i <= 100) do
		set hap = hap + i;
        set i = i + 1;
	end while;
    
    select '1부터 100까지의 합 : ', hap;
end $$
delimiter ;
call whileProc();
```
##### ITERATE, LEAVE
![](Pasted%20image%2020240519163843.png)
#### 동적 SQL (PREPARE, EXCUTE)
```mysql
prepare myQuery from 'select * from member'; # sql 준비
excure myQuery; # 준비한 sql문 실행
deallocate prepare myQuery; # 준비한 문장 해제
```

prepare 문에서는 ?로 나중에 입력될 값을 비워 놓고,
execute 문에서는 using으로 ?에 값을 전달할 수 있다.

#### 윈도우 함수

[정리글1](https://schatz37.tistory.com/12) [정리글2](https://mizykk.tistory.com/121)

: 행과 행 간의 관계를 쉽게 정의하기 위해 만든 함수. GROUP BY는 집계된 결과만 보여주는 반면, 왼도우 함수는 기존 데이터에 집계된 값을 추가하여 나타낸다.

**(GROUP BY를 사용했을 경우)**
집계된 값만 나타난다.

![](Pasted%20image%2020240521101830.png)

**(윈도우 함수를 사용했을 경우)**
기존 데이터에 집계된 값이 추가되어 나타난다.

![](Pasted%20image%2020240521101908.png)

![](Pasted%20image%2020240520220934.png)

```mysql
select 윈도우함수([대상]) over([partition by 칼럼])
							[order by 칼럼 asc|desc]
							[rows|range between a and b]);
```


## SQLD 이론
<hr>

개별적 관점의 외부 스키마를 모아서  
통합적 관점의 개념 스키마를 만들고, 그로부터  
물리적으로 저장하는 내부 스키마를 만든다  
  
엔터티 발생시점 분류 : 기본, 중심, 행위  
  
기본 속성 : 원래속성  
설계 속성 : 1:1치환  
파생 속성 : 계산값  
  
대표성 갖는지 : 주식별자/보조식별자  
스스로 생성됐는지 : 내부식별자/외부식별자  
단일 속성으로 식별되는지 : 단일식별자/복합식별자  
업무적으로 의미있는지 : 본질식별자/인조식별자  
  
이름은 주식별자 쓰면 안된다  
  
슈퍼키(식별만 되면 됨) > 후보키(더 뺄 수 없음) > 기본키(유일)  
후보키 중에 기본키 아닌거 : 대체키  
  
2차 정규화할 때 기본키가 복합키면 복합키 기준으로 나눔  
  
속성 여러개를 다시 묶는건 1차 정규화 (이미 1차 정규화 돼있는것도 가능)  
  
정규화는 논리 데이터 모델 일관성 확보  
  
식별 관계 : 부모 테이블의 기본키를 자식의 기본키로 사용  
비식별 관계 : 부모 테이블의 기본키를 자식에서 외래키로 사용  
  
NULL 값에 숫자 더해도 NULL, 비교하면 FALSE 또는 unknown, 집계 함수 계산에선 아예 빠짐

![](다운로드.png)

트랜잭션 : 데이터베이스 read, write 연산 수행하는 단위

|ACID 원리|설명|
|---|---|
|원자성|트랜잭션의 수행은 성공하거나 실패해야 함|
|일관성|트랜잭션은 데이터의 일관성을 보장해야 함|
|고립성|동시에 수행되지 않고 각각 고립되어 실행되어야 함|
|영속성|완료(commit)된 뒤에 데이터가 유실되지 않아야 함|

유일성 : 각각을 식별할 수 있는지
최소성 : 더 적은 속성으로 식별할 수 있는지
슈퍼키 : 유일성 확보된 모든 키
대체키 : 기본키 아닌 후보키
후보키 : 최소성, 유일성 만족한 키
기본키 : 후보키 중 하나만 고른 키

엔터티의 요건
1. 업무에서 필요하고 관리하고자 하는 정보
2. 유일한 식별자가 있어야 함
3. 한 개가 아니라 두 개 이상의 인스턴스 존재
4. 업무 프로세스에 의해 이용됨
5. 속성이 있어야 함
6. 다른 엔터티와 한 개 이상의 관계 있음 (코드, 통계 엔터티는 편의상 생략)

비식별자 관계 : 주 식별자에 부모의 식별자 사용 안 함

기본 속성 : 업무상 수집된 기본 속성
설계 속성 : 코드 등 시스템에서 만든 속성
파생 속성 : 계산값이나 영향 받은 값

[정리글](https://mangkyu.tistory.com/110)
제1 정규화 : 한 칸에 데이터 하나만 (속성 묶는 것도 가능)  
제2 정규화 : 기본키로 찾을 수 있는 속성은 key-value 테이블로 따로 빼기  
제3 정규화 : 다른 키로 찾을 수 있는 속성은 테이블로 따로 빼기  
  
슈퍼/서브 타입 데이터 모델 : 객체 지향 상속이랑 비슷함


| 분류                                                | 설명                                                                |                     주요 명령어                      |
| :------------------------------------------------ | :---------------------------------------------------------------- | :---------------------------------------------: |
| 데이터 정의어<br>(DDL : Data <br>Definition Language)   | 데이터와 데이터간의 <br>관계 정의를 위한 언어.<br>데이터 구조 또는 객체를<br>생성, 변경, 삭제하는데 사용 |        CREATE<br>ALTER<br>DROP<br>RENAME        |
| 데이터 조작어<br>(DML : Data <br>Manipulation Language) | 데이터베이스 사용자 또는<br>응용 프로그램의 데이터<br>검색, 등록, 삭제, 갱신에 쓰임               | SELECT, FROM<br>WHERE, INSERT<br>UPDATE, DELETE |
| 데이터 제어어<br>(DCL : Data <br>Control Language)      | 데이터에 대한 액세스를 제어<br>하기 위한 언어.<br>데이터 보안, 무결성, 병행수행<br>제어에 사용됨.     |      GRANT<br>REVOKE<br>COMMIT<br>ROLLBACK      |
엑셀에서 테이블 만들었다고 했을 때, 기본적인 틀을 안 건드리면 DML
기본적인 틀을 건드리면 DDL

서브쿼리
1. 스칼라 서브쿼리
	- SELECT에 사용하는 서브쿼리
	- 서브쿼리 결과를 하나의 칼럼처럼 사용하기 위해 주로 사용
	- 조인의 대체연산 (성능이 안 좋아서 잘 사용하진 않음)

```mysql
select empno, ename,
		(select dname
		from dept d
		where d.deptno = e.deptno) as dname
from emp e
where deptno = 10;
```


2. 인라인 뷰
	- FROM 절에 사용하는 서브쿼리
	- 서브쿼리 결과를 테이블처럼 사용하기 위해 주로 사용

```mysql
select e.empno, e.ename, e.sal, i.avg_sal
from emp e, (select deptno, avg(sal) as avg_sal
			from emp
			group by deptno)
where e.deptno = i.deptno
and e.sal > i.avg_sal;
```

3. WHERE절 서브쿼리 (명칭 없음)
	- 가장 일반적인 서브쿼리
	- 비교 상수 자리에 값을 전달하기 위한 목적으로 주로 사용(상수항의 대체)
	- 리턴 데이터의 형태에 따라 단일행 서브쿼리, 다중행 서브쿼리, 다중칼럼 서브쿼리, 상호연관 서브쿼리로 나눔

WHERE 절 서브쿼리 종류
1. 단일행 서브쿼리
	- 서브쿼리 결과가 1개의 행이 리턴되는 형태
	- 같다(=), 같지 않다(<>) 등의 비교 연산자 사용 가능
2. 다중행 서브쿼리
	- 서브쿼리 결과가 여러 행이 리턴되는 형태
	- '=', '>', '<'와 같은 비교 연산자 사용 불가
	- 서브 쿼리 결과를 하나로 요약하거나 다중행 서브쿼리 연산자 사용

다중행 서브쿼리 연산자

| 연산자   | 의 미      |
| ----- | -------- |
| IN    | 같은 값을 찾음 |
| > ANY | 최소값을 반환함 |
| < ANY | 최대값을 반환함 |
| < ALL | 최소값을 반환함 |
| > ALL | 최대값을 반환함 |

3. 다중컬럼 서브쿼리
	- 서브쿼리 결과가 여러 칼럼이 리턴되는 형태
	- 메인쿼리와의 비교 칼럼이 2개 이상
	- 대소 비교 전달 불가

부서별 최대 봉급 수령자 확인
```mysql
select empno, ename, sal, deptno
	from emp
where (deptno, sal) in (select deptno, max(sal)
					   from emp
					   group by deptno);
```

4. 상호연관 서브쿼리
	- 메인쿼리와 서브쿼리의 비교를 수행하는 형태
	- 비교할 집단이나 조건은 서브쿼리에 명시

부서별로 해당 부서의 평균보다 많이 받는 수령자 확인
```mysql
select empno, ename, sal, deptno
from emp e1
where sal > (select avg(sal)
			from emp e2
			where e1.deptno = e2.deptno
			group by deptno);
```





계층형 질의
: 계층형 데이터(동일한 테이블에 계층적으로 상위와 하위 데이터가 포함)를 다루는 쿼리를 수행

```mysql
select ...
from ...
where 조건
start with 조건 # 데이터 전개가 시작될 데이터를 지정
connect by prior 자식 = 부모 # 부모에서 자식 방향 데이터 전개
[ order siblings by 칼럼명1, 칼럼명2 ... ];
```

## 집계 함수

**GROUP BY**
```MYSQL
SELECT 상품ID, 월, SUM(매출액) AS 매출액
FROM 월별매출
GROUP BY 상품ID, 월;
```

![](Pasted%20image%2020240521000339.png)

**ROLLUP**
[정리글](https://for-my-wealthy-life.tistory.com/44)
소그룹 간의 합계를 계산. GROUP BY로 묶은 각각의 소그룹 합계와 전쳬 합계 모두 구할 수 있음.
```MYSQL
SELECT 상품ID, 월, SUM(매출액) AS 매출액
FROM 월별매출
GROUP BY ROLLUP(상품ID, 월);
```

![](Pasted%20image%2020240521000458.png)

**CUBE**
항목들 간의 다차원적인 소계 계산. 명시한 모든 칼럼에 대해 소그룹 계산
```MYSQL
SELECT 상품ID, 월, SUM(매출액) AS 매출액
FROM 월별매출
GROUP BY CUBE(상품ID, 월);
```

![](Pasted%20image%2020240521000650.png)

**GROUPING SETS**
특정 항목에 대한 소계 계산
```MYSQL
SELECT 상품ID, 월, SUM(매출액) AS 매출액
FROM 월별매출
GROUP BY GROUPING SETS(상품ID, 월);
```

![](Pasted%20image%2020240521000758.png)

**GROUPING**
집계함수를 지원하는 함수. 집계가 계산된 결과는 1, 아니면 0
```MYSQL
SELECT 
    CASE GROUPING(상품ID) WHEN 1 THEN '모든 상품ID' ELSE 상품ID END AS 상품ID,
    CASE GROUPING(월) WHEN 1 THEN '모든 월' ELSE 월 END AS 월, 
    SUM(매출액) AS 매출액
FROM 월별매출
GROUP BY ROLLUP(상품ID, 월);
```

![](Pasted%20image%2020240521001026.png)

### Chapter 01 데이터베이스 기본
1. 트랜잭션
	↘️ 인가받지 않은 사용자로부터 데이터를 보장하기 위해 DBMS가 가져야하는 특성, 하나의 논리적 기능을 정상적으로 수행하기 위한 작업의 기본 단위
	- ***트랜잭션의 특성*** (==ACID==)
		- ==원자성==(Atomicity) : 트랜잭션내의 연산은 ==반드시 모두 수행 아니면 모두 수행되지 않아야==함
		- ==일관성==(Consistency) : 트랜잭션 ==수행 전과 수행 후의 상태가 같아==야 하는 성질
		- ==격리성(==Isolation) : ==동시에 실행==되는 트랜잭션들이 ==서로 영향을 미치지 않아야== 한다는 성질
		- ==영속성==(Durability) : ==성공이 완료==된 트랜잭션의 ==결과는 지속적으로 유지==되어야 한다.
	- 트랜잭션 제어어 (TCL)
		- COMMIT : 트랜잭션을 메모리에 영구적으로 저장하는 명령어
		- ROLLBACK : 트랜잭션 저장을 무효화 시키는 명령어
		- CHECKPOINT : ROLLBACK을 위한 시점을 저장하는 명령어
	- 트랜잭션 상태(활부완실철)![[Pasted image 20230926174128.png]]
2. 데이터 분석 함수 종류
	- 집계 함수 : 여러행 또는 테이블 전체 행으로 부터 하나의 결괏값을 반환하는 함수
	- 그룹 함수 : 소그룹 간의 소계 및 중계 등의 중간 합계 분석 데이터를 산출하는 함수
	- 윈도 함수 : 데이터베이스를 사용한 온라인 분석 처리 용도로 사용하기 위해 표준 SQL에 추가된 기능
3. SQL 기본
![[릴레이션 인스턴스.png]]
- 튜플(Tuple) : 릴레이션 구성하는 각각의 행 (가로)
- 카디널리티(Cardinality) : 튜플의 수
	==튜==플==카==디널리티==행==
- 속성(Attribute) : 릴레이션을 구성하는 각각의 열(세로)
- 차수(Dgree) : 속성의 수
	==속==성==차==수==열==
- 도메인(Domain) : 속성들이 가질수 있는 값들의 집합

| 데이터 정의어 | 테이블의 구조를 정의함 |CREATE, ALTER, DROP, TRUNCATE|
|---|---|---|
|데이터 조작어 | 데이터 조회/삽입/삭제/경 |SELECT, INSERT, UPDATE, DELETE|
|데이터 제어어|데이터베이스에 접근 권한|GRANT, REVOKE|
- DDL : 데이터 정의어, 테이블 생성, 수정, 삭제
1. CREATE : 데이터베이스, 테이블등 생성
	↘️ CREATE TABLE 테이블명()
2. ALTER : 테이블을 수정
	- 컬럼 추가
		↘️ ALTER TABLE 테이블명 ADD (컬럼명 타입);
	- 컬럼 변경
		↘️ ALTER TABLE 테이블명 MODIFY (컬럼명 타입);
	- 컬럼명 변경
		↘️ ALTER TABLE 테이블명 RENAME COLUMN 컬럼명 TO 바꿀컬럼명;
	- 컬럼 삭제
		↘️ ALTER TABLE 테이블명 DROP COLUMN 컬럼명;
3. DROP : 데이터베이스, 테이블 삭제
	- DROP TABLE 테이블명 CASCADE;
		↘️ 삭제 할때 참조된 테이블도 같이 삭제 O
	- DROP TABLE 테이블명 RESTRICT;
		↘️ 삭제 할때 참조되는 테이블 같이 삭제 X
- DML : 데이터 조작어, 데이터 베이스에 입력된 레코드 조회, 수정, 삭제
1. SELECT : 데이터 조회
	SELECT * FROM 테이블명
	- WHERE 조건
		↘️ where에는 집계함수 X having에 조건을 써야 한다.
	     WHERE 컬럼명 = ‘ OO ‘ 이런식으로 작성
		-  LIKE
		   WHERE 컬럼명 LIKE ‘%’
	           EX) WHERE 이름 LIKE ‘이%’
		   ↘️ 이~ 조회
		   EX) WHERE 이름 LIKE ‘%종%’
		   ↘️ 종 포함 조회
		- BETWEEN
		  WHERE 컬럼명 BETWEEN A IN B
		  EX ) BETWEEN 20 IN 30
		  ↘️ 20 이상 30이하
		- IN
		 WHERE 컬럼명 IN (A, B, C . . . 등)
	         괄호안에 숫자, 글자가 나옴
		  EX) WHERE 학년 IN (3, 4);
		  ↘️ 3, 4학년 조회
		- GROUP BY
		 ↘️ 직급별, 학과별 등등.. 그룹짓는 문제
		 SELECT에서 보고 GROUP BY로
		 EX) GROUP BY 학과
		- ORDER BY
		 ↘️ 오름차순, 내림차순 정렬
		 오름차순 : ORDER BY 기준컬럼 ASC
		 내림차순 : ORDER BY 기준컬럼 DESC
		 여러번 작성 가능
		 EX) ORDER BY A ASC, B DESC
		 ↘️ A는 오름차순, A의 값이 같으면 내림차순
		- HAVING 
		 ↘️ 집계 함수 조건일때
		 EX) 평균성적 90점 이상
		 ↘️ HAVING AVG(성적) >= 90 
2. INSERT : 데이터 삽입
	INSERT INTO 테이블명 ( ) VALUES ( );
	↘️ EX ) INSERT INTO 학생(이름, 학년, 학번) VALUES(‘이이이’, 4, 123);
3. UPDATE : 데이터 수정
	UPDATE 테이블명 SET 컬럼명 = ‘변경내용’
	↘️ 컬럼명에 적은 컬럼은 다 변한다.
	UPDATE 테이블명 SET 컬럼명 = ‘변경내용’ WHERE 컬럼명 = ‘변경조건’;
     ↘️ WHERE 붙여 컬럼을 정할 수 있다.
 4. TRUNCATE
	TRUNCATE TABLE 테이블명;
	 ↘️ 테이블 내의 모든 데이터 삭제
4. DELETE : 데이터 삭제
	DELETE FROM 테이블명 : 모든 행 삭제
	EX) DELETE FROM 학생 WHERE 이름 = ‘민수’;
	↘️ 학생 테이블에서 이름이 민수인 데이터 삭제
- DCL : 데이터 제어어, 데이터베이스에 접근하거나 객체에 권한 주는 언어
1. GRANT
	↘️ 특정 데이터베이스 사용자에게 특정 작업에 대한 수행 권한을 부여
	GRANT 권한 ON 테이블 TO 유저
	( 권한 종류 : SELECT, INSERT, DELETE 등 )
	EX ) 이종표에게 학생 테이블의 삭제 권한 부여
	↘️ GRANT DELETE ON 학생 TO 이종표
2. REVOKE
	↘️ 특정 데이터베이스 사용자에게 특정 작업에 대한 수행 권한을 박탈, 회수
	REVOKE 권한 ON 테이블 FROM 유저
	EX) 이종표에게 학생 테이블 삭제 권한 회수
	↘️ REVOKE DELETE ON 학생 FROM 이종표
## 💡💡💡키 종류💡💡💡
1. ==후보키==(Candidate Key)
 ↘️ 릴레이션을 구성하는 속성들 중에서 튜플을 유일하게 식별하기 위해 사용하는 속성들의 부분집합
 ==유일성과 최소성을 만족 해야한다.==
 모든 ==릴레이션에는 반드시 하나이상의 후보키가 존재==
 2. ==슈퍼키==(Super Key)
 ↘️ 한 릴레이션 내에 있는 속성들의 집합으로 구성된 키 
 ==유일성 O, 최소성 X==
3. ==기본키== (Primary Key)
 ↘️ 후보키 중에서 선택한 주 키 (Main Key),
 null 값 X,  동일한 값 중복 저장 X
4. ==대체키==(Alternate Key)
 ↘️ 기본키를 제외한 나머지 후보키
5. ==외래키==(Foreign key)
 ↘️ 다른 릴레이션의 기본키를 참조하고 있는 속성 또는 속성들의 집합.
 외래키로 지정하면 참조 릴레이션의 기본키에 없는 값은 입력할 수 없다.


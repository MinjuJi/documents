조인
- 한 개 이상의 테이블을 사용해서 데이터를 획득해야할 때 사용된다.
* 데이터베이스 정규화 작업을 통해서 정보들이 여러 개의 테이블로 나뉘어서
저장/관리되기 때문에 조인 작업을 SQL의 select 작업에서 필수적인 기술이다.
- 조인을 사용하면 한번에 여러 테이블에서 데이터을 조회할 수 있다.
- 작성방법
select table1.column, table2.column,  -- table1과 table2에 있는 데이터를 조회할 수 있다.
from table1, table2                   -- 획득할 데이터가 포함된 테이블을 조인시킨다.
where table1.column1 = table2.column2 -- 조인된 행들중에서 유효한 행만 필터링하기 위한 조건식

* from 절에 조인할 테이블을 정의하면, table1의 모든 행과 table2의 모든 행이 연결된다.
(table1의 행의 갯수 x table2의 행의 갯수) 만큼의 행을 가진 테이블이 메모리 생성된다.
* n개의 테이블을 조인했다면 n-1개의 조인 조건식이 필요하다
* 조회할 컬럼명이 동일할 때는 반드시 테이블명을 접두사로 붙여야 한다.
* 테이블에 별칭을 붙일 수 있다. 
select A.column, B.column, ...
from table1 A, table2 B
where A.column1 = B.column2

- 조인의 종류
- 등가조인
* 조인 조건에 참여하는 컬럼의 값이 서로 동일한 값을 가지는 경우
select A.column, B.column, ...
from table1 A, table2 B
where A.column1 = B.column2; <---- 등가조인 조건 (서로 값이 동일한 경우 조인)
- 비등가조인
* 조인 조건에 = 연산자가 아닌 다른 연산자가 포함되는 조인이다.
* 등급을 계산할 때 사용된다.
select A.column, B.column, ...
from table1 A, table2 B
where A.column >= B.column1  <--- 비등가 조인 조건
and A.column <= B.column2  <--- (=연산이 아닌 다른 연산자가 사용)
- 셀프조인(자체조인)
* 하나의 테이블을 이용해서 조인을 구성하는 것이다.
* 조직도, 카테고리, 메뉴처럼 하나의 테이블에 안에 
상위데이터, 하위데이터가 공존하는 경우 정보를 
한 번에 상위데이터와 하위데이터를 조회할 때 셀프조인이 필요하다.
* 하나의 테이블을 역할을 각각 나누어서 조인에 참여시켜야 한다.
select A.column, B.column, ...
from table1 A, table1 B     <--- 같은 테이블로 조인을 구성
where A.column1 = B.column2                          
- 포괄조인
* 포괄조인을 사용하면 조인 조건을 만족하지 않는 행도 조회할 수 있다.
* 포괄조인 연산자를 정보가 부족한 조인조건 부분에 넣는다.
select table1.column, table2.column, ...
from table1, table2
where table1.column(+) = table2.column

select table1.column, table2.column, ...
from table1, table2
where table1.column = table2.column(+)
* 포괄조인 연산자는 정보가 부족한 쪽에 null행을 생성한다.
null행은 반대편테이블의 하나 이상의 행과 조인할 수 있다.
* 포괄조인 연산자는 조인조건의 한쪽에만 표시할 수 있다.


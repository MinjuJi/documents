# 서브쿼리(sub query)
- 메인 쿼리 내부에 정의된 쿼리
- 다른 select 문의 내부에 정의된 select문을 서브쿼리라고 한다.
- 서브쿼리를 포함시킬 수 있는 곳
  + where 절	
  + having 절
  + from 절 (인라인뷰라고도 부른다)
- 서브쿼리 형식
```sql
  select column, column
  from table
  where column 연산자 (select column
                       from table)
```
- 서브쿼리의 특징
  + 서브쿼리는 한번만 실행된다.
  + 서브쿼리는 메인쿼리보다 먼저 실행된다.
  + 서브쿼리의 실행결과는 메인쿼리의 조건식에서 사용된다.
  + 조건식에서 비교값으로 사용되는 값이 쿼리의 실행결과로만 획득할 수 있을 때, 그 비교값을 조회하는 쿼리가 서브쿼리다.
- 서브쿼리 사용시 주의점
  + 서브쿼리는 반드시 괄호로 묶어야 한다.
  + 조건식의 오른쪽에 서브쿼리를 위치시키면 가독성이 높아진다.
  + 서브쿼리의 실행결과가 단일행인지, 다중행인지에 따라 적절한 연산자를 사용해야 한다.

```sql
  -- 전체 사원의 평균급여보다 급여를 적게 받는 사원들의 사원아이디, 이름, 급여를 조회하기
  -- 조건식에서 사원의 급여와 비교되는 전체사원의 평균급여는 select문의 실행결과로 획득되는 값이다.
  -- 따라서, where절에 사원들의 전체 평급을 조회하는 select문(서브쿼리)이 필요하다.
  select employee_id, first_name, salary
  from employees
  where salary < (select avg(salary)
                  from employees)
```

## 서브쿼리의 종류
- 단일행 서브쿼리
  + 서브쿼리의 실행결과로 한 행만 반환된다.
  + 단일행 비교 연산자
    * =, >, >=, <, <=, <>
- 다중행 서브쿼리
  + 서브쿼리의 실행결과로 여러 행이 반환된다.
  + 다중행 비교 연산자
    * in, any, all

| 단일행 서브쿼리 | 다중행 서브쿼리 |
| --- | --- |
| = | in |
| <> | not in |
| > | >any, >all |
| < | <any <all |

- 다중열 서브쿼리
  + 두 개 이상의 컬럼값이 조회조건으로 반환되는 서브쿼리다.
  + 다중열 서브쿼리 형식
  ```sql
    select column, column, ....
    from table1 
    where (column1, column2) in (select column1, column2 
                                 from table2)
  ```
- having절에서 서브쿼리 사용하기 
  + group by 절을 사용해서 그룹화하고 그룹함수를 실행한 결과를 필터링하는 having 절에도 서브쿼리를 사용할 수 있다.
  + 사용예
  ```sql
    select column, 그룹함수
    from table1
    group by column
    having 그룹함수 연산자 (select column
                            from table)
  ```
- 상호연관 서브쿼리
  + 서브쿼리가 메인쿼리문에서 사용(참조)되는 컬럼을 참조할 때 상호연관 서브쿼리가 된다.
  +  상호연관 서브쿼리는 메인쿼리문에서 처리되는 각 행에 대해서 한번씩 실행된다. 
  + 형식
  ```sql
    select outer.column1, outer.column2, ...
    from table1 outer
    where column 연산자 (select column1
                         from table2
                         where column = outer.column3)
    -- 서브쿼리에서 메인쿼리에서 사용되는 테이블의 컬럼을 참조한다.
    -- 서브쿼리에서는 메인쿼리의 테이블의 별칭을 사용해서 메인쿼리에서 사용되는 테이블의 컬럼을 참조한다.
  ```
  + 예제
    * 교수테이블에서 해당 직급의 평균급여보다 급여를 많이 받는 교수의 정보를 조회하기
    ```sql
      select A.profno, A.name, A.position, A.pay
      from professor A 
      where A.pay > (select avg(B.pay)
                     from professor B
                     where B.position = A.position);
    ```
    * 교수테이블에서 교수정보를 조회하기, 교수번호, 교수이름, 직급, 해당직급의 평균급여 정보를 조회하기
    ```sql
      select A.profno, A.name, A.position, A.pay, 
             (select avg(B.pay) from professor B where B.position = A.position) position_avg_pay
      from professor A;
    ```
    * 교수테이블에서 교수정보를 조회하기. 교수번호, 교수이름, 직급, 해당교수가 지도하는 학생숫자를 조회하기
    ```sql
      select A.profno, A.name, A.position, 
             (select count(*) from student B where B.profno = A.profno) student_cnt
      from professor A;
    ```
- 스칼라 서브쿼리
  + 하나의 행에서 하나의 값만 반환하는 서브쿼리다.
    * 다중행 X, 다중열 X, 단일행-단일열 O
  + 스칼라 서브쿼리는 select절, insert문의 values에서 사용할 수 있다.
  + 스칼라 서브쿼리는 decode 및, case의 조건 및 표현식에서 사용할 수 있다.
  ```sql
    select col1, col2, (select col3 from table2 where 조건식)
    from table1;
  ```
  ```sql
    insert into table1 
    (col1, col2, col3, ...)
    values
    (값, 값, (select col4 from table2 where 조건식));
  ```













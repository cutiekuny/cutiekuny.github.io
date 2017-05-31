---
layout: post
title:  "SQL 실습 day 1"
date:   2017-5-31
---
-- 계정 잠금 해제
-- 해당 라인만 출력하려면 ctrl+enter, F5는 사용하지 말것
ALTER USER SCOTT ACCOUNT UNLOCK;
ALTER USER SCOTT IDENTIFIED BY oracle;

ALIAS를 쓸때 가독성 측면에서 주로 AS를 씀.. 쌍따옴표 써야할 때는 공백, 특문, 대소 구분시에 사용

* 중간문제
--ALIAS주기
SELECT DEPTNO AS "부서#", DNAME AS "부서명", LOC AS "위치" FROM DEPT;
--부서별로 담당 업무가 하나씩 출력되도록
SELECT DISTINCT DEPTNO, JOB FROM EMP;

--' '안에는 대소문자 구분함. 그래서 initcap함수를 이용해 대소문자 상관없이 찾을 수 있다. ALIAS쓸때만 " "쓰는것임. 그 외에는 ' '.
--initcap으로 camelCase 변환하여 적용
SELECT EMPNO, ENAME, JOB, SAL, DEPTNO FROM EMP WHERE JOB = 'Manager' or initcap(JOB) = 'Manager';

-- _와 %의 차이는? %는 무엇이 와도 괜찮지만 자릿수를 제한하지 않고, _는 자릿수를 제한한다.

--오렌지나 sqldeveloper같은 툴을 쓰다보면 원격 db와 툴의 날짜 형식이 서로
 달라 sql문 작성할때 에러 발생 소지가 있음. 이럴 땐 tochar함수를 이용하면 댐


--날짜도 비교가 됌
SELECT EMPNO,
       ENAME,
       JOB,
       SAL,
       HIREDATE,
       DEPTNO
  FROM EMP
 WHERE HIREDATE > '1982/01/01';

-- NULL * 3 = NULL.
-- NOT IN을 쓰면 전체에서 IN 조건들의 값들을 뺀 나머지임. LIKE도 같음.
SELECT *
  FROM EMP
 WHERE SAL NOT IN(1600,
               1250,
               1500);

-- S<T이지만 S < SS 인 것도 알고 있어야함. 그래서 S로 시작하는 놈들만 뽑고싶으면 뭐 이런식으로
SELECT *
  FROM EMP
 WHERE ENAME > 'S'
   AND ENAME <'T';

-- 성이 ㅇ으로 시작하는 거.
SELECT *
  FROM STUDENT
 WHERE NAME < '자' AND NAME > '아' ;

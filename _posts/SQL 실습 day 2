---
layout: post
title:  "SQL 실습 day 2"
date:   2017-5-31
---

 --SELECT 절에서 가장 나중에 실행되는 게 ORDER BY이므로 
--ORDER BY는 ALIAS로 사용 가능
--ORDER BY가 2개면 뒤의 조건은 앞에 조건 중 동등한 조건이 있을때 사용
SELECT ENAME AS "이름",
       SAL AS "연봉"
  FROM EMP
 WHERE SAL > 2000
 ORDER BY 연봉 DESC,
       이름 ASC;

* 함수
--단일형 함수는 매개변수가 1개, 복수형 함수는 매개변수가 여러개(즉, GROUP BY와 함께 사용)

INITCAP 함수는 전체 글자가 소문자든 대문자든 상관안하고, 공백기준 첫번째 글자만 CAP만들어줌 나머진 소문자로 변경. 
LOWER는 모두 소문자로, UPPER는 모두 대문자로 변경

--2017-05-18 -는 뒤에서부터 카운트하겠다.. 첫번째 인자 크기보다 두번째 인자 크기가 커도 정상출력.
SELECT SUBSTR(SYSDATE, 1, 4)||'년 '||SUBSTR(SYSDATE, 6, 2)||'월 '||SUBSTR(SYSDATE, -2, 3)||'일' AS RESULT
  FROM DUAL;
 
-- SUBSTR return값이 문자이므로 비교할때 데이터 타입 맞춰주기 (퍼포먼스 이슈)
SELECT *
  FROM EMP
 WHERE SUBSTR(HIREDATE, -5, 2) = '02';
 
-- INSTR() ? return 위치(숫자) : return 0,  
SELECT *
  FROM EMP
 WHERE INSTR(ENAME, 'I', 1, 1) = 3;

-- LPAD(컬럼명, 자리수, 채울문자?생략가능!) LEFT PADDING. 왼쪽에 빈 공간만큼 문자로 채움
-- LTRIM(컬럼명, 지울문자?생략가능!) LEFT TRIM. 왼쪽에 해당문자있으면 없어질 때까지 지움. RTRIM도 있음.
-- REPLACE(컬럼명, 문자, 바꿀문자)
-- TRANSLATE(컬럼명, 단어, 바꿀단어) 둘의 차이는 문자로 검색하느냐 단어로 검색하느냐의 단위 차이. 12 = ABC로 보느냐 1=A, 2=B 로 보느냐의 차이.
SELECT RPAD(REPLACE(JUMIN, SUBSTR(JUMIN, 7), ''), LENGTH(JUMIN), '*')
  FROM STUDENT;

--MOD, FLOOR(바닥값), CEIL(천장값), ABS(절대값), SIGN(부호 확인.1:0:-1) ㅇㅇ
SELECT HIREDATE,
       SYSDATE ,
       MONTHS_BETWEEN(SYSDATE, HIREDATE)
  FROM EMP;
 
SELECT HIREDATE,
       ADD_MONTHS(HIREDATE, 6) AS "보너스날짜"
  FROM EMP;
 
-- 1:일 ~ 7:토
SELECT NEXT_DAY(SYSDATE, 7)
  FROM DUAL;
 
-- 해당 월의 마지막 날짜 RETURN
SELECT LAST_DAY(SYSDATE)
  FROM DUAL;
 
--헷갈리지 말기
SELECT SYSDATE,
       ROUND(SYSDATE, 'MONTH'),
       ROUND(SYSDATE, 'YEAR'),
       ROUND(SYSDATE)
  FROM DUAL;

-- 숫자 TO_CHAR : 9는 자리수, 0은 패딩, 소수점, 천단위, 특문도 가능
-- 날짜 TO_CHAR : YYYY(RRRR), MM, DD, Q(분기), W(주수),
SELECT SYSDATE,
       TO_CHAR(SYSDATE, 'YY'),
       TO_CHAR(SYSDATE, 'Q'),
       TO_CHAR(SYSDATE, 'W'),
       TO_CHAR(SYSDATE, 'yymmdd, DAY')
  FROM DUAL;
 ALTER SESSION 
   SET NLS_DATE_LANGUAGE='AMERICAN';
 
-- 성능에 유리하게 하려면 컬럼에 함수는 씌우지 않는편으로
SELECT *
  FROM EMP
 WHERE TO_CHAR(HIREDATE, 'MM/DD/YYYY') = '11/17/1981'
   AND HIREDATE = TO_DATE('11/17/1981', 'MM/DD/YYYY');
 SELECT TO_DATE('11/10/10', 'YY/MM/DD')
  FROM DUAL;
 DESC STUDENT;

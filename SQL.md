# 자릿수 ROUND(), TRUNCATE(), CEIL(), FLOOR(), GREATEST(), LEAST()

## ROUND()
- `ROUND(숫자, 반올림할 자릿수)` : 숫자를 반올림할 자릿수 +1 자릿수에서 반올림
```
SELECT ROUND(3456.1234567) FROM DUAL;
>>> 3456

SELECT ROUND(3456.1234567, 1) FROM DUAL;
>>> 3456.1

SELECT ROUND(3456.1234567, 4) FROM DUAL;
>>> 3456.1235

SELECT ROUND(3456.1234567, -1) FROM DUAL;
>>> 3460

SELECT ROUND(3456.1234567, -2) FROM DUAL;
>>> 3500
```

## TRUNCCATE()
- `TRUNCATE(숫자, 버릴 자릿수)` : 숫자를 버릴 자릿수 아래로 버림 (반드시 버릴 자릿수를 명시해야함)
```
SELECT TRUNCATE(3456.1234567 ,1) FROM DUAL;
// 3456.1
 
SELECT TRUNCATE(3456.1234567 ,4) FROM DUAL;
// 3456.1234
 
SELECT TRUNCATE(3456.1234567 ,-1) FROM DUAL;
// 3450
 
SELECT TRUNCATE(3456.1234567 ,-2) FROM DUAL;
// 3400 
```

## CEIL() == CEILING()
- `CEIL(올림하고자 하는 소수)` : 입력받을 수를 올림한 수가 나온다.
```
SELECT CEIL(0.8);
>>> 1
``` 

## FLOOR()
- `FLOOR(숫자)`: 값보다 작은 정수 중 가장 큰 정수를 구한다. 소수점 이하 버림을 의미한다.
```
SELECT FLOOR(12.11);
>>> 12

SELECT FLOOR(-19.1);
>>> -20
```

## GREATEST()
- `GREATEST(숫자1, 숫자2,....)` : 주어진 숫자 중에 가장 큰 값을 반환한다.
```
SELECT greatest(10, 4, 20 , 1);
>>> 20
```

## LEAST()
- `LEAST(숫자1, 숫자2, ...)` : 주어진 숫자 중에 가장 작은 값을 반환한다.
```
SELECT least(10, 4, 20 , 1);
>>> 1
```

# REGEXP
- `REGEXP`는 `LIKE`를 이용한 검색과 달리 `Regular Expression(정규 표현식)`를 이용해 검색한다.

## :question: Regular Expression(정규 표현식)이란?
- 정규 표현식은 특정한 규칙을 가진 문자열을 집합을 표현하는데 사용하는 형식 언어이다.
- 문자열을 처리하는 방법 중 하나로 `특정한 조건의 문자`를 `검색`하거나 `치환`하는 과정을 매우 간단하게 처리할 수 있도록 해주는 수단.

## REGEXP 사용 예제
```
>> '길' 또는 '로' 또는 '그'가 포함된 문자열을 찾고 싶을 때

# 정규표현식을 사용하지 않을 때
SELECT *
FROM tbl
WHERE data like '%길%' OR data like '%로%' OR data like '%그%'

# 정규표현식
SELECT *
FROM tbl
WHERE data REGEXP '길|로|그'

>> ‘안녕’ 또는 ‘하이’로 시작하는 문자열을 찾고 싶을 때

# 정규표현식을 사용하지 않을 때 
SELECT *
FROM tbl  
WHERE data LIKE '안녕%' OR data LIKE '하이%';

# 정규표현식을 사용할 때 
SELECT *
FROM tbl
WHERE data REGEXP ('^안녕|^하이');

>> 길이 7글자인 문자열 중 2번째 자리부터 abc를 포함하는 문자열을 찾고 싶을 때

# 정규표현식을 사용하지 않을 때
SELECT *
FROM tbl
WHERE CHAR_LENGTH(data) = 7 AND SUBSTRING(data, 2, 3) = 'abc';

# 정규표현식을 사용할 때
SELECT *
FROM tbl
WHERE data REGEXP ('^.abc...$');

```

# 문자열 자르기 SUBSTRING(), LEFT(), RIGHT()

## SUBSTRING()
- `SUBSTRING(문자열, 시작위치, 길이)`
```
SELECT SUBSTRING("WWW.Google.COM", 3);
>>> W.Google.COM

SELECT SUBSTRING("WWW.Google.COM", 3, 5);
>>> W.Goo

SELECT SUBSTRING("WWW.Google.COM" FROM 5);
>>> Google.COM

SELCT SUBSTRING("WWW.Google.COM" FROM 2 FOR 2);
>>> WW
```

## LEFT()
- `LEFT(문자열, 길이)` : 왼쪽에서부터 잘라내어 반환
```
SELECT LEFT("WWW.Google.COM", 3);
>>> WWW
```

## RIGHT()
- `RIGHT(문자열, 길이)` : 오른쪽부터 잘래니어 반환
```
SELECT RIGHT("WWW.Google.COM", 3);
>>> COM
```

## SUBSTRING_INDEX()
- `SUBSTRING_INDEX(문자열, 구분자, 구분자 INDEX)` : 구분자와 구분자 숫자만큼 잘라내어 반환
```
SELECT SUBSTRING_INDEX("010-5678-9999", "-", 2);
>>> 010-5678
```

# date_format 사용하기

## DATE_FORMATE(시간값, 원하는 포맷);
- `시간값에 원하는 컬럼, 데이터`를 넣고 원하는 포맷 칸에 원하는 `출력 형태의 포맷 문자열`을 넣는다.
- 포맷 문자열은 `대, 소문자`를 유의한다. 표기되는 결과가 달라진다.

### now()
- 현재 시스템의 시간을 출력한다.
```
SELECT now()
>>> 2023-02-21 11:23:00
```

### 날짜만 표기하기 date_format(now(), '%Y-%m-%d')
```
SELECT date_format(now(), '%Y-%m-%d')
>>> 2020-02-06
```

### 날짜+시간 표기
- %H : 시간 24시간 (00 ~ 23)
- %h : 시간 12시간 (00 ~ 12)
- %i : 분 (00 ~ 59)
- %s : 초(00~59)
```
select date_format(now(), '%Y.%m.%d %H:%i:%s')
>>> 2023.02.21 11:25:00
```

# 날짜, 시간 계산 DATEDIFF, TIMEDIFF

## DATEDIFF
- `DATEDIFF(expr, expr2)` - 두 기간 사이의 `일수 계산` (expr : 종료일, expr2 : 시작일)
```
SELECT DATEDIFF('2021-12-31','2021-01-20');
>>> 345
SELECT DATEDIFF('2021-12-31','2022-01-20');
>>> -20
SELECT DATEDIFF('2021-12-31', CURRENT_DATE()); # CURRENT_DATE() : 현재 날짜 조회
>>> -7
```

## TIMEDIFF
- `TIMEDIFF(expr, expr2)` : 두 기간 사이의 `시간을 계산`한다. (expr : 종료시간, expr2 : 시작 시간)
```
SELECT TIMEDIFF('2022-02-01 23:00:00','2022-01-30 00:00:00');
>>> 71:00:00
SELECT TIMEDIFF('2021-12-31 23:00:00','2022-01-01 00:00:00.000000');
>>> -01:00:00.000000
SELECT TIMEDIFF('2022-01-02 00:00:00',CURRENT_TIMESTAMP());
>>> -135:51:10
SELECT TIMEDIFF('11:30:00','00:00:00');
>>> 11:30:00
```

## PERIOD_DIFF
- `PERIOD_DIFF(P1, P2)` : 두 기간 사이의 `개월 수 차이`를 계산 (P1 : 시작년월, P2 : 종료년월)
```
SELECT PERIOD_DIFF('202202','202112');
>>> 2
SELECT PERIOD_DIFF('202202','201212');
>>> -10
SELECT PERIOD_DIFF('2202','1912');
>>> 26
```

## TIMESTAMPDIFF
- `TIMESTAMPDIFF(unit, datetime_expr1, datetime_expr2)` : 시간 또는 개월 수 등 여러 가지 형태의 계산을 할 수 있는 함수 (unit : 반환 값 형식, datetime_exp1 : 시작일, datetime_expr2 : 종료일)
```
SELECT TIMESTAMPDIFF(MONTH,'2021-02-01','2022-03-01');
>>> 13
SELECT TIMESTAMPDIFF(YEAR,'2021-02-01','2022-03-01');
>>> 1
SELECT TIMESTAMPDIFF(HOUR,'2022-02-01','2022-02-03');
>>> 48
```

# NULL값 처리 IFNULL, CASE, COALESCE

## IFNULL
- `SELECT IFNULL(Column명, "Null일 경우 대체 값") FROM 테이블명;` : NULL을 반환할 때, 다른 값으로 출력한다.
```
>> NAME Column이 NULL인 경우 "No name"을 출력, NULL이 아닌 경우 NAME Column을 출력

SELECT IFNULL(NAME, "No name") as NAME
FROM ANIMAL_INS
```

### IF()
- NULL처리는 `IF`함수와 `IS NULL` 조건으로도 가능하다.
```
>>NAME Column이 NULL이 True인 경우 "No name"을, False인 경우는 NAME Column을 출력

SELECT IF(IS NULL(NAME), "No name", NAME) as NAME
FROM ANIMAL_INS
```

## CASE
```
CASE 
    WHEN 조건식1 THEN 식1
    WHEN 조건식2 THEN 식2
    ...
    ELSE 조건에 맞는경우가 없는 경우 실행할 식
END
```
- column 값을 조건식을 통해 True, False를 판단하여 조건에 맞게 column값을 변환한다.
```
>> NAME Column의 IS NULL 조건이 True인 경우 "No name" 출력
>> WHEN 조건들에 True인 조건이 없을 경우 ELSE 문을 통해 NAME Column의 값 출력
>> END 이후 그 Column의 별칭을 NAME으로 지정

SELECT 
    CASE
        WHEN NAME IS NULL THEN "No name"
        ELSE NAME
    END as NAME
FROM ANIMAL_INS
```

## COALESCE
```
>> NULL 처리 상황

SELECT COALESCE(Column명1, Column명1이 NULL인 경우 대체할 값)
FROM 테이블명


>> 배타적 OR 관계 열
>> Column1 ~ 4 중 NULL이 아닌 첫 번째 Column을 출력

SELECT COALESCE(Column명1, Column명2, Column명3, Column명4)
FROM 테이블명
```
- 지정한 표현식들 중에 NULL이 아닌 첫 번째 값을 반환한다.
- 표현식은 여러 항목 지정이 가능하고, 처음으로 만나는 NULL이 아닌 값을 출력한다.
- 표현식이 모두 NULL일 경우엔 결과도 NULL 반환
- `COALESCE`은 배타적 OR 관계 열에서 활용도가 높다.
- 테이블에서 두 개 이상의 속성(열) 중 하나의 값만 가지는 데이터일 경우
```
>> NAME Column의 값이 NULL인 경우 다음 표현식으로 넘어간다.
>> 다음 표현식인 "No name"이 Null이 아니므로 "No name"을 출력.

SELECT COALESCE(NAME, "No name")
FROM ANIMAL_INS
```

# DATE FUNCTION (날짜 관련 함수)

## DAYOFWEEK(DATE)
- 날짜를 한 주의 몇 번째 요일인지 나타내는 숫자로 리턴한다.
- (1 = 일요일, 2 = 월요일, ... 7 = 토요일)
```
SELECT DAYOFWEEK('1998-02-03')
>>> 3
```

## DATE_FORMAT(date, format)
- format의 정의에 따라 날짜 혹은 시간을 출력한다

### format에 사용되는 문자
    - %m : 월이름(january...december)
    - %w : 요일명
    - %y : 4자리 년도
    - %a : 짧은 요일명(sun..sat)
    - %d : 일(00 .... 31)
    - %h : 12시 형식의 시간(01...12)

## CURDATE()
- 함수가 문자열이나 숫자로 사용되었는지 문맥에 따라서 'YYYY-MM-DD'이나 YYYYMMDD 형식으로 현재 날짜를 반환한다.
```
SELECT CURDATE();
>> '2023-02-15'

SELECT CURDATE() + 0;
>> 20230215
```

## CURTIME()
- 함수가 문자열이나 숫자로 사용되었는지 문맥에 따라서 'HH:MM:SS'이나 HHMMSS 형식으로 현재 시간을 반환한다.
```
SELECT CURTIME();
>>'23:20:14'

SELECT CURTIME() + 0;
>>232014
```

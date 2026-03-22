# SQL_ADVANCED 3주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_3st_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=1YmWy-7-OhQ&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=10
https://www.youtube.com/watch?v=tuQFkzjqEGw&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=11
https://www.youtube.com/watch?v=IOCsreDYqFE&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=12
-->

**교재 실습 예제 파일은 07_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_3st_TIL

### 4장 SQL 고급 문법
#### 01. MySQL의 데이터 형식
#### 02. 두 테이블을 묶는 조인
#### 03. SQL 프로그래밍 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | ✅         |
| 4주차 | p.216~271 | 🍽️         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. MySQL의 데이터 형식

```
1. 정수형
1) TINYINT : 1바이트, -128 ~ 127
2) SMALLINT : 2바이트, -32,768 ~ 32,767
3) INT : 4바이트, 약 -21억 ~ + 21억
4) BIGINT : 8바이트, 약 -900경 ~ +900경
-> UNSIGNED : 범위가 0부터 지정

2. 문자형
1) CHAR(개수) : 1 ~ 255바이트
2) VARCHAR(개수) : 1 ~ 16383바이트
3) TEXT
(1) TEXT : 1 ~ 65535바이트
(2) LONGTEXT : 1 ~ 42949672975바이트
4) BLOB
(1) BLOB : 1 ~ 65535바이트
(2) LONGBLOB : 1 ~ 42949672975바이트

3. 실수형
1) FLOAT : 4바이트, 소수점 아래 7자리까지 표현
2) DOUBLE : 8바이트, 소수점 아래 15자리까지 표현

4. 날짜형
1) DATE : 3바이트, 날짜만 저장, YYYY-MM-DD 형식
2) TIME : 3바이트, 시간만 저장, HH:MM:SS 형식
3) DATETIME : 8바이트, 날짜 및 시간 저장, YYYY0MM0DD HH:MM:SS 형식

5. 변수의 선언 및 값 대입
SET @변수이름 = 변수의 값; -> 변수 선언 및 값 대입
SELECT @ 변수이름; -> 변수의 값 출력

6. 데이터 형 변환
1) 명시적 변환 : 직접 함수 사용해 변환
(1) CAST (값 AS 데이터_형식 [(길이)])
(2) CONVERT (값, 데이터_형식[(길이)])
2) 암시적 변환 : 별도의 지시 없이 자연스럽게 변환 
```

> **확인문제: 다음 보기에서 데이터 형식의 변환에 사용되는 함수를 2개 고르세요.**

보기는 아래와 같습니다.
```
CONVERT() / DATA() / CAST() / MOVE() / TYPE() / SUM() / AVG() / CURRENT_DATE()
```

```
CAST(), CONVERT()
```


## 2. 두 테이블을 묶는 조인

<!-- 두 테이블을 묶는 조인에 관해 배우게 된 점을 적어주세요. -->
```
1. 조인
: 두 개의 테이블을 서로 묶어서 하나의 결과를 만들어 내는 것

2. 일대다 관계
: 한쪽 테이블에는 하나의 값만 존재해야 하지만, 연결된 다른 테이블에는 여러 개의 값이 존재할 수 있는 관계
-> 조인을 위해서는 테이블이 일대다 관계로 연결되어야 함

3. 내부 조인
SELECT <열 목록>
FROM <첫 번째 테이블>
  INNER JOIN <두 번째 테이블>
  ON <조인될 조건>
[WHERE 검색 조건]

4. 외부 조인
: 두 테이블 조인 시 필요한 내용이 한쪽 테이블에만 있어도 결과 추출 가능
SELECT <열 목록>
FROM <첫 번째 테이블(LEFT 테이블)>
  <LEFT | RIGHT | FULL> OUTER JOIN <두 번째 테이블(RIGHT 테이블)>
  ON <조인될 조건>
[WHERE 검색 조건];

5. 기타 조인
1) 상호 조인 : 한쪽 테이블의 모든 행과 다른 쪽 테이블의 모든 행을 조인시키는 기능
-> 카티션 곱이라고도 부름
2) 자체 조인 : 자기 자신과 조인
SELECT <열 목록>
FROM <테이블> 별칭A
  INNER JOIN <테이블> 별칭B
  ON <조인될 조건>
[WHERE 검색 조건]
```

> **확인문제: 다음 SQL은 회원으로 가입만 하고, 한 번도 구매한 적이 없는 회원의 목록을 조회하는 쿼리입니다. 빈칸에 들어갈 가장 적절한 구문을 고르세요..**

```sql
SELECT DISTINCT M.mem_id, B.prod_name, M.mem_name, M.addr
  FROM member M
    LEFT OUTER JOIN buy B
    ON M.mem_id = B.mem_id
  __________
  ORDER BY M.mem_id;
```
보기는 아래와 같습니다.
```
1. JOIN B.prod_name IS NULL
2. LIMIT B.prod_name IS NULL
3. HAVING B.prod_name IS NULL
4. WHERE B.prod_name IS NULL
```
```
4. 한 번도 구매하지 않았으므로 물건 이름이 비어있을 것임. 
```

## 3. SQL 프로그래밍 

<!-- IF문, CASE문, WHILE문, 동적 SQL에 관해 배우게 된 점을 적어주세요. -->

```
1. IF문
IF <조건식> THEN
  SQL문장들
END IF;
-> SQL 문장이 여러 개면 BEGIN ~ END로 묶기

2. IF ~ ELSE문
: 조건식이 참이면 SQL문장들1을, 아니면 SQL문장들2를 실행

3. CASE문
CASE
  WHEN 조건1 THEN
    SQL문장들1
  WHEN 조건2 THEN
    SQL문장들2
  WHEN 조건3 THEN
    SQL문장들3
  ELSE
    SQL문장들4
END CASE;

4. WHILE문
WHILE <조건식> DO
  SQL 문장들
END WHILE;

5. WHILE문의 응용
1) ITERATE[레이블] : 지정한 레이블로 가서 계속 진행
2) LEAVE[레이블] : 지정한 레이블을 빠져나감. 즉 WHILE문이 종료됨.

6. 동적 SQL
1) PREPARE : SQL문을 실행하지 않고 미리 준비함
2) EXCUTE : 준비한 SQL문을 실행함 -> 실행 후에는 DEALLOCATE PREPARE로 문장 해제 필요
```

> **확인문제: 다음은 CASE 문의 형식입니다. 빈칸에 들어갈 가장 적절한 명령어를 보기에서 고르세요..**

```sql
CASE
    (1) 조건 THEN
        SQL문장들1
    ELSE
        SQL문장들4
END (2);
```

보기는 아래와 같습니다.
```
WHEN / THEN / CURRENT / DATE / TIME / IF / END IF / CASE
```

```
여기에 답을 적어주세요!
(1) WHEN
(2) CASE
```

![Image](https://github.com/user-attachments/assets/f3ad1d2c-b0f2-4eb9-82a9-746583e757c1)

![Image](https://github.com/user-attachments/assets/70ddd77f-f197-4c2d-8383-27698c1754c4)

![Image](https://github.com/user-attachments/assets/97baf62c-1f8a-4f50-b5fd-c7cf7fb4f32e)

---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + shift + Enter)** 하여 데이터베이스를 구축하세요.

```sql
-- 1. 데이터베이스 생성
CREATE DATABASE IF NOT EXISTS week3_db;

-- 2. 사용할 데이터베이스 선택
USE week3_db;

-- 3. 기존 테이블 삭제 (초기화용)
DROP TABLE IF EXISTS orders;
DROP TABLE IF EXISTS customers;

-- 4. 테이블 생성 (조인 실습용)
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(20),
    signup_date_str VARCHAR(8) 
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,           
    order_date_str VARCHAR(8), 
    amount_str VARCHAR(10)     
);

-- 5. 데이터 삽입
INSERT INTO customers VALUES
(1, '진아', '20240218'),
(2, '혜인', '20230302'),
(3, '규서', '20220315'),
(4, '규영', '20210401'),
(5, '철원', '20230909'),
(6, '예운', '20240201'),
(7, '민서', '20220320'),
(8, '광윤', '20240105'); -- 주문 없는 고객(외부 조인용)

INSERT INTO orders VALUES
(101, 1, '20240220', '12000'),
(102, 1, '20240303', '30000'),
(103, 2, '20240111', '15000'),
(104, 3, '20221201', '9000'),
(105, 5, '20231111', '20000'),
(106, 7, '20220707', '5000'),
(107, 99, '20240210', '7000'); -- 고객 테이블에 없는 customer_id (외부 조인용)
```

## 2. 실습 문제

다음 SQL 문을 작성하고 실행 결과를 확인 후 인증 사진을 아래에 업로드하세요.

1. **데이터 형식 변환**
   - orders 테이블의 `order_date_str`을 DATE 형식으로 변환하여 조회하시오.
   (힌트: STR_TO_DATE 사용)

2. **데이터 형식 변환**
   - orders 테이블의 `amount_str`을 숫자형으로 변환하여 조회하시오.

3. **내부 조인 (INNER JOIN)**
   - customers와 orders를 customer_id 기준으로 내부 조인하여
     고객 이름(name)과 주문 번호(order_id)를 함께 조회하시오.

4. **외부 조인 (LEFT JOIN)**
   - customers를 기준으로 LEFT JOIN을 수행하여,
     주문이 없는 고객도 함께 조회하시오.

5. **스토어드 프로시저 (IF문 사용)**
   - 입력받은 금액이 10000 이상이면 '고액 주문',
     그렇지 않으면 '일반 주문'을 출력하는
     프로시저를 생성하시오.
   - 생성 후 CALL로 실행 결과를 확인하시오.


![Image](https://github.com/user-attachments/assets/e2f19000-c162-4903-9e26-30e1936ef8ea)


### 🎉 수고하셨습니다.








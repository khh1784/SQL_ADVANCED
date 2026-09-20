# SQL_ADVANCED 3주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_3rd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=1YmWy-7-OhQ&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=10
https://www.youtube.com/watch?v=tuQFkzjqEGw&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=11
https://www.youtube.com/watch?v=IOCsreDYqFE&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=12
-->

**교재 실습 예제 파일은 08_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_3rd_TIL

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
- 정수형: TINYINT(1바이트), SMALLINT(2바이트), INT(4바이트), BIGINT(8바이트)
          UNSIGNED 속성을 추가하면 음수 범위 대신 0부터 시작하는 양수 범위로 확장 가능.
- 문자형
  1. CHAR(n): 고정길이 문자형으로 자릿수가 정해진 데이터(예: 전화번호 국번, 주소 코드)에 효율적
  2. VARCHAR(n): 가변길이 문자형으로 자릿수가 일정하지 않은 텍스트에 사용하여 공간을 절약
- 대량 데이터 형식: TEXT/LONGTEXT(자막, 소설 등 대용량 글자) 및 BLOB/LONGBLOB(이미지, 동영상 등 이진 파일)을 사용
- 날짜/시간형: DATE(YYYY-MM-DD), TIME(HH:MM:SS), DATETIME(날짜와 시간 모두 포함)
- 형변환 함수:
  1. CAST(값 AS 데이터형식) / CONVERT(값, 데이터형식): 명시적으로 데이터 타입을 변환
  2. STR_TO_DATE(문자열, 포맷): 문자열을 날짜 형식으로 변환
     
<img width="959" height="505" alt="image" src="https://github.com/user-attachments/assets/2f6ee939-1372-4ae4-8326-a1a32cf52c39" />

> **확인문제: 다음 보기에서 데이터 형식의 변환에 사용되는 함수를 2개 고르세요.**

보기는 아래와 같습니다.
```
CONVERT() / DATA() / CAST() / MOVE() / TYPE() / SUM() / AVG() / CURRENT_DATE()
```

```
CAST(), CONVERT()
```


## 2. 두 테이블을 묶는 조인

- 내부 조인 (INNER JOIN): 두 테이블에 모두 존재하는 일치 행만 결합하여 조회(가장 많이 사용)
- 외부 조인 (OUTER JOIN): 한쪽에만 데이터가 존재하더라도 결과를 출력
   1. LEFT OUTER JOIN: 왼쪽 테이블의 모든 행을 기준으로 출력
   2. RIGHT OUTER JOIN: 오른쪽 테이블의 모든 행을 기준으로 출력
- 상호 조인 (CROSS JOIN): 한쪽 테이블의 모든 행과 다른 쪽 테이블의 모든 행을 조인하는 카티션 곱(Cartesian Product)
- 자체 조인 (SELF JOIN): 하나의 테이블이 자기 자신과 조인하는 형태

<img width="959" height="502" alt="image" src="https://github.com/user-attachments/assets/7600c4ac-b01a-4b5c-a171-63c3b58debc3" />

<img width="959" height="503" alt="image" src="https://github.com/user-attachments/assets/bc7b2846-1b30-42d6-bf6a-f2a637a66dc4" />

<img width="959" height="506" alt="image" src="https://github.com/user-attachments/assets/6244a439-34da-4aa9-8857-ab0344dcd677" />

<img width="959" height="505" alt="image" src="https://github.com/user-attachments/assets/603cfd4c-fadd-499f-96d6-459920b9fb80" />

<img width="959" height="505" alt="image" src="https://github.com/user-attachments/assets/e7e69ad3-c4ea-4669-9d49-57e775e44a24" />

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
4. WHERE B.prod_name IS NULL
조인된 전체 결과 데이터 중 한 번도 구매한 적이 없는 회원만 필터링하기 위해서는 WHERE 조건절에서 IS NULL 연산자를 사용하여 물품명(B.prod_name)이 NULL인 행만 걸러야 함.
```

## 3. SQL 프로그래밍 

<!-- IF문, CASE문, WHILE문에 관해 배우게 된 점을 적어주세요. -->
- IF문
  : 조건식이 참(True)인지 거짓(False)인지에 따라 실행할 SQL 문장을 분기하는 가장 대표적인 조건문
  
```sql
IF <조건식> THEN
    SQL문장1; -- 조건식이 참(True)일 때 실행
ELSE
    SQL문장2; -- 조건식이 거짓(False)일 때 실행
END IF;
```

특징
1. 참/거짓 두 가지 경우로 나누어 로직을 처리할 때 적합
2. 조건에 맞춰 실행할 SQL 문장이 여러 개일 경우 BEGIN ~ END 블록으로 묶어 작성하는 것을 권장

- CASE 문 (다중 조건문)
  : 조건이 여러 개이거나 다양한 범주의 결과를 반환해야 할 때 사용

```sql
CASE
    WHEN 조건1 THEN
        SQL문장1;
    WHEN 조건2 THEN
        SQL문장2;
    ELSE
        SQL문장3; -- 위의 조건에 모두 해당하지 않을 때 실행
END CASE;
```

특징 : 스토어드 프로시저 내부 제어문뿐만 아니라, SELECT문 안에서 데이터 값을 기준별로 분류하여 새로운 열로 출력할 때도 널리 활용

- WHILE 문
  : 조건식이 참(True)인 동안 지정한 SQL 문장들을 계속해서 반복 실행
  
```sql
WHILE <조건식> DO
    SQL문장들; -- 조건식이 참인 동안 반복 실행
END WHILE;
```

반복 제어 키워드:
1. ITERATE [레이블이름]: 지정한 레이블 위치로 이동하여 다음 반복을 계속 수행 (다른 언어의 continue와 동일)
2. LEAVE [레이블이름]: 반복문을 즉시 탈출하여 종료(다른 언어의 break와 동일)
   
   
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
(1, '신영', '20241528'),
(2, '경모', '20220261'),
(3, '세원', '20203401'),
(4, '진우', '20221024'),
(5, '성환', '20225100'),
(6, '혜준', '20244946'),
(7, '채은', '20250412'),
(8, '다나', '20212774'); -- 주문 없는 고객(외부 조인용)

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
```sql
SELECT order_id, STR_TO_DATE(order_date_str, '%Y%m%d') AS order_date
FROM orders;
```
<img width="959" height="504" alt="image" src="https://github.com/user-attachments/assets/3f90dce6-6081-40d2-9587-e8bdf957183f" />

2. **데이터 형식 변환**
   - orders 테이블의 `amount_str`을 숫자형으로 변환하여 조회하시오.
```sql
SELECT order_id, CAST(amount_str AS UNSIGNED) AS amount
FROM orders;
```
<img width="959" height="504" alt="image" src="https://github.com/user-attachments/assets/c2218fcd-f4c7-4e0c-95d8-9a49643c3ab3" />


3. **내부 조인 (INNER JOIN)**
   - customers와 orders를 customer_id 기준으로 내부 조인하여
     고객 이름(name)과 주문 번호(order_id)를 함께 조회하시오.
```sql
SELECT C.name, O.order_id
FROM customers C
INNER JOIN orders O
    ON C.customer_id = O.customer_id;
```
<img width="959" height="506" alt="image" src="https://github.com/user-attachments/assets/d025c452-3cc8-4c9e-abcb-65ec1ca67c7c" />


4. **외부 조인 (LEFT JOIN)**
   - customers를 기준으로 LEFT JOIN을 수행하여,
     주문이 없는 고객도 함께 조회하시오.
```sql
SELECT C.customer_id, C.name, O.order_id, O.order_date_str, O.amount_str
FROM customers C
LEFT JOIN orders O
    ON C.customer_id = O.customer_id;
```
<img width="959" height="503" alt="image" src="https://github.com/user-attachments/assets/199902e0-4000-4df2-bbbe-d4b6ec010f00" />


5. **스토어드 프로시저 (IF문 사용)**
   - 입력받은 금액이 10000 이상이면 '고액 주문',
     그렇지 않으면 '일반 주문'을 출력하는
     프로시저를 생성하시오.
   - 생성 후 CALL로 실행 결과를 확인하시오.
```sql
-- 기존 프로시저가 있다면 삭제
DROP PROCEDURE IF EXISTS check_order_proc;

-- 프로시저 생성
DELIMITER $$
CREATE PROCEDURE check_order_proc(
    IN input_amount INT
)
BEGIN
    IF input_amount >= 10000 THEN
        SELECT '고액 주문' AS "주문 유형";
    ELSE
        SELECT '일반 주문' AS "주문 유형";
    END IF;
END $$
DELIMITER ;

-- 실행 확인 (CALL)
CALL check_order_proc(15000); -- 결과: '고액 주문'
CALL check_order_proc(5000);  -- 결과: '일반 주문'
```
<img width="959" height="503" alt="image" src="https://github.com/user-attachments/assets/1573d79f-8ef9-4c35-b923-8ae395fac1a2" />
<img width="959" height="505" alt="image" src="https://github.com/user-attachments/assets/5a3c2a05-9218-4278-9b08-d36eb3cc829b" />





### 🎉 수고하셨습니다.








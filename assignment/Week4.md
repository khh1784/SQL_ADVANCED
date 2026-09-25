# SQL_ADVANCED 4주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_4th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=DMNpkj_bZIs&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=13
https://www.youtube.com/watch?v=BUHj-behLyc&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=14
https://www.youtube.com/watch?v=JrXWxku7ZIM&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=15
-->

**교재 실습 예제 파일은 08_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_4th_TIL

### 5장 테이블과 뷰
#### 01. 테이블 만들기
#### 02. 제약조건으로 테이블을 견고하게
#### 03. SQL 가상의 테이블: 뷰 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | ✅         |
| 4주차 | p.216~271 | ✅         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 테이블 만들기 
- 개념: 데이터베이스에서 실제 데이터가 저장되는 가장 기본이 되는 2차원 표 형태의 개체로, 행(Row)과 열(Column)로 구성
- 테이블 생성 문법 (CREATE TABLE):
  CREATE TABLE 테이블이름 (
    열이름1 데이터형식 [제약조건],
    열이름2 데이터형식 [제약조건],
    ...
  );
- 핵심 키워드:
  1. AUTO_INCREMENT: 열을 정의할 때 1부터 자동으로 증가하는 값을 입력(반드시 기본키 지정 필요)
  2. PRIMARY KEY: 각 행을 유일하게 구분하는 기본키를 설정


## 2. 제약조건으로 테이블을 견고하게 
- 개념: 데이터의 결함이 없는 상태인 '데이터 무결성'을 지키기 위해 테이블의 열에 대해 설정하는 입력 규칙
- 주요 제약조건:
  1. PRIMARY KEY (기본키): 중복되지 않는 유일한 값이며, NULL 값을 허용하지                            않음(테이블당 1개만 지정 가능)
  2. FOREIGN KEY (외래키): 두 테이블 간의 관계를 맺어 주며, 참조하는 테이블                            의 기본키에 존재하는 값만 입력 가능하도록 참조                             무결성을 유지
  3. UNIQUE (유일한 값): 중복되지 않는 유일한 값을 입력받아야 하지만, NULL                          값은 허용
  4. CHECK (값의 범위 검사): 입력되는 데이터가 지정한 조건(예: amount > 0)                             에 맞는지 검사
  5. DEFAULT (기본값 설정): 값을 입력하지 않고 생략했을 때 자동으로 들어갈                             기본값을 정의
  6. NOT NULL: 빈 값(NULL)을 허용하지 않고 반드시 데이터를 입력하도록 강제
     
> **확인문제: 다음 보기 중에서 각 문항이 설명하는 것을 고르세요.**

보기는 아래와 같습니다.
```
CHECK / DEFAULT / PRIMAY KEY / UNIQUE / NOT NULL / FOREIGN KEY
```

```
여기에 답과 그 이유를 적어주세요!
1. 입력되는 데이터가 조건에 맞는지 검사하는 기능: CHECK(이유: CHECK 제약조건은 입력되는 데이터가 미리 지정한 조건(예: 특정 범위나 양수 여부 등)을 만족하는지 검증)
2. 값을 입력하지 않으면 자동으로 들어갈 값: DEFAULT(이유: DEFAULT 제약조건은 INSERT 시 해당 열의 값을 전달하지 않았을 때 자동으로 입력될 기본값을 설정)
3. 빈 값을 입력하는 것을 허용하지 않음: NOT NULL(이유: NOT NULL 제약조건은 해당 열에 NULL 데이터가 들어오는 것을 방지하여 필수로 값이 입력되도록 강제)
```


## 3. 가상의 테이블: 뷰 
- 개념: 실제 데이터를 저장하지 않고, SELECT 문으로 정의되는 가상의 테이블
- 주요 장점 및 특징:
  1. 보안성: 원본 테이블의 중요한 개인정보나 민감한 열을 숨기고 필요한 열만              선택적으로 공개할 수 있음
  2. 복잡한 쿼리의 단순화: 자주 사용하는 복잡한 조인(JOIN) 쿼리를 뷰로 생성                           해 두면 SELECT * FROM 뷰이름으로 간편하게 재사용                          할 수 있음

> **확인문제: 다음은 뷰의 특징입니다. 거리가 먼 것을 하나 고르세요.**

보기는 아래와 같습니다.
```
1️⃣ 뷰에는 테이블의 모든 열을 포함시켜야 합니다.
2️⃣ 뷰는 복잡한 SQL을 단순하게 만드는 효과가 있습니다.
3️⃣ 뷰는 보안에 도움이 됩니다.
4️⃣ 일부 사용자가 테이블에는 접근하지 못하게 하고, 뷰에만 접근하도록 설정할 수 있습니다.
```

```
답: 1️⃣ 뷰에는 테이블의 모든 열을 포함시켜야 합니다.
이유: 뷰는 원본 테이블의 모든 열을 포함할 필요가 없으며, 필요한 일부 열만 선택적으로 추출하여 가상의 테이블을 만들 수 있는 것이 핵심 장점이자 특징

```


---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + Shift + Enter)** 하여 데이터베이스를 생성하세요.

```sql
CREATE DATABASE IF NOT EXISTS week4_db;
USE week4_db;
```
<img width="1919" height="1125" alt="image" src="https://github.com/user-attachments/assets/018381a7-2e48-4e91-a4ca-ce2c4a9855b9" />

## 2. 실습문제

1. 다음 조건을 만족하는 `users` 테이블을 생성하시오.
```
- user_id는 INT이며 **기본키(Primary Key)**로 설정합니다.
- name은 VARCHAR(20)이며 NULL을 허용하지 않습니다.
- email은 VARCHAR(50)이며 중복을 허용하지 않습니다.
- signup_date는 DATE 타입으로 설정합니다.
- grade는 INT이며 기본값(Default)을 1로 설정합니다.
```

```sql
CREATE TABLE users (
    user_id INT PRIMARY KEY,
    name VARCHAR(20) NOT NULL,
    email VARCHAR(50) UNIQUE,
    signup_date DATE,
    grade INT DEFAULT 1
);
```
<img width="1919" height="1128" alt="image" src="https://github.com/user-attachments/assets/a11a4909-d2d3-4910-9e34-03395b75bd71" />


2. 다음 조건을 만족하는 `orders` 테이블을 생성하시오.
```
- order_id는 INT이며 기본키(Primary Key)로 설정합니다.
- user_id는 INT이며 NULL을 허용하지 않습니다.
- amount는 INT이며 0보다 커야 합니다.
- order_date는 DATE 타입으로 설정합니다.
```

```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    user_id INT NOT NULL,
    amount INT CHECK (amount > 0),
    order_date DATE
);
```
<img width="1919" height="1129" alt="image" src="https://github.com/user-attachments/assets/92585894-19a3-4e44-9d33-de7f1f76141d" />


3. 다음 조건을 만족하여 데이터를 삽입하시오.
```
- users 테이블에 3명 이상의 데이터를 직접 INSERT 하시오. (단, user 중 본인이 포함돼야 함)
- orders 테이블에 3건 이상의 데이터를 직접 INSERT 하시오.
```

```sql
INSERT INTO users (user_id, name, email, signup_date, grade) VALUES
(1, '권현하', 'myemail@example.com', '2024-01-10', 1),
(2, '김철수', 'chulsoo@example.com', '2024-02-15', 2),
(3, '이영희', 'younghee@example.com', '2024-03-01', 1);
```
<img width="1918" height="1128" alt="image" src="https://github.com/user-attachments/assets/8ac58620-d222-4a12-b6a1-02eeaffb22a6" />


```sql
INSERT INTO orders (order_id, user_id, amount, order_date) VALUES
(101, 1, 15000, '2024-03-05'),
(102, 2, 30000, '2024-03-10'),
(103, 3, 50000, '2024-03-12');
```
<img width="1919" height="1123" alt="image" src="https://github.com/user-attachments/assets/8df7f7a8-1370-49fe-8b51-8f10932184c3" />


4. users와 orders 테이블을 활용하여 다음 컬럼을 보여주는 뷰 user_order_view를 생성하시오.
```
- user_id
- name
- amount
```

```sql
CREATE VIEW user_order_view AS
SELECT 
    U.user_id,
    U.name,
    O.amount
FROM users U
INNER JOIN orders O
    ON U.user_id = O.user_id;
```
<img width="1919" height="1127" alt="image" src="https://github.com/user-attachments/assets/2dd9c429-39ed-4168-a738-2270a5af3481" />


5. 생성한 user_order_view를 조회하시오.
```sql
SELECT * FROM user_order_view;
```
<img width="1919" height="1126" alt="image" src="https://github.com/user-attachments/assets/09bb1822-f7a1-46af-8f78-3c52df2aab5c" />


## 3. 제출 방법

1. 각 문제의 실행 결과가 보이도록 화면을 캡처합니다.
2. 테이블 생성 결과, 데이터 삽입 결과, 뷰 생성 및 조회 결과가 모두 보이도록 제출합니다.
  

[1]
<img width="1919" height="1128" alt="image" src="https://github.com/user-attachments/assets/52e0fed7-7b93-4930-b630-15feba299184" />

[2]
<img width="1919" height="1129" alt="image" src="https://github.com/user-attachments/assets/14493072-4a08-4d01-bba7-f2de54434831" />

[3]
<img width="1918" height="1128" alt="image" src="https://github.com/user-attachments/assets/8ac58620-d222-4a12-b6a1-02eeaffb22a6" />

<img width="1919" height="1123" alt="image" src="https://github.com/user-attachments/assets/770d76fe-7797-4ee1-8275-9fa7c4a1eb03" />

[4]
<img width="1919" height="1127" alt="image" src="https://github.com/user-attachments/assets/75253230-5cd9-4e20-a7b0-c8a4b98d605c" />

[5]
<img width="1919" height="1126" alt="image" src="https://github.com/user-attachments/assets/0064a897-a297-4f9d-8966-2826ed14555c" />




### 🎉 수고하셨습니다.








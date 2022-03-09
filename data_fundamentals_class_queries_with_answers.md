
### 3. 관계형 데이터베이스 실습 (1)

[101] Q. Customers 테이블의 모든 데이터 조회

```markdown
SELECT * FROM Customers;
```

[102] Q. Customers 테이블에서 진짜 이름만 조회

```markdown
SELECT RealName FROM Customers;
```

[103] Q. Customers 테이블에서 전체 사람 수 조회

```markdown
SELECT COUNT(RealName) FROM Customers;
```

[104] Q. Orders 테이블의 모든 데이터 조회

```markdown
SELECT * FROM Orders;

[105] Q. Orders 테이블의 주문 수량 컬럼만 조회

```markdown
SELECT OrderQuantity FROM Orders;
```

[106] Q. Orders 테이블의 주문 수량 컬럼에서, 총 주문 수량을 조회

```markdown
SELECT SUM(OrderQuantity) FROM Orders;
```

[107] Q. Orders 테이블에서 짜장면의 주문 내역만 조회

```markdown
SELECT SUM(OrderQuantity) FROM Orders WHERE ProductID=1;
```

[108] Q. 짜장면의 주문 수량은?

```markdown
SELECT SUM(OrderQuantity) FROM Orders WHERE ProductID = 1
```

[109] Q. 합치기

```markdown
SELECT *
FROM Orders
JOIN Customers ON Orders.CustomerID = Customers.CustomerID
```

[110] Q. 주문 테이블에서, 고객ID 옆에 고객 이름을 표시하고 싶다면?
- JOIN을 사용!

```markdown
SELECT Orders.CustomerID, Customers.CustomerName
FROM Orders
JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```

[111] Q. 주문 테이블에서, 고객ID 옆에 고객 이름을 표시하고 싶다면?
- JOIN을 사용! { 좀 더 짧은 구문 }

```markdown
SELECT O.CustomerID, C.CustomerName
FROM Orders O
JOIN Customers C ON O.CustomerID = C.CustomerID;
```

[112] Q. 주문 테이블에서, 고객ID, 고객이름, 제품ID, 주문수량을 표시하고 싶다면?
- JOIN을 사용!

```markdown
SELECT Orders.CustomerID, Customers.CustomerName,
  Orders.ProductID, Orders.OrderQuantity
FROM Orders
JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```

[113] I. 결과를 다시 SELECT 가 가능함

```markdown
SELECT *
FROM (
  SELECT O.CustomerID, C.CustomerName, O.ProductID, O.OrderQuantity
  FROM Orders O
  JOIN Customers C ON O.CustomerID = C.CustomerID
) OC
```

[114] Q. 주문 테이블에서, CustomerID 대신에 CustomerName을, ProductID 대신에 ProductName을 표시하고 싶다면?

```markdown
SELECT *
FROM (
  SELECT O.CustomerID, C.CustomerName, O.ProductID, O.OrderQuantity
  FROM Orders O
  JOIN Customers C ON O.CustomerID = C.CustomerID
) OC
JOIN Products P ON OC.ProductID = P.ProductID
```

[115] Q. 주문 테이블에서, 다음과 같이 표시하고 싶다면?

```markdown
SELECT OC.CustomerName, P.ProductName, P.ProductPrice, OC.OrderQuantity
FROM 
( SELECT O.CustomerID, C.CustomerName, O.ProductID, O.OrderQuantity
FROM Orders O
JOIN Customers C ON O.CustomerID = C.CustomerID
) OC
JOIN Products P ON OC.ProductID = P.ProductID
```

[116] Q. 주문 테이블에서, 다음과 같이 표시하고 싶다면? (OrderTotal 추가)

```markdown
SELECT OC.CustomerName, P.ProductName, P.ProductPrice, OC.OrderQuantity, P.ProductPrice * OC.OrderQuantity AS OrderTotal
FROM 
( SELECT O.CustomerID, C.CustomerName, O.ProductID, O.OrderQuantity
FROM Orders O
JOIN Customers C ON O.CustomerID = C.CustomerID
) OC
JOIN Products P ON OC.ProductID = P.ProductID
```

[117] I. "뷰(View)" 를 생성

```markdown
CREATE VIEW Order2 AS
SELECT OC.CustomerName, P.ProductName, P.ProductPrice, OC.OrderQuantity, P.ProductPrice * OC.OrderQuantity AS OrderTotal
FROM 
( SELECT O.CustomerID, C.CustomerName, O.ProductID, O.OrderQuantity
FROM Orders O
JOIN Customers C ON O.CustomerID = C.CustomerID
) OC
JOIN Products P ON OC.ProductID = P.ProductID
```

[118] I. "뷰(View)" 에 대한 질의

```markdown
SELECT * FROM Order2;
```

[119] Q. 각 메뉴별 주문 총 금액을 알고 싶다면?
- SUM, GROUP BY 항목 등을 사용

```markdown
SELECT ProductName, SUM(OrderTotal) FROM Order2 GROUP BY ProductName;
```

[120] I. 주문 항목을 추가

```markdown
INSERT INTO Orders (CustomerID, ProductID, OrderQuantity)
VALUES (1, 1, 100);
```

[121] I. 주문 항목을 수정: 100개 주문 항목을 50개로 수정

```markdown
UPDATE Orders SET OrderQuantity=50 WHERE OrderID=?
```

[122] I. 주문 항목을 삭제

```markdown
DELETE FROM Orders WHERE OrderID=16
```

### 3. 관계형 데이터베이스 실습 (2)

[201] Q. 앞에서 10개?

```markdown
SELECT * FROM price LIMIT 10;
```

[202] Q. 고추장만 보기
- WHERE 항목 이용, pum name 컬럼 이용

```markdown
SELECT * FROM price WHERE pum name="고추장";
```

[203] Q. 고추장의 개수
- 조건,함수: WHERE, COUNT
- 이용 컬럼: good id, pum name 

```markdown
SELECT COUNT(good id) FROM price WHERE pum name="고추장";
```

[204] Q. 고추장의 평균 가격
- 조건,함수: WHERE, AVG
- 이용 컬럼: sales price, pum name

```markdown
SELECT AVG(sales price) FROM price WHERE pum name="고추장";
```

[205] Q. 제일 비싼 고추장 가격
- 조건,함수: WHERE, MAX
- 이용 컬럼: sales price, pum name

```markdown
SELECT MAX(sales price) FROM price WHERE pum name="고추장";
```

[206] Q. 제일 비싼 고추장의 상품명
- 조건,함수: WHERE, MAX
- 이용 컬럼: sales price, pum name, good name

```markdown
[SQLite]
SELECT good name, MAX(sales price) FROM price WHERE pum name="고추장";
[MySQL(2)]
SELECT good name, sales price FROM price
WHERE sales price = (SELECT MAX(sales price) FROM price WHERE pum name="고추장");
```

[207] Q. 제일 싼 고추장의 상품명
- 조건,함수: WHERE, MIN
- 이용 컬럼: sales price, pum name, good name

```markdown
[SQLite]
SELECT good name, MIN(sales price) FROM price WHERE pum name="고추장";
[MySQL]
SELECT good name, sales price FROM price
WHERE pum name="고추장" AND
sales price = (SELECT MIN(sales price) FROM price WHERE pum name="고추장");
[MySQL(2), SQLite(2)]
SELECT good name, sales price FROM price
WHERE sales price = (SELECT MIN(sales price) FROM price WHERE pum name="고추장")
AND pum name="고추장";
```

[208] Q. 제일 비싼 고추장과 제일 싼 고추장을 함께 보고 싶다면???

```markdown
[SQLite]
SELECT good name, MAX(sales price) AS price FROM price WHERE pum name="고추장"
UNION
SELECT good name, MIN(sales price) AS price FROM price WHERE pum name="고추장";
[MySQL]
(
SELECT good name, sales price FROM price
WHERE pum name="고추장" AND
sales price = (SELECT MAX(sales price) FROM price WHERE pum name="고추장")
)
UNION
(
SELECT good name, sales price FROM price
WHERE sales price = (SELECT MIN(sales price) FROM price WHERE pum name="고추장")
AND pum name="고추장"
);
```

[209] Q. 제일 비싼 고추장과 제일 싼 고추장을 함께, "옆으로" 나열해서 보고 싶다면?

```markdown
SELECT * FROM (
(SELECT good name, MAX(sales price) FROM price WHERE pum name="고추장"),
(SELECT good name, MIN(sales price) FROM price WHERE pum name="고추장")
);
```

[210] Q. 된장의 개수
- 조건,함수: WHERE, COUNT
- 이용 컬럼: good id, pum name

```markdown
SELECT COUNT(good id) FROM price WHERE pum name="된장";
```

[211] Q. 된장의 평균 가격
- 조건,함수: WHERE, AVG
- 이용 컬럼: sales price, pum name

```markdown
SELECT AVG(sales price) FROM price WHERE pum name="된장";
```

[212] Q. 고추장과 된장의 평균 가격
- 조건,함수: WHERE, AND, AVG
- 이용 컬럼: sales price, pum name

```markdown
SELECT AVG(sales price) FROM price WHERE pum name="고추장" OR pum name="된장";
```

[213] Q. 면도기 목록
- 조건,함수: WHERE
- 이용 컬럼: pum name

```markdown
SELECT * FROM price WHERE pum name="면도기";
```

[214] Q. 면도기의 개수
- 조건,함수: WHERE, COUNT
- 이용 컬럼: good id, pum name

```markdown
SELECT COUNT(good id) FROM price WHERE pum name="면도기";
```

[215] Q. 면도기 6중 날인 항목

```markdown
SELECT good name FROM price 
WHERE pum name="면도기" AND good name LIKE "%6중%";
```

[216] Q. 면도기 6중 날 항목 중에서 가장 비싼 항목
- 조건,함수: WHERE, MAX
- 이용 컬럼: good name, sales price, pum name, good name

```markdown
[SQLite]
SELECT good name, MAX(sales price)
FROM price WHERE pum name="면도기" AND good name LIKE "%6중%";
[MySQL]
SELECT good name, sales price FROM price 
WHERE sales price = (
  SELECT MAX(sales price) FROM price
  WHERE pum name="면도기" AND good name LIKE "%6중%"
)
AND pum name="면도기" AND good name LIKE "%6중%"
```

[217] Q. 각 제품들의 개수와 평균 가격
- 조건,함수: WHERE, COUNT, AVG, GROUP BY
- 이용 컬럼: pum name, good id, sales price

```markdown
SELECT pum name, COUNT(good id), AVG(sales price) FROM price GROUP BY pum name;
```

[218] Q. 각 제품별 가장 비싼 제품의 이름
- 조건,함수: WHERE, MAX, GROUP BY
- 이용 컬럼: pum name, good id, sales price

```markdown
[SQLite]
SELECT pum name, good name, MAX(sales price) FROM price GROUP BY pum name;
[MySQL (1)]
SELECT pum name, max sales price, (
    SELECT good name
    FROM price
    WHERE max price.pum name = pum name
    AND max price.max sales price = sales price
    LIMIT 1
)
FROM (
    SELECT pum name, MAX( sales price ) AS max sales price
    FROM price
    GROUP BY pum name
) max price;
```

[219] Q. 각 제품들의 개수와 평균 가격
- 조건,함수: WHERE, COUNT, AVG, GROUP BY
- 이용 컬럼: pum name, good id, sales price

```markdown
SELECT pum name, COUNT(good id), AVG(sales price) FROM price GROUP BY pum name;
```

[220] Q. 제품별 평균할인가를 높은 순서대로 이름과 함께 출력
- 조건,함수: WHERE, AVG, GROUP BY, ORDER BY, DESC
- 이용 컬럼: pum name, sales price

```markdown
SELECT pum name, AVG((benefit * -1 * 100) / sales price) AS ave discount price 
FROM price GROUP BY pum name ORDER BY ave discount price DESC;
```

### 3. 관계형 데이터베이스 실습 (3)

[301] Q. "[TRACE]" 메시지만 표시
- 조건,함수: WHERE
- 이용 컬럼: field4

```markdown
SELECT * FROM sample WHERE field4="[TRACE]";
```

[302] Q. field4 에 어떤 항목들이 있는지 목록 만들기
- 조건,함수: DISTINCT
- 이용 컬럼: field4

```markdown
SELECT DISTINCT(field4) FROM sample;
```

[303] Q. field4 에 어떤 항목들이 있는지 목록 만들기
- 조건,함수: DISTINCT
- 이용 컬럼: field4

```markdown
SELECT DISTINCT(field4) FROM sample;
```

[304] Q. field4 에 어떤 항목들이 몇 개가 있는지를 찾기
- 조건,함수: COUNT, GROUP BY
- 이용 컬럼: field4

```markdown
SELECT field4, count(field4) FROM sample GROUP BY field4;
```

[305] Q. 시간(초)별로 몇 건의 이벤트가 일어났는지 알아보기
- 조건,함수: COUNT, GROUP BY
- 이용 컬럼: field2

```markdown
SELECT field2, count(field2) FROM sample GROUP BY field2;
```

[306] Q. 시간(초)별로, 이벤트가 각각 몇 건이 일어났는지 알아보기
- 조건,함수: COUNT, GROUP BY
- 이용 컬럼: field2, field4

```markdown
SELECT field2, field4, COUNT(field4) FROM sample GROUP BY field2, field4;
```

[307] Q. 클래스별로, 이벤트가 각각 몇 건이 일어났는지 알아보기
- 조건,함수: COUNT, GROUP BY
- 이용 컬럼: field3, field4

```markdown
SELECT field3, field4, COUNT(field4) FROM sample GROUP BY field3, field4;
```

[308] Q. "incorrect id" 가 발생한 항목만 따로 보기
- 조건,함수: WHERE
- 이용 컬럼: field5

```markdown
SELECT * FROM sample WHERE field5 LIKE "%incorrect id%";
```

[309] Q. "19:00:00" ~ "19:30:00" 사이에 일어난 이벤트만 따로 보기
- 조건,함수: WHERE, AND, >=, <=
- 이용 컬럼: field2

```markdown
SELECT * FROM sample WHERE field2 >= "19:00:00" AND field2 <= "19:30:00";
```

[310] Q. Actors 테이블에는 총 몇 개의 행(rows)가 있는지 조회하기
- 조건,함수: COUNT
- 이용 컬럼: field1

```markdown
SELECT COUNT(field1) FROM Actors;
```

[311] Q. field2 별로 각각 몇 개의 행(rows)이 있는지를, 많은 순서대로 정렬하여 표시
- 조건,함수: COUNT, AS, GROUP BY, ORDER BY, DESC
- 이용 컬럼: field1

```markdown
SELECT field2, COUNT(field2) AS field2count
FROM Actors GROUP BY field2 ORDER BY field2count DESC;
```

[312] Q. field2 가 "20000513" 인 사람의 데이터 조회
- 조건,함수: WHERE
- 이용 컬럼: field2

```markdown
SELECT field1, field2, field3, field4 FROM Actors WHERE field2="20000513";
```

[313] Q. 직원은 모두 몇 명일까요?
- 조건,함수: DISTINCE
- 이용 컬럼: field2

```markdown
SELECT COUNT(DISTINCT(field2)) FROM Actors;
```

[314] Q. 각각의 직원들이 발생시킨 이벤트는 몇 건일까요? (많은 순서대로, 이름도 표시)
- 조건,함수: COUNT, GROUP BY
- 이용 컬럼: field2, field4

```markdown
SELECT field2, field3, COUNT(field2) AS field2count
FROM Actors GROUP BY field2 ORDER BY field2count DESC
```

[315] Q. 클래스별로, 이벤트 별로 각각 몇 건이 일어났는지 알아보기
- 조건,함수: COUNT, GROUP BY
- 이용 컬럼: field3, field4

```markdown
SELECT field3, field4, COUNT(field4) FROM sample GROUP BY field3, field4;
```


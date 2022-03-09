# Data Fundamentals - Class

## 1. 연관 사이트

### 1.1 EduTracker

강의 중간에 실습을 하는 경우, 강의에 참석하시는 분들의 진행 상황을 확인하기 위해 EduTracker 를 사용하고 있습니다.
[EduTracker](http://exastudy.cafe24.com/solutions/edutracker/) 사이트에 접속 하신 후, 아래의 항목을 입력해 주십시오.

- 이벤트 코드: "Data Fundamentals" 항목을 선택해 주십시오.
- 이벤트 비밀번호: 220310 을 입력해 주십시오.
- 사용자 이름: 참석자 분의 성함을 입력해 주십시오. (예. 홍길동)
- 사용자 비밀번호: 임의의 비밀번호를 입력해 주십시오.

로그인을 성공하고 난 이후에, 다시 로그인을 하기 위해서는 이전에 사용하셨던 "사용자 이름", "사용자 비밀번호" 를 입력하시면 됩니다.
만약, 비밀번호를 잃어버리신 경우에는, 새로운 "사용자 이름" 과 새로운 "사용자 비밀번호" 를 입력하여 로그인 해 주십시오.

### 1.2 SQLite Browser

실습에 사용하는 SQLite Browser 를 다운로드 하는 사이트 입니다.
- [SQLite Browser Download](https://sqlitebrowser.org/)

### 1.3 Sample Database Sites

- [Test Site 1](http://141.164.49.85/phpmyadmin/)
  - ID: user01 ~ user50
  - PW: 강의시간 배포
- [Test Site 2](http://141.164.48.150/phpmyadmin/)
  - ID: user01 ~ user50
  - PW: 강의시간 배포

## 2. 샘플 파일

### 2.1 Sample files

실습에 사용하는 샘플 파일입니다.

- [Download](http://exastudy.cafe24.com/lectures/data_fundamentals/)

### 2.2 통계청 자료

통계청 - 온라인 수집가격 정보

[통계데이터 센터](https://data.kostat.go.kr/sbchome/index.do)

- 빅데이터활용 -> 온라인 수집가격 정보 -> 분석활용가격정보(2021년 12월)

### 2.3 샘플 로그

[Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=37003)

## 3. 샘플 쿼리

쿼리를 직접 작성하시는 것을 추천하지만, 정답 확인이 필요한 경우에는 [Data Fundamentals Class Queries With Answers](data_fundamentals_class_queries_with_answers.html) 페이지를 참고해 주십시오.


### 3. 관계형 데이터베이스 실습 (1)

[101] Q. Customers 테이블의 모든 데이터 조회

[102] Q. Customers 테이블에서 진짜 이름만 조회

[103] Q. Customers 테이블에서 전체 사람 수 조회

[104] Q. Orders 테이블의 모든 데이터 조회

[105] Q. Orders 테이블의 주문 수량 컬럼만 조회

[106] Q. Orders 테이블의 주문 수량 컬럼에서, 총 주문 수량을 조회

[107] Q. Orders 테이블에서 짜장면의 주문 내역만 조회

[108] Q. 짜장면의 주문 수량은?

[109] Q. 합치기

[110] Q. 주문 테이블에서, 고객ID 옆에 고객 이름을 표시하고 싶다면?
- JOIN을 사용!

[111] Q. 주문 테이블에서, 고객ID 옆에 고객 이름을 표시하고 싶다면?
- JOIN을 사용! { 좀 더 짧은 구문 }

[112] Q. 주문 테이블에서, 고객ID, 고객이름, 제품ID, 주문수량을 표시하고 싶다면?
- JOIN을 사용!

[113] I. 결과를 다시 SELECT 가 가능함

[114] Q. 주문 테이블에서, CustomerID 대신에 CustomerName을, ProductID 대신에 ProductName을 표시하고 싶다면?

[115] Q. 주문 테이블에서, 다음과 같이 표시하고 싶다면?

[116] Q. 주문 테이블에서, 다음과 같이 표시하고 싶다면? (OrderTotal 추가)

[117] I. "뷰(View)" 를 생성

[118] I. "뷰(View)" 에 대한 질의

[119] Q. 각 메뉴별 주문 총 금액을 알고 싶다면?
- SUM, GROUP BY 항목 등을 사용

[120] I. 주문 항목을 추가

[121] I. 주문 항목을 수정: 100개 주문 항목을 50개로 수정

[122] I. 주문 항목을 삭제

### 3. 관계형 데이터베이스 실습 (2)

[201] Q. 앞에서 10개?

[202] Q. 고추장만 보기
- WHERE 항목 이용, pum name 컬럼 이용

[203] Q. 고추장의 개수
- 조건,함수: WHERE, COUNT
- 이용 컬럼: good id, pum name 

[204] Q. 고추장의 평균 가격
- 조건,함수: WHERE, AVG
- 이용 컬럼: sales price, pum name

[205] Q. 제일 비싼 고추장 가격
- 조건,함수: WHERE, MAX
- 이용 컬럼: sales price, pum name

[206] Q. 제일 비싼 고추장의 상품명
- 조건,함수: WHERE, MAX
- 이용 컬럼: sales price, pum name, good name

[207] Q. 제일 싼 고추장의 상품명
- 조건,함수: WHERE, MIN
- 이용 컬럼: sales price, pum name, good name

[208] Q. 제일 비싼 고추장과 제일 싼 고추장을 함께 보고 싶다면???

[209] Q. 제일 비싼 고추장과 제일 싼 고추장을 함께, "옆으로" 나열해서 보고 싶다면?

[210] Q. 된장의 개수
- 조건,함수: WHERE, COUNT
- 이용 컬럼: good id, pum name

[211] Q. 된장의 평균 가격
- 조건,함수: WHERE, AVG
- 이용 컬럼: sales price, pum name

[212] Q. 고추장과 된장의 평균 가격
- 조건,함수: WHERE, AND, AVG
- 이용 컬럼: sales price, pum name

[213] Q. 면도기 목록
- 조건,함수: WHERE
- 이용 컬럼: pum name

[214] Q. 면도기의 개수
- 조건,함수: WHERE, COUNT
- 이용 컬럼: good id, pum name

[215] Q. 면도기 6중 날인 항목

[216] Q. 면도기 6중 날 항목 중에서 가장 비싼 항목
- 조건,함수: WHERE, MAX
- 이용 컬럼: good name, sales price, pum name, good name

[217] Q. 각 제품들의 개수와 평균 가격
- 조건,함수: WHERE, COUNT, AVG, GROUP BY
- 이용 컬럼: pum name, good id, sales price

[218] Q. 각 제품별 가장 비싼 제품의 이름
- 조건,함수: WHERE, MAX, GROUP BY
- 이용 컬럼: pum name, good id, sales price

[219] Q. 각 제품들의 개수와 평균 가격
- 조건,함수: WHERE, COUNT, AVG, GROUP BY
- 이용 컬럼: pum name, good id, sales price

[220] Q. 제품별 평균할인가를 높은 순서대로 이름과 함께 출력
- 조건,함수: WHERE, AVG, GROUP BY, ORDER BY, DESC
- 이용 컬럼: pum name, sales price

### 3. 관계형 데이터베이스 실습 (3)

[301] Q. "[TRACE]" 메시지만 표시
- 조건,함수: WHERE
- 이용 컬럼: field4

[302] Q. field4 에 어떤 항목들이 있는지 목록 만들기
- 조건,함수: DISTINCT
- 이용 컬럼: field4

[303] Q. field4 에 어떤 항목들이 있는지 목록 만들기
- 조건,함수: DISTINCT
- 이용 컬럼: field4

[304] Q. field4 에 어떤 항목들이 몇 개가 있는지를 찾기
- 조건,함수: COUNT, GROUP BY
- 이용 컬럼: field4

[305] Q. 시간(초)별로 몇 건의 이벤트가 일어났는지 알아보기
- 조건,함수: COUNT, GROUP BY
- 이용 컬럼: field2

[306] Q. 시간(초)별로, 이벤트가 각각 몇 건이 일어났는지 알아보기
- 조건,함수: COUNT, GROUP BY
- 이용 컬럼: field2, field4

[307] Q. 클래스별로, 이벤트가 각각 몇 건이 일어났는지 알아보기
- 조건,함수: COUNT, GROUP BY
- 이용 컬럼: field3, field4

[308] Q. "incorrect id" 가 발생한 항목만 따로 보기
- 조건,함수: WHERE
- 이용 컬럼: field5

[309] Q. "19:00:00" ~ "19:30:00" 사이에 일어난 이벤트만 따로 보기
- 조건,함수: WHERE, AND, >=, <=
- 이용 컬럼: field2

[310] Q. Actors 테이블에는 총 몇 개의 행(rows)가 있는지 조회하기
- 조건,함수: COUNT
- 이용 컬럼: field1

[311] Q. field2 별로 각각 몇 개의 행(rows)이 있는지를, 많은 순서대로 정렬하여 표시
- 조건,함수: COUNT, AS, GROUP BY, ORDER BY, DESC
- 이용 컬럼: field1

[312] Q. field2 가 "20000513" 인 사람의 데이터 조회
- 조건,함수: WHERE
- 이용 컬럼: field2

[313] Q. 직원은 모두 몇 명일까요?
- 조건,함수: DISTINCE
- 이용 컬럼: field2

[314] Q. 각각의 직원들이 발생시킨 이벤트는 몇 건일까요? (많은 순서대로, 이름도 표시)
- 조건,함수: COUNT, GROUP BY
- 이용 컬럼: field2, field4

[315] Q. 클래스별로, 이벤트 별로 각각 몇 건이 일어났는지 알아보기
- 조건,함수: COUNT, GROUP BY
- 이용 컬럼: field3, field4

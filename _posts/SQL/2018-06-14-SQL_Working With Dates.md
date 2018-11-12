---
layout: post
title: SQL Working With Dates
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.



### SQL Dates

> 날짜 작업을 할 때 가장 어려운 부분은 삽입하려는 날짜 형식이 데이터베이스의 날짜 열 형식과 일치하는지 확인하는 것입니다.

데이터에 날짜 부분 만 포함되어 있으면 쿼리가 예상대로 작동합니다. 그러나 시간 부분이 관련되면 더 복잡해집니다.

---



### SQL Date Data Types



**MySQL** 에는 데이터베이스에 날짜 또는 날짜 / 시간 값을 저장하기위한 다음 데이터 유형이 있습니다:

- DATE - format YYYY-MM-DD
- DATETIME - format: YYYY-MM-DD HH:MI:SS
- TIMESTAMP - format: YYYY-MM-DD HH:MI:SS
- YEAR - format YYYY or YY



**SQL Server**에는 데이터베이스에 날짜 또는 날짜 / 시간 값을 저장하기위한 다음 데이터 형식이 있습니다:

- DATE - format YYYY-MM-DD
- DATETIME - format: YYYY-MM-DD HH:MI:SS
- SMALLDATETIME - format: YYYY-MM-DD HH:MI:SS
- TIMESTAMP - format: a unique number



**Note** : 데이터베이스에 새 테이블을 만들 때 열에 대해 날짜 유형이 선택됩니다!

---



### SQL Working with Dates

> 관련된 시간 구성 요소가 없으면 두 날짜를 쉽게 비교할 수 있습니다!



다음의 "Orders" 테이블이 있다고 가정합니다:

| OrderId | ProductName            | OrderDate  |
| ------- | ---------------------- | ---------- |
| 1       | Geitost                | 2008-11-11 |
| 2       | Camembert Pierrot      | 2008-11-09 |
| 3       | Mozzarella di Giovanni | 2008-11-11 |
| 4       | Mascarpone Fabioli     | 2008-10-29 |



이제 우리는 위 표에서 OrderDate가 "2008-11-11"인 레코드를 선택하려고합니다.

다음 SELECT 문을 사용합니다:

```sql
SELECT * FROM Orders WHERE OrderDate='2008-11-11'
```



결과 세트는 다음과 같습니다:

| OrderId | ProductName            | OrderDate  |
| ------- | ---------------------- | ---------- |
| 1       | Geitost                | 2008-11-11 |
| 3       | Mozzarella di Giovanni | 2008-11-11 |



이제 "Order"테이블이 다음과 같이 보입니다 ( "Orderdate"열의 시간 구성 요소에 주목하십시오):

| OrderId | ProductName            | OrderDate           |
| ------- | ---------------------- | ------------------- |
| 1       | Geitost                | 2008-11-11 13:23:44 |
| 2       | Camembert Pierrot      | 2008-11-09 15:45:21 |
| 3       | Mozzarella di Giovanni | 2008-11-11 11:12:01 |
| 4       | Mascarpone Fabioli     | 2008-10-29 14:56:59 |



 위와 같은 SELECT 문을 사용하는 경우 :

```sql
SELECT * FROM Orders WHERE OrderDate='2008-11-11'
```

우리는 결과를 얻지 못할 것이다! 이는 쿼리가 시간 부분이 없는 날짜만 찾고 있기 때문입니다.

**Tip:** 검색어를 간단하고 쉽게 유지하려면 날짜에 시간 구성 요소를 허용하지 마십시오!


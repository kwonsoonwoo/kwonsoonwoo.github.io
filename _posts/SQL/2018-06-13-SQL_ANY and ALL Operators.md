---
layout: post
title: SQL ANY and ALL Operators(티스토리 이전)
category: SQL
tags:
  - SQL
  - SQL ANY and ALL Operators
  - SQL ANY ALL 연산자
---



[여기로 이동](https://lifetutorial.tistory.com/43)

<!--

[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.



### The SQL ANY and ALL Operators

---

ANY W ALL 연산자는 WHERE 또는 HAVING 절과 함께 사용됩니다.

ANY 연산자는 하위 쿼리 값 중 하나가 조건을 충족하면 true를 반환합니다.

ALL 연산자는 모든 하위 쿼리 값이 조건을 충족하면 true를 반환합니다.



#### ANY Syntax

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name operator ANY
(SELECT column_name FROM table_name WHERE condition);
```



#### ALL Syntax

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name operator ALL
(SELECT column_name FROM table_name WHERE condition);
```

> **참고** : 연산자는 표준 비교 연산자 (=, <>,! =,>,> =, <또는 <=) 여야합니다.



### Demo Database

---

다음은 Northwind 샘플 데이터베이스의 "Products"테이블에서 선택한 것입니다:

| ProductID | ProductName                  | SupplierID | CategoryID | Unit                | Price |
| --------- | ---------------------------- | ---------- | ---------- | ------------------- | ----- |
| 1         | Chais                        | 1          | 1          | 10 boxes x 20 bags  | 18    |
| 2         | Chang                        | 1          | 1          | 24 - 12 oz bottles  | 19    |
| 3         | Aniseed Syrup                | 1          | 2          | 12 - 550 ml bottles | 10    |
| 4         | Chef Anton's Cajun Seasoning | 2          | 2          | 48 - 6 oz jars      | 22    |
| 5         | Chef Anton's Gumbo Mix       | 2          | 2          | 36 boxes            | 21.35 |



그리고 "OrderDetails"테이블의 선택항목 입니다 :

| OrderDetailID | OrderID | ProductID | Quantity |
| ------------- | ------- | --------- | -------- |
| 1             | 10248   | 11        | 12       |
| 2             | 10248   | 42        | 10       |
| 3             | 10248   | 72        | 5        |
| 4             | 10249   | 14        | 9        |
| 5             | 10249   | 51        | 40       |

---



### SQL ANY Examples

---

하위 쿼리 값 중 하나가 조건을 충족하면 ANY 연산자는 TRUE를 반환합니다.

다음 SQL 문은 TRUE를 리턴하고 quantity = 10 인 OrderDetails 테이블에 모든 레코드를 찾으면 제품 이름을 나열합니다:



#### Example

```sql
SELECT ProductName
FROM Products
WHERE ProductID = ANY (SELECT ProductID FROM OrderDetails WHERE Quantity = 10);
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 31

| ProductName                      |
| -------------------------------- |
| Chais                            |
| Chang                            |
| Chef Anton's Cajun Seasoning     |
| Uncle Bob's Organic Dried Pears  |
| Konbu                            |
| Tofu                             |
| Pavlova                          |
| Teatime Chocolate Biscuits       |
| Sir Rodney's Scones              |
| Guaraná Fantástica               |
| NuNuCa Nuß-Nougat-Creme          |
| Gumbär Gummibärchen              |
| Thüringer Rostbratwurst          |
| Nord-Ost Matjeshering            |
| Sasquatch Ale                    |
| Steeleye Stout                   |
| Gravad lax                       |
| Côte de Blaye                    |
| Boston Crab Meat                 |
| Jack's New England Clam Chowder  |
| Singaporean Hokkien Fried Mee    |
| Perth Pasties                    |
| Tourtière                        |
| Pâté chinois                     |
| Raclette Courdavault             |
| Tarte au sucre                   |
| Louisiana Fiery Hot Pepper Sauce |
| Scottish Longbreads              |
| Mozzarella di Giovanni           |
| Rhönbräu Klosterbier             |
| Original Frankfurter grüne Soße  |



다음 SQL.은 TRUE를 리턴하고 quantity> 99 인 OrderDetails 테이블에 모든 레코드를 찾으면 제품 이름을 나열합니다:



#### Example

```sql
SELECT ProductName
FROM Products
WHERE ProductID = ANY (SELECT ProductID FROM OrderDetails WHERE Quantity > 99);
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 2

| ProductName    |
| -------------- |
| Steeleye Stout |
| Pâté chinois   |



### SQL ALL Example

---

ALL 연산자는 모든 하위 쿼리 값이 조건을 충족하면 TRUE를 반환합니다.

OrderDetails 테이블의 모든 레코드가 quantity = 10이면 다음 SQL 문은 TRUE를 반환하고 제품 이름을 나열합니다:



#### Example

```sql
SELECT ProductName
FROM Products
WHERE ProductID = ALL (SELECT ProductID FROM OrderDetails WHERE Quantity = 10);
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 0

| ProductName |
| ----------- |
|             |

-->
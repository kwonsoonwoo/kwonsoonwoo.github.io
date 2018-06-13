---
layout: post
title: SQL GROUP BY Statement
category: SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





### The SQL GROUP BY Statement

---

GROUP BY 문은 집계 함수 (COUNT, MAX, MIN, SUM, AVG)와 함께 사용되어 결과 집합을 하나 이상의 열로 그룹화합니다.



####GROUP BY Syntax

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);
```





### Demo Database

---

다음은 Northwind 샘플 데이터베이스의 "Customers"테이블에서 선택한 것입니다:



| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ------------------ | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Maria Anders       | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |



### SQL GROUP BY Examples

---

다음 SQL 문은 각 국가의 고객 수를 나열합니다:



#### Example

```sql
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 21

| COUNT(CustomerID) | Country     |
| ----------------- | ----------- |
| 3                 | Argentina   |
| 2                 | Austria     |
| 2                 | Belgium     |
| 9                 | Brazil      |
| 3                 | Canada      |
| 2                 | Denmark     |
| 2                 | Finland     |
| 11                | France      |
| 10                | Germany     |
| 1                 | Ireland     |
| 3                 | Italy       |
| 5                 | Mexico      |
| 4                 | Norway      |
| 1                 | Poland      |
| 2                 | Portugal    |
| 5                 | Spain       |
| 2                 | Sweden      |
| 2                 | Switzerland |
| 7                 | UK          |
| 13                | USA         |
| 4                 | Venezuela   |



다음 SQL 문은 각 국가의 고객 수를 기준으로 많은 순에서 작은 순으로 정렬하여 나열합니다:



#### Example

```sql
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
ORDER BY COUNT(CustomerID) DESC;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 21

| COUNT(CustomerID) | Country     |
| ----------------- | ----------- |
| 13                | USA         |
| 11                | France      |
| 10                | Germany     |
| 9                 | Brazil      |
| 7                 | UK          |
| 5                 | Mexico      |
| 5                 | Spain       |
| 4                 | Norway      |
| 4                 | Venezuela   |
| 3                 | Argentina   |
| 3                 | Canada      |
| 3                 | Italy       |
| 2                 | Austria     |
| 2                 | Belgium     |
| 2                 | Denmark     |
| 2                 | Finland     |
| 2                 | Portugal    |
| 2                 | Sweden      |
| 2                 | Switzerland |
| 1                 | Ireland     |
| 1                 | Poland      |



### Demo Database

---

아래는 Northwind 샘플 데이터베이스의 "Orders"테이블에서 선택한 것입니다:

| OrderID | CustomerID | EmployeeID | OrderDate  | ShipperID |
| ------- | ---------- | ---------- | ---------- | --------- |
| 10248   | 90         | 5          | 1996-07-04 | 3         |
| 10249   | 81         | 6          | 1996-07-05 | 1         |
| 10250   | 34         | 4          | 1996-07-08 | 2         |



'Shippers'표의 선택 항목입니다 :

| ShipperID | ShipperName      |
| --------- | ---------------- |
| 1         | Speedy Express   |
| 2         | United Package   |
| 3         | Federal Shipping |



### GROUP BY With JOIN Example

---

다음 SQL 문은 각 발송인이 보낸 주문 수를 나열합니다:



#### Example

```sql
SELECT Shippers.ShipperName, COUNT(Order.OrderID) AS NumberOfOrders FROM Orders
LEFT JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID
GROUP BY ShipperName;
```



### Result:

Number of Records: 3

| ShipperName      | NumberOfOrders |
| ---------------- | -------------- |
| Federal Shipping | 68             |
| Speedy Express   | 54             |
| United Package   | 74             |
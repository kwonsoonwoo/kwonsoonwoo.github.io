---
layout: post
title: SQL INNER JOIN Keyword
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





### SQL INNER JOIN Keyword

---

INNER JOIN 키워드는 두 표에서 모두 일치하는 값을 가진 레코드를 선택합니다.



#### INNER JOIN Syntax



```sql
SELECT column_name(S)
FROM table1
INNER JOIN table2 ON table1.column_name = table2.column_name;
```

>[홈페이지 그림 참조](https://www.w3schools.com/sql/sql_join_inner.asp)





### Demo Database

---

이 튜토리얼에서는 잘 알려진 Northwind 샘플 데이터베이스를 사용합니다.

다음은 "Orders" 테이블에서 선택한 항목입니다:



| OrderID | CustomerID | EmployeeID | OrderDate  | ShipperID |
| ------- | ---------- | ---------- | ---------- | --------- |
| 10308   | 2          | 7          | 1996-09-18 | 3         |
| 10309   | 37         | 3          | 1996-09-19 | 1         |
| 10310   | 77         | 8          | 1996-09-20 | 2         |



그리고 "Customers" 테이블의 선택 :



| CustomerID | CustomerName                       | ContactName    | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | -------------- | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Maria Anders   | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo   | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno | Mataderos 2312                | México D.F. | 05023      | Mexico  |



### JOIN Three Tables

---

다음 SQL 문은 고객 및 배송 정보가 포함 된 모든 주문을 선택합니다.



#### Example

```sql
SELECT Orders.OrderID, Customers.CustomerName, Shippers.ShipperName
FROM ((Orders
INNER JOIN Customers ON Orders.CUSTOMER ID = Customer.Customer10:
INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID);
```


---
layout: post
title: SQL FULL OUTER JOIN Keyword
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





### SQL FULL OUTER JOIN Keyword

---

FULL OUTER JOIN 키워드는 왼쪽 (table1) 또는 오른쪽 (table2) 테이블 레코드가 일치 할 때 모든 레코드를 리턴합니다.



#### FULL OUTER JOIN Syntax

```sql
SELECT column_name(S)
FROM table1
FULL OUTER JOIN table2 ON table1.column_name = table2.column_name;
```


>[홈페이지 그림 참조](https://www.w3schools.com/sql/sql_join_inner.asp)





### Demo Database

---

이 튜토리얼에서는 잘 알려진 Northwind 샘플 데이터베이스를 사용합니다.

다음은 "Customers" 테이블에서 선택한 항목입니다:

| CustomerID | CustomerName                       | ContactName    | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | -------------- | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Maria Anders   | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo   | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno | Mataderos 2312                | México D.F. | 05023      | Mexico  |



그리고 "Orders" 테이블에서 선택한 항목입니다 :

| OrderID | CustomerID | EmployeeID | OrderDate  | ShipperID |
| ------- | ---------- | ---------- | ---------- | --------- |
| 10308   | 2          | 7          | 1996-09-18 | 3         |
| 10309   | 37         | 3          | 1996-09-19 | 1         |
| 10310   | 77         | 8          | 1996-09-20 | 2         |



### SQL FULL OUTER JOIN Example

---

다음 SQL 문은 모든 직원과 모든 주문을 선택합니다:



#### Example

```sql
SELECT Customers.CutomerName, Orders.OrderID
FROM Customers
FULL OUTER JOIN Orders ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.CustomerName;
```



결과 집합의 선택 항목은 다음과 같습니다:



| CustomerName                       | OrderID |
| ---------------------------------- | ------- |
| Alfreds Futterkiste                |         |
| Ana Trujillo Emparedados y helados | 10308   |
| Antonio Moreno Taquería            | 10365   |
|                                    | 10382   |
|                                    | 10351   |

**참고** : FULL OUTER JOIN 키워드는 왼쪽 테이블 (Customers)의 모든 행과 오른쪽 테이블 (Orders)의 모든 행을 리턴합니다. 'Orders'에 일치하지 않는 행이 'Customers'에 있거나 'Cutomers'에 일치하지 않는 행이 'Orders'에 있는 경우 해당 행이 함께 표시됩니다.
---
layout: post
title: SQL LEFT JOIN Keyword
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





### SQL LEFT JOIN Keyword

---

LEFT JOIN 키워드는 왼쪽 테이블 (table1)의 모든 레코드와 오른쪽 테이블 (table2)의 일치 레코드를 반환합니다. 일치하는 것이 없으면 오른쪽 결과가 NULL입니다.



####LEFT JOIN Syntax



```sql
SELECT column_name(S)
FROM table1
LEFT JOIN table2 ON table1.column_name = table2.column_name;
```
**참고** : 일부 데이터베이스에서는 LEFT JOIN을 LEFT OUTER JOIN이라고합니다.

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



그리고 "Orders" 테이블에서 선택한 항목 :



| OrderID | CustomerID | EmployeeID | OrderDate  | ShipperID |
| ------- | ---------- | ---------- | ---------- | --------- |
| 10308   | 2          | 7          | 1996-09-18 | 3         |
| 10309   | 37         | 3          | 1996-09-19 | 1         |
| 10310   | 77         | 8          | 1996-09-20 | 2         |



### SQL LEFT JOIN Example

---

다음 SQL 문은 모든 고객과 고객이 가질 수 있는 주문을 모두 선택합니다:



#### Example

```sql
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID
ORDER BY Customers.CustomerName;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것

**참고** : LEFT JOIN 키워드는 오른쪽 테이블 (Orders)에 일치하는 항목이 없더라도 왼쪽 테이블 (Customers)의 모든 레코드를 반환합니다.



### Result:(일부만 발췌)

Number of Records: 215

| CustomerName                       | OrderID |
| ---------------------------------- | ------- |
| Ana Trujillo Emparedados y helados | 10308   |
| Antonio Moreno Taquería            | 10365   |
| Around the Horn                    | 10355   |
| Around the Horn                    | 10383   |
| B's Beverages                      | 10289   |
| Berglunds snabbköp                 | 10278   |
| Berglunds snabbköp                 | 10280   |
| Berglunds snabbköp                 | 10384   |
| Blauer See Delikatessen            | *null*  |
| Blondel père et fils               | 10265   |

**총 215개의 Records가 있음**
---
layout: post
title: SQL SELECT Statement
category: SQL
tags:
  - SQL
  - SQL SELECT Statement
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.







## The SQL SELECT Statement

---



SELECT 문은 데이터베이스에서 데이터를 선택하는 데 사용됩니다.

리턴 된 데이터는 result-set이라고 하는 result table에 저장됩니다.





## SELECT Syntax

---


```sql
SELECT column1, column2, ...
FROM table_name;
```



여기에서 column1, column2, ...는 데이터를 선택할 테이블의 필드 이름입니다. 표에서 사용 가능한 모든 필드를 선택하려면 아래 구문을 사용하십시오.



```sql
SELECT * FROM table_name;
```







## Demo Database

---

다음은 Northwind 샘플 데이터베이스의 "Customers"테이블에서 선택한 것입니다.



| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ------------------ | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Maria Anders       | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |







## SELECT Column Example

---

다음 SQL 문은 "Customers"테이블에서 "CustomerName"및 "City"열을 선택합니다.



### Example

```sql
SELECT CustomerName, City FROM Customers;
```

>[w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것







## SELECT * Example

---

다음 SQL 문은 "Customers"테이블에서 모든 열을 선택합니다.



### Example

```sql
SELECT * FROM Customers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것

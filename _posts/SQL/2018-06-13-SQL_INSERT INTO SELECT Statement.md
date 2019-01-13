---
layout: post
title: SQL INSERT INTO SELECT Statement
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.



### The SQL INSERT INTO SELECT Statement

---

 INSERT INTO SELECT 문은 한 테이블의 데이터를 복사하여 다른 테이블에 삽입합니다.

-  INSERT INTO SELECT는 소스 및 목표 테이블의 데이터 유형이 일치해야합니다.
- 목표 테이블의 기존 레코드는 영향을 받지 않습니다.



#### INSERT INTO SELECT Syntax

한 테이블의 모든 열을 다른 테이블로 복사  :

```sql
INSERT INTO table2
SELECT * FROM table1
WHERE condition;
```



한 테이블의 일부 열만 다른 테이블로 복사 :

```sql
INSERT INTO table2 (column1, column2, column3, ...)
SELECT column1, column2, column3, ...
FROM table1
WHERE condition;
```





### DEMO Database

---

이 튜토리얼에서는 잘 알려진 Northwind 샘플 데이터베이스를 사용합니다.

다음은 'Customers' table에서 선택한 항목입니다:

| CustomerID | CustomerName                       | ContactName    | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | -------------- | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Maria Anders   | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo   | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno | Mataderos 2312                | México D.F. | 05023      | Mexico  |



그리고 "Suppliers"테이블의 선택항목 입니다 :

| SupplierID | SupplierName               | ContactName      | Address        | City        | Postal Code | Country |
| ---------- | -------------------------- | ---------------- | -------------- | ----------- | ----------- | ------- |
| 1          | Exotic Liquid              | Charlotte Cooper | 49 Gilbert St. | Londona     | EC1 4SD     | UK      |
| 2          | New Orleans Cajun Delights | Shelley Burke    | P.O. Box 78934 | New Orleans | 70117       | USA     |
| 3          | Grandma Kelly's Homestead  | Regina Murphy    | 707 Oxford Rd. | Ann Arbor   | 48104       | USA     |



### SQL INSERT INTO SELECT Examples

---

다음 SQL 문은 "Suppliers"를 "Customers"로 복사합니다 (데이터가 채워지지 않은 열은 NULL을 포함합니다):



#### Example

```sql
INSERT INTO Customers (CustomerName, City, Country)
SELECT SupplierName, City, Country FROM Suppliers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

You have made changes to the database. Rows affected: 29

(데이터베이스를 변경했습니다. 영향을 받은 행 : 29)



다음 SQL 문은 "Suppliers"를 "Customers"로 복사합니다 (모든 열을 채움):



#### Example

```sql
INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country)
SELECT SupplierName, ContactName, Address, City, PostalCode, Country FROM Suppliers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

You have made changes to the database. Rows affected: 29

(데이터베이스를 변경했습니다. 영향을 받은 행 : 29)



다음 SQL 문은 독일 공급 업체만을 "Customers"로 복사합니다:



#### Example

```sql
INSERT INTO Customers (CustomerName, City, Country)
SELECT SupplierName, City, Country FROM Suppliers
WHERE Country='Germany';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

You have made changes to the database. Rows affected: 3

(데이터베이스를 변경했습니다. 영향을 받은 행 : 3)
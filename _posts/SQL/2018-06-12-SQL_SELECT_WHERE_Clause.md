---
layout: post
title: SQL WHERE Clause
category: SQL
tags:
  - SQL
  - SQL WHERE Clause
  - SQL WHERE 절
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.







## The SQL WHERE Clause

---



WHERE 절은 레코드를 필터링하는 데 사용됩니다.

WHERE 절은 지정된 조건을 충족하는 레코드 만 추출하는 데 사용됩니다.



### WHERE Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```



> 참고 : WHERE 절은 SELECT 문에서만 사용되는 것이 아니라 UPDATE, DELETE 문에서도 사용됩니다!





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







## WHERE Clause Example

---



다음 SQL 문은 "Customers"테이블에서 "Mexico"국가의 모든 고객을 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE Country='Mexico';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:

Number of Records: 5

| CustomerID | CustomerName                       | ContactName          | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | -------------------- | ----------------------------- | ----------- | ---------- | ------- |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo         | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno       | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 13         | Centro comercial Moctezuma         | Francisco Chang      | Sierras de Granada 9993       | México D.F. | 05022      | Mexico  |
| 58         | Pericles Comidas clásicas          | Guillermo Fernández  | Calle Dr. Jorge Cash 321      | México D.F. | 05033      | Mexico  |
| 80         | Tortuga Restaurante                | Miguel Angel Paolino | Avda. Azteca 123              | México D.F. | 05033      | Mexico  |







## Text Fields vs. Numeric Fields

---



SQL은 텍스트 값을 작은 따옴표로 묶어야합니다(대부분의 데이터베이스 시스템에서는 큰 따옴표도 사용할 수 있습니다).

그러나 숫자 필드는 따옴표로 묶지 않아야합니다:



### Example

```sql
SELECT * FROM Customers
WHERE Customer ID=1;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 1

| CustomerID | CustomerName        | ContactName  | Address       | City   | PostalCode | Country |
| ---------- | ------------------- | ------------ | ------------- | ------ | ---------- | ------- |
| 1          | Alfreds Futterkiste | Maria Anders | Obere Str. 57 | Berlin | 12209      | Germany |







## Operators in The WHERE Clause

---



다음 연산자는 WHERE 절에서 사용할 수 있습니다.

| Operator | Description                                                  |
| -------- | ------------------------------------------------------------ |
| =        | Equal(같다)                                                  |
| <>       | Not equal. **Note:** In some versions of SQL this operator may be written as != |
|          | (같지 않다. 참고:  일부 SQL 버전에서 이 연산자는 ! =로 쓰여질것이다.) |
| >        | Greater than(보다 큰)                                        |
| <        | Less than(보다 작은)                                         |
| >=       | Greater than or equal(크거나 같다)                           |
| <=       | Less than or equal(작거나 같다)                              |
| BETWEEN  | Between an inclusive range(포괄적 범위)                      |
| LIKE     | Search for a pattern(패턴 검색)                              |
| IN       | To specify multiple possible values for a column(열에 가능한 여러 값을 지정하려면) |

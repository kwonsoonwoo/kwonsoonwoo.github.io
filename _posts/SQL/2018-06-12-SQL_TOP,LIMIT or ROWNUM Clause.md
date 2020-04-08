---
layout: post
title: SQL TOP, LIMIT or ROWNUM Clause(티스토리 이전)
category: SQL
tags:
  - SQL
  - SQL TOP, LIMIT ROWNUM Clause
---



[여기로 이동](https://lifetutorial.tistory.com/37)

<!--

[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.







## The SQL SELECT TOP Clause

---



SELECT TOP 절은 리턴 할 레코드 수를 지정하는 데 사용됩니다.

SELECT TOP 절은 수천 개의 레코드가 있는 큰 테이블에서 유용합니다. 많은 수의 레코드를 반환하면 성능에 영향을 줄 수 있습니다.



> 참고 : 모든 데이터베이스 시스템이 SELECT TOP 절을 지원하는 것은 아닙니다. MySQL은 제한된 수의 레코드를 선택하기 위해 LIMIT 절을 지원하고 Oracle은 ROWNUM을 사용합니다.



**SQL Server / MS Access Syntax:**

```sql
SELECT TOP number|percent column_name(s)
FROM table_name
WHERE condition;
```



**MySQL Syntax:**

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;
```



**Oracle Syntax:**

```sql
SELECT column_name(s)
FROM table_name
WHERE ROWNUM <= number;
```







## Demo Database

---



다음은 Northwind 샘플 데이터베이스의 "Customers"테이블에서 선택한 것입니다:



| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ------------------ | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Maria Anders       | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |







## SQL TOP, LIMIT and ROWNUM Examples

---



다음 SQL 문은 "Customers"테이블에서 처음 세 개의 레코드를 선택합니다:



### Example

```sql
SELECT TOP 3 * FROM Customers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:

Number of Records: 3

| CustomerID | CustomerName                       | ContactName    | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | -------------- | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Maria Anders   | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo   | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno | Mataderos 2312                | México D.F. | 05023      | Mexico  |





다음 SQL 문은 LIMIT 절을 사용하는 동일한 예제를 보여줍니다:



### Example

```sql
SELECT * FROM Customers
LIMIT 3;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:

Number of Records: 3

| CustomerID | CustomerName                       | ContactName    | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | -------------- | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Maria Anders   | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo   | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno | Mataderos 2312                | México D.F. | 05023      | Mexico  |





다음 SQL 문은 ROWNUM을 사용하는 동일한 예제를 보여줍니다:



### Example

```sql
SELECT TOP 50 PERCENT * FROM Customers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:(일부만 발췌)

Number of Records: 46

| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ------------------ | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Maria Anders       | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |

**Customer ID 46번까지 있음**





## ADD a WHERE CLAUSE

---



다음 SQL 문은 "Customers"테이블에서 국가가 "Germany"인 처음 세 개의 레코드를 선택합니다.



### Example

```sql
SELECT TOP 3 * FROM Customers
WHERE Country='Germany';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:

Number of Records: 3

| CustomerID | CustomerName              | ContactName  | Address        | City     | PostalCode | Country |
| ---------- | ------------------------- | ------------ | -------------- | -------- | ---------- | ------- |
| 1          | Alfreds Futterkiste       | Maria Anders | Obere Str. 57  | Berlin   | 12209      | Germany |
| 6          | Blauer See Delikatessen   | Hanna Moos   | Forsterstr. 57 | Mannheim | 68306      | Germany |
| 17         | Drachenblut Delikatessend | Sven Ottlieb | Walserweg 21   | Aachen   | 52066      | Germany |





다음 SQL 문은 LIMIT 절을 사용하는 동일한 예제를 보여줍니다:



### Example

```sql
SELECT * FROM Customers
WHERE Country='Germany'
LIMIT 3;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:

Number of Records: 3

| CustomerID | CustomerName              | ContactName  | Address        | City     | PostalCode | Country |
| ---------- | ------------------------- | ------------ | -------------- | -------- | ---------- | ------- |
| 1          | Alfreds Futterkiste       | Maria Anders | Obere Str. 57  | Berlin   | 12209      | Germany |
| 6          | Blauer See Delikatessen   | Hanna Moos   | Forsterstr. 57 | Mannheim | 68306      | Germany |
| 17         | Drachenblut Delikatessend | Sven Ottlieb | Walserweg 21   | Aachen   | 52066      | Germany |







다음 SQL 문은 ROWNUM을 사용하는 동일한 예제를 보여줍니다.



### Example

```sql
SELECT * FROM Customers
WHERE Country='Germany' AND ROWNUM <= 3;
```

-->
---
layout: post
title: SQL UPDATE Statement
category: SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.






## The SQL UPDATE Statement

---



UPDATE 문은 테이블의 기존 레코드를 수정하는 데 사용됩니다.



#### UPDATE Syntax

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```



> 참고 : 테이블에서 레코드를 업데이트 할 때 주의하십시오! UPDATE 문에서 WHERE 절을 확인하십시오. WHERE 절은 업데이트 돼야하는 레코드를 지정합니다. WHERE 절을 생략하면 테이블의 모든 레코드가 업데이트됩니다!







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







## UPDATE Table

---



다음 SQL 문은 첫 번째 고객 (CustomerID = 1)을 새 담당자(ContactName) 및 새 도시(City)로 업데이트합니다.



### Example

```sql
UPDATE Customers
SET ContactName = 'Alfred Schmidt', City = 'Frankfurt'
WHERE CustomerID = 1;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

You have made changes to the database. Rows affected: 1

(데이터베이스를 변경했습니다. 영향을받은 행 : 1)





"Customers" 테이블의 선택은 다음과 같습니다:



| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ------------------ | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Alfred Schmidt     | Obere Str. 57                 | Frankfurt   | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |







## UPDATE Multiple Records

---



업데이트 될 레코드 수를 결정하는 것은 WHERE 절입니다.

다음 SQL 문은 country가 "Mexico"인 모든 레코드에 대해 연락처 이름(ContactName)을 "Juan"으로 업데이트합니다.



### Example

```sql
UPDATE Customers
SET ContactName = 'Juan'
WHERE Country = 'Mexico';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

You have made changes to the database. Rows affected: 5

(결과: 데이터베이스를 변경했습니다. 영향을받은 행 : 5)





"Customers" 테이블의 선택은 다음과 같습니다:



| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ------------------ | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Alfred Schmidt     | Obere Str. 57                 | Frankfurt   | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Juan               | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Juan               | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |







## Update Warning!

---


> 레코드를 업데이트 할 때는 주의하십시오. WHERE 절을 생략하면 모든 레코드가 업데이트됩니다!



### Example

```sql
UPDATE Customers
SET ContactName='Juan';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

You have made changes to the database. Rows affected: 94

(결과: 데이터베이스를 변경했습니다. 영향을 받은 행 : 94)





"Customers"테이블의 선택은 다음과 같습니다:



| CustomerID | CustomerName                       | ContactName | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ----------- | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Juan        | Obere Str. 57                 | Frankfurt   | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Juan        | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Juan        | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Juan        | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Juan        | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |

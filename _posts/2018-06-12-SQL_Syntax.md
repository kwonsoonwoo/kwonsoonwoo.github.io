---
layout: post
title: SQL Syntax
category: SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.







## Database Tables

---



데이터베이스는 대개 하나 이상의 테이블을 포함합니다. 각 표는 이름 (예 : '고객'또는 '주문')으로 식별됩니다. 테이블은 데이터가 있는 레코드 (행)를 포함합니다.

이 튜토리얼에서는 잘 알려진 Northwind 샘플 데이터베이스를 사용할겁니다. (MS Access 및 MS SQL Server에 포함되어 있는)

아래는 'Customers' table에서 선택한 항목입니다.



| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ------------------ | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Maria Anders       | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |



위의 table에는 다섯 개의 레코드 (각 고객 당 하나)와 일곱 개의 열 (CustomerID, CustomerName, ContactName, Address, City, PostalCode 및 Country)이 들어 있습니다.







## SQL Statements

---



데이터베이스에서 실행해야하는 대부분의 조치는 SQL 문으로 수행됩니다.

다음 SQL 문은 "Customers"테이블의 모든 레코드를 선택합니다.

###Example

```sql
SELECT * FROM Customers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것

이 튜토리얼에서는 다양한 SQL 문에 대해 설명합니다.







## Keep in Mind That...

---



- SQL 키워드는 대소문자를 구분하지 않습니다.  select는 SELECT와 같습니다.
- 이 튜토리얼에서는 모든 SQL 키워드를 대문자로 작성합니다.







## Semicolon after SQL Statements?

---



일부 데이터베이스 시스템에서는 각 SQL 문의 끝에 세미콜론이 필요합니다.

세미콜론은 데이터베이스 시스템에서 각 SQL 문을 분리하여 서버에 대한 동일한 호출에서 둘 이상의 SQL 문을 실행할 수 있도록 하는 표준 방법입니다.

이 튜토리얼에서는 각 SQL 문 끝에 세미콜론을 사용할겁니다.







## Some of The Most Important SQL Commands

---



- SELECT - 데이터베이스에서 데이터를 추출합니다.
- UPDATE - 데이터베이스의 데이터를 업데이트합니다.
- DELETE - 데이터베이스에서 데이터를 삭제합니다.
- INSERT INTO - 새로운 데이터를 데이터베이스에 삽입합니다.
- CREATE DATABASE - 새 데이터베이스를 만듭니다.
- ALTER DATABASE - 데이터베이스를 수정합니다.
- CREATE TABLE - 새 테이블을 만듭니다.
- ALTER TABLE - 테이블을 수정합니다.
- DROP TABLE - 테이블을 삭제합니다.
- CREATE INDEX - 색인 (검색 키)을 작성합니다.
- DROP INDEX - 색인을 삭제합니다.

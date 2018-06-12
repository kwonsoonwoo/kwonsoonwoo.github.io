---
layout: post
title: SQL DELETE Statement
category: SQL
---



####[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

####기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

####결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.







## The SQL DELETE Statement

---



DELETE 문은 테이블의 기존 레코드를 삭제하는 데 사용됩니다.



### DELETE Syntax

```sql
DELETE FROM table_name
WHERE condition;
```



> 참고 : 테이블에서 레코드를 삭제할 때 주의하십시오! DELETE 문의 WHERE 절을 확인하십시오. WHERE 절은 삭제될 레코드를 지정합니다. WHERE 절을 생략하면 테이블의 모든 레코드가 삭제됩니다!







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







## SQL DELETE Example

---



다음 SQL 문은 "Customers"테이블에서 고객 "Alfreds Futterkiste"를 삭제합니다:



### Example

```sql
DELETE FROM Customers
WHERE CustomerName='Alfreds Futterkiste';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

You have made changes to the database. Rows affected: 1

(데이터베이스를 변경했습니다. 영향을 받은 행 : 1)





"Customers" 테이블은 이제 다음과 같이 보입니다:



| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ------------------ | ----------------------------- | ----------- | ---------- | ------- |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |





## Delete All Records

---



테이블 삭제 없이 테이블삭의 모든 행을 삭제할 수 있습니다. 이는 테이블 구조, 속성 및 인덱스가 손상되지 않는다는 것을 의미합니다.



```sql
DELETE FROM table_name;
```



또는:



```sql
DELETE * FROM table_name;
```


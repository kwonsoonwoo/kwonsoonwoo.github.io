---
layout: post
title: SQL SELECT DISTINCT Statement
category: SQL
---



####[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

####기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

####결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.







## The SQL SELECT DISTINCT Statement

---



테이블 내에서 열은 종종 많은 중복 값을 포함합니다. 그래서 개발자는 때론 서로 다른 (뚜렷한) 값만 나열하고 싶어합니다.

SELECT DISTINCT 문은 고유한 (다른) 값만 리턴하는 데 사용됩니다.



#### SELECT DISTINCT Syntax

```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
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







## SELECT Example

---



다음 SQL 문은 Customers 테이블의 "Country"열에있는 모든 (중복 된) 값을 선택합니다.



### Example

```sql
SELECT Country FROM Customers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



이제 DISTINCT 키워드를 위의 SELECT 문과 함께 사용하여 결과를 봅시다.



```sql
SELECT DISTINCT Country FROM Customers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:

Number of Records: 21

| Country     |
| ----------- |
| Germany     |
| Mexico      |
| UK          |
| Sweden      |
| France      |
| Spain       |
| Canada      |
| Argentina   |
| Switzerland |
| Brazil      |
| Austria     |
| Italy       |
| Portugal    |
| USA         |
| Venezuela   |
| Ireland     |
| Belgium     |
| Norway      |
| Denmark     |
| Finland     |
| Poland      |







## SELECT DISTINCT Examples

---



다음 SQL 문은 Customers 테이블의 "Country"열에서 DISTINCT 값만 선택합니다.



### Example

```sql
SELECT DISTINCT Country FROM Customers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 21

| Country     |
| ----------- |
| Germany     |
| Mexico      |
| UK          |
| Sweden      |
| France      |
| Spain       |
| Canada      |
| Argentina   |
| Switzerland |
| Brazil      |
| Austria     |
| Italy       |
| Portugal    |
| USA         |
| Venezuela   |
| Ireland     |
| Belgium     |
| Norway      |
| Denmark     |
| Finland     |
| Poland      |





다음 SQL 문은 서로 다른 (별개의) 고객 국가의 수를 나열합니다.



### Example

```sql
SELECT COUNT(DISTINCT Country) FROM Customers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 1

| COUNT(DISTINCT Country) |
| ----------------------- |
| 21                      |



> 참고 : 위의 예는 Firefox 및 Microsoft Edge에서 작동하지 않습니다! COUNT (DISTINCT column_name)는 Microsoft Access 데이터베이스에서 지원되지 않으므로 Firefox와 Microsoft Edge는 예제에서 Microsoft Access를 사용하고 있습니다.



다음은 MS Access의 해결 방법입니다.

### Example

```sql
SELECT Count(*) AS DistinctCountries
FROM (SELECT DISTINCT Country FROM Customers);
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



결과 값은 위의  Result:와 같습니다.
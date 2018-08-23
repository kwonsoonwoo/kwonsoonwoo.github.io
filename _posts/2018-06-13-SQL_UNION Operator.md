---
layout: post
title: SQL UNION Operator
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





### The SQL UNION Operator

---

UNION 연산자는 두 개 이상의 SELECT 문의 결과 집합을 결합하는 데 사용됩니다.

- UNION 내의 각 SELECT 문은 같은 수의 열을 가져야합니다.
- 열은 유사한 데이터 형식을 가져야합니다.
- 각 SELECT 문의 열은 같은 순서로 있어야합니다



####UNION Syntax

```sql
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```



#### UNION ALL Syntax

UNION 연산자는 기본적으로 고유 값만 선택합니다. 중복 값을 허용하려면 UNION ALL을 사용하십시오.

```sql
SELECT column_name(s) FROM table1
UNION ALL
SELECT column_name(s) FROM table2;
```

**참고** : 결과 집합의 열 이름은 일반적으로 UNION의 첫 번째 SELECT 문의 열 이름과 동일합니다.



### Demo Database

---

이 튜토리얼에서는 잘 알려진 Northwind 샘플 데이터베이스를 사용합니다.

다음은 "Customers" 테이블에서 선택한 항목입니다:

| CustomerID | CustomerName                       | ContactName    | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | -------------- | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Maria Anders   | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo   | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno | Mataderos 2312                | México D.F. | 05023      | Mexico  |



그리고 "Suppliers"테이블에서 선택한 항목입니다:

| SupplierID | SupplierName               | ContactName      | Address        | City        | PostalCode | Country |
| ---------- | -------------------------- | ---------------- | -------------- | ----------- | ---------- | ------- |
| 1          | Exotic Liquid              | Charlotte Cooper | 49 Gilbert St. | London      | EC1 4SD    | UK      |
| 2          | New Orleans Cajun Delights | Shelley Burke    | P.O. Box 78934 | New Orleans | 70117      | USA     |
| 3          | Grandma Kelly's Homestead  | Regina Murphy    | 707 Oxford Rd. | Ann Arbor   | 48104      | USA     |



### SQL UNION Example

---

다음 SQL 문은 "Customers"및 "Suppliers"에서 나온 다른 모든 도시 (고유 한 값만)를 선택합니다.



#### Example

```sql
SELECT City FROM Customers
UNION
SELECT City FROM Suppliers
ORDER By City;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것

**참고** : 일부 고객 또는 공급 업체가 동일한 도시를 가지고있는 경우, UNION은 고유 한 값만 선택하기 때문에 각 도시는 한 번만 나열됩니다. UNION ALL을 사용하여 중복 값을 선택하십시오!



### Result:(일부만 발췌)

Number of Records: 95

| City         |
| ------------ |
| Aachen       |
| Albuquerque  |
| Anchorage    |
| Ann Arbor    |
| Annecy       |
| Barcelona    |
| Barquisimeto |
| Bend         |
| Bergamo      |
| Berlin       |
| Bern         |
| Boise        |

**총 95개의 Record가 있음**



### SQL UNION ALL Example

---

다음 SQL 문은 "Customers" 와 "Suppliers"에서 모든 도시 (중복 값 포함)를 선택합니다.



#### Example

```sql
SELECT City FROM Customers
UNION ALL
SELECT City FROM Suppliers
ORDER BY City;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:(일부만 발췌)

Number of Records: 122

| City         |
| ------------ |
| Aachen       |
| Albuquerque  |
| Anchorage    |
| Ann Arbor    |
| Annecy       |
| Barcelona    |
| Barquisimeto |
| Bend         |
| Bergamo      |
| Berlin       |
| Bern         |

**총 122개의 Record가 있음**



### SQL UNION With WHERE

---

다음 SQL 문은 "Customers" 와 "Suppliers"에서 독일내에 있는 모든 다른 도시 (유일한 값만)를 선택합니다.



#### Example

```sql
SELECT City, Country FROM Customers
WHERE Country='Germany'
UNION
SELECT City, Country FROM Suppliers
WHERE Country='Germany'
ORDER BY City;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 13

| City           | Country |
| -------------- | ------- |
| Aachen         | Germany |
| Berlin         | Germany |
| Brandenburg    | Germany |
| Cunewalde      | Germany |
| Cuxhaven       | Germany |
| Frankfurt      | Germany |
| Frankfurt a.M. | Germany |
| Köln           | Germany |
| Leipzig        | Germany |
| Mannheim       | Germany |
| München        | Germany |
| Münster        | Germany |
| Stuttgart      | Germany |



### SQL UNION ALL With WHERE

---

다음 SQL 문은 "Customers" 와 "Suppliers"에서 독일의 모든 도시 (중복 값 포함)를 선택합니다.



#### Example

```sql
SELECT City, Country FROM Customers
WHERE Country='Germany'
UNION ALL
SELECT City, Country FROM Suppliers
WHERE Country='Germany'
ORDER BY City;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 13

| City           | Country |
| -------------- | ------- |
| Aachen         | Germany |
| Berlin         | Germany |
| Brandenburg    | Germany |
| Cunewalde      | Germany |
| Cuxhaven       | Germany |
| Frankfurt      | Germany |
| Frankfurt a.M. | Germany |
| Köln           | Germany |
| Leipzig        | Germany |
| Mannheim       | Germany |
| München        | Germany |
| Münster        | Germany |
| Stuttgart      | Germany |



### Another UNION Example

---

다음 SQL 문은 모든 customers와 suppliers를 나열합니다:



#### Examples

```sql
SELECT 'Customer' As Type, ContactName, City, Country
FROM Customers
UNION
SELECT 'Supplier', ContactName, City, Country
FROM Suppliers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:(일부만 발췌)

Number of Records: 98

| Type     | ContactName | City         | Country     |
| -------- | ----------- | ------------ | ----------- |
| Customer | Juan        | Aachen       | Germany     |
| Customer | Juan        | Albuquerque  | USA         |
| Customer | Juan        | Anchorage    | USA         |
| Customer | Juan        | Barcelona    | Spain       |
| Customer | Juan        | Barquisimeto | Venezuela   |
| Customer | Juan        | Bergamo      | Italy       |
| Customer | Juan        | Bern         | Switzerland |
| Customer | Juan        | Boise        | USA         |
| Customer | Juan        | Brandenburg  | Germany     |
| Customer | Juan        | Bruxelles    | Belgium     |

**총 98개의 Record가 있음**


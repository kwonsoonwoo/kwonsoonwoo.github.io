---
layout: post
title: SQL EXISTS Operator
category: SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.



### The SQL EXISTS Operator

---

EXISTS 연산자는 하위 쿼리에 레코드가 있는지 테스트하는 데 사용됩니다.

 EXISTS 연산자는 하위 쿼리가 하나 이상의 레코드를 반환하면 true를 반환합니다.



#### EXISTS Syntax

```sql
SELECT column_name(s)
FROM table_name
WHERE EXISTS
(SELECT column_name FROM table_name WHERE condition);
```

---



### Demo Database

---

다음은 Northwind 샘플 데이터베이스의 "Products"테이블에서 선택한 것입니다:

| ProductID | ProductName                  | SupplierID | CategoryID | Unit                | Price |
| --------- | ---------------------------- | ---------- | ---------- | ------------------- | ----- |
| 1         | Chais                        | 1          | 1          | 10 boxes x 20 bags  | 18    |
| 2         | Chang                        | 1          | 1          | 24 - 12 oz bottles  | 19    |
| 3         | Aniseed Syrup                | 1          | 2          | 12 - 550 ml bottles | 10    |
| 4         | Chef Anton's Cajun Seasoning | 2          | 2          | 48 - 6 oz jars      | 22    |
| 5         | Chef Anton's Gumbo Mix       | 2          | 2          | 36 boxes            | 21.35 |



그리고 "Suppliers"테이블의 선택항목 입니다 :



| SupplierID | SupplierName               | ContactName      | Address                   | City        | PostalCode | Country |
| ---------- | -------------------------- | ---------------- | ------------------------- | ----------- | ---------- | ------- |
| 1          | Exotic Liquid              | Charlotte Cooper | 49 Gilbert St.            | London      | EC1 4SD    | UK      |
| 2          | New Orleans Cajun Delights | Shelley Burke    | P.O. Box 78934            | New Orleans | 70117      | USA     |
| 3          | Grandma Kelly's Homestead  | Regina Murphy    | 707 Oxford Rd.            | Ann Arbor   | 48104      | USA     |
| 4          | Tokyo Traders              | Yoshi Nagase     | 9-8 Sekimai Musashino-shi | Tokyo       | 100        | Japan   |

---



### SQL EXISTS Examples

---

다음 SQL 문은 TRUE를 반환하고 제품 가격이 20 미만인 공급 업체를 나열합니다:



#### Example

```sql
SELECT SupplierName
FROM Suppliers
WHERE EXISTS (SELECT ProductName FROM Products WHERE supplierId =
Suppliers.supplierId AND Price < 20);
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 24

| SupplierName                      |
| --------------------------------- |
| Exotic Liquid                     |
| New Orleans Cajun Delights        |
| Tokyo Traders                     |
| Mayumi's                          |
| Pavlova, Ltd.                     |
| Specialty Biscuits, Ltd.          |
| PB Knäckebröd AB                  |
| Refrescos Americanas LTDA         |
| Heli Süßwaren GmbH & Co. KG       |
| Plutzer Lebensmittelgroßmärkte AG |
| Formaggi Fortini s.r.l.           |
| Norske Meierier                   |
| Bigfoot Breweries                 |
| Svensk Sjöföda AB                 |
| Aux joyeux ecclésiastiques        |
| New England Seafood Cannery       |
| Leka Trading                      |
| Lyngbysild                        |
| Zaanse Snoepfabriek               |
| Karkki Oy                         |
| G'day, Mate                       |
| Ma Maison                         |
| Pasta Buttini s.r.l.              |
| Escargots Nouveaux                |



다음 SQL 문은 TRUE를 반환하고 제품 가격이 22 인 공급 업체를 나열합니다:



#### Example

```sql
SELECT SupplierName
FROM Suppliers
WHERE EXISTS (SELECT ProductName FROM Products WHERE SupplierId = 
Suppliers.supplierId AND Price = 22);
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 1

| SupplierName               |
| -------------------------- |
| New Orleans Cajun Delights |


---
layout: post
title: SQL BETWEEN Operator
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





###The SQL BETWEEN Operator

---



BETWEEN 연산자는 주어진 범위 내의 값을 선택합니다. 값은 숫자, 텍스트 또는 날짜 일 수 있습니다.

BETWEEN 연산자는 다음을 포함합니다: 시작과 끝 값이 포함됩니다.



#### BETWEEN Syntax

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```



###Demo Database

---



다음은 Northwind 샘플 데이터베이스의 "Products" 테이블에서 선택한 것입니다:



| ProductID | ProductName                  | SupplierID | CategoryID | Unit                | Price |
| --------- | ---------------------------- | ---------- | ---------- | ------------------- | ----- |
| 1         | Chais                        | 1          | 1          | 10 boxes x 20 bags  | 18    |
| 2         | Chang                        | 1          | 1          | 24 - 12 oz bottles  | 19    |
| 3         | Aniseed Syrup                | 1          | 2          | 12 - 550 ml bottles | 10    |
| 4         | Chef Anton's Cajun Seasoning | 1          | 2          | 48 - 6 oz jars      | 22    |
| 5         | Chef Anton's Gumbo Mix       | 1          | 2          | 36 boxes            | 21.35 |



### BETWEEN Example

---



다음 SQL 문은 가격이 10과 20 사이인 모든 제품을 선택합니다.:



### Example

```sql
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:(일부만 발췌)

Number of Records: 29

| ProductID | ProductName             | SupplierID | CategoryID | Unit                | Price |
| --------- | ----------------------- | ---------- | ---------- | ------------------- | ----- |
| 1         | Chais                   | 1          | 1          | 10 boxes x 20 bags  | 18    |
| 2         | Chang                   | 1          | 1          | 24 - 12 oz bottles  | 19    |
| 3         | Aniseed Syrup           | 1          | 2          | 12 - 550 ml bottles | 10    |
| 15        | Genen Shouyu            | 6          | 2          | 24 - 250 ml bottles | 15.5  |
| 16        | Pavlova                 | 7          | 3          | 32 - 500 g boxes    | 17.45 |
| 21        | Sir Rodney's Scones     | 8          | 3          | 24 pkgs. x 4 pieces | 10    |
| 25        | NuNuCa Nuß-Nougat-Creme | 11         | 3          | 20 - 450 g glasses  | 14    |
| 31        | Gorgonzola Telino       | 14         | 4          | 12 - 100 g pkgs     | 12.5  |
| 34        | Sasquatch Ale           | 16         | 1          | 24 - 12 oz bottles  | 14    |
| 35        | Steeleye Stout          | 16         | 1          | 24 - 12 oz bottles  | 18    |
| 36        | Inlagd Sill             | 17         | 8          | 24 - 250 g jars     | 19    |

**총 29개의 Record가 있음**



###NOT BETWEEN Example

---



앞의 예제 범위를 벗어난 제품을 표시하려면 NOT BETWEEN을 사용합니다:



### Example

```sql
SELECT * FROM Products
WHERE Price NOT BETWEEN 10 AND 20;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:(일부만 발췌)

Number of Records: 48

| ProductID | ProductName                     | SupplierID | CategoryID | Unit             | Price |
| --------- | ------------------------------- | ---------- | ---------- | ---------------- | ----- |
| 4         | Chef Anton's Cajun Seasoning    | 2          | 2          | 48 - 6 oz jars   | 22    |
| 5         | Chef Anton's Gumbo Mix          | 2          | 2          | 36 boxes         | 21.35 |
| 6         | Grandma's Boysenberry Spread    | 3          | 2          | 12 - 8 oz jars   | 25    |
| 7         | Uncle Bob's Organic Dried Pears | 3          | 7          | 12 - 1 lb pkgs.  | 30    |
| 8         | Northwoods Cranberry Sauce      | 3          | 2          | 12 - 12 oz jars  | 40    |
| 9         | Mishi Kobe Niku                 | 4          | 6          | 18 - 500 g pkgs. | 97    |
| 10        | Ikura                           | 4          | 8          | 12 - 200 ml jars | 31    |
| 11        | Queso Cabrales                  | 5          | 4          | 1 kg pkg.        | 21    |
| 12        | Queso Manchego La Pastora       | 5          | 4          | 10 - 500 g pkgs. | 38    |
| 13        | Konbu                           | 6          | 8          | 2 kg box         | 6     |
| 14        | Tofu                            | 6          | 7          | 40 - 100 g pkgs. | 23.25 |

**총 48개의 Record가 있음**



### BETWEEN with IN Example

---



다음 SQL 문은 가격이 10과 20 사이 인 모든 제품을 선택합니다. 그중에; CategoryID가 1,2 또는 3 인 제품은 표시하지 않습니다.

 

### Example

```sql
SELECT * FROM Products
WHERE (Price BETWEEN 10 AND 20)
AND NOT CategoryID IN (1,2,3);
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 9

| ProductID | ProductName                   | SupplierID | CategoryID | Unit              | Price |
| --------- | ----------------------------- | ---------- | ---------- | ----------------- | ----- |
| 31        | Gorgonzola Telino             | 14         | 4          | 12 - 100 g pkgs   | 12.5  |
| 36        | Inlagd Sill                   | 17         | 8          | 24 - 250 g jars   | 19    |
| 40        | Boston Crab Meat              | 19         | 8          | 24 - 4 oz tins    | 18.4  |
| 42        | Singaporean Hokkien Fried Mee | 20         | 5          | 32 - 1 kg pkgs.   | 14    |
| 46        | Spegesild                     | 21         | 8          | 4 - 450 g glasses | 12    |
| 57        | Ravioli Angelo                | 26         | 5          | 24 - 250 g pkgs.  | 19.5  |
| 58        | Escargots de Bourgogne        | 27         | 8          | 24 pieces         | 13.25 |
| 73        | Röd Kaviar                    | 17         | 8          | 24 - 150 g jars   | 15    |
| 74        | Longlife Tofu                 | 4          | 7          | 5 kg pkg.         | 10    |



### BETWEEN Text Values Example

---



아래 SQL 문은 'Carnarvon Tigers'와 'Mozzarella di Giovanni'사이에 ProductName이 있는 모든 제품을 선택합니다.



### Example

```sql
SELECT * FROM Products
WHERE ProductName BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:(일부만 발췌)

Number of Records: 37

| ProductID | ProductName                  | SupplierID | CategoryID | Unit               | Price |
| --------- | ---------------------------- | ---------- | ---------- | ------------------ | ----- |
| 18        | Carnarvon Tigers             | 7          | 8          | 16 kg pkg.         | 62.5  |
| 1         | Chais                        | 1          | 1          | 10 boxes x 20 bags | 18    |
| 2         | Chang                        | 1          | 1          | 24 - 12 oz bottles | 19    |
| 39        | Chartreuse verte             | 18         | 1          | 750 cc per bottle  | 18    |
| 4         | Chef Anton's Cajun Seasoning | 2          | 2          | 48 - 6 oz jars     | 22    |
| 5         | Chef Anton's Gumbo Mix       | 2          | 2          | 36 boxes           | 21.35 |
| 48        | Chocolade                    | 22         | 3          | 10 pkgs.           | 12.75 |
| 38        | Côte de Blaye                | 18         | 1          | 12 - 75 cl bottles | 263.5 |
| 58        | Escargots de Bourgogne       | 27         | 8          | 24 pieces          | 13.25 |
| 52        | Filo Mix                     | 24         | 5          | 16 - 2 kg boxes    | 7     |

**총 37개의 Record가 있음**



### NOT BETWEEN Text Values Example

---



아래 SQL 문은 'Carnarvon Tigers' 및 'Mozzarella di Giovanni'사이에 ProductName이 없는 모든 제품을 선택합니다.



### Example

```sql
SELECT * FROM Products
WHERE ProductName NOT BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:(일부만 발췌)

Number of Records: 40

| ProductID | ProductName                     | SupplierID | CategoryID | Unit                | Price |
| --------- | ------------------------------- | ---------- | ---------- | ------------------- | ----- |
| 17        | Alice Mutton                    | 7          | 6          | 20 - 1 kg tins      | 39    |
| 3         | Aniseed Syrup                   | 1          | 2          | 12 - 550 ml bottles | 10    |
| 40        | Boston Crab Meat                | 19         | 8          | 24 - 4 oz tins      | 18.4  |
| 60        | Camembert Pierrot               | 28         | 4          | 15 - 300 g rounds   | 34    |
| 30        | Nord-Ost Matjeshering           | 13         | 8          | 10 - 200 g glasses  | 25.89 |
| 8         | Northwoods Cranberry Sauce      | 3          | 2          | 12 - 12 oz jars     | 40    |
| 25        | NuNuCa Nuß-Nougat-Creme         | 11         | 3          | 20 - 450 g glasses  | 14    |
| 77        | Original Frankfurter grüne Soße | 12         | 2          | 12 boxes            | 13    |
| 70        | Outback Lager                   | 7          | 1          | 24 - 355 ml bottles | 15    |
| 16        | Pavlova                         | 7          | 3          | 32 - 500 g boxes    | 17.45 |
| 53        | Perth Pasties                   | 24         | 6          | 48 pieces           | 32.8  |

**총 40개의 Record가 있음**



### Sample Table

---

아래는 Northwind 샘플 데이터베이스의 "Orders"테이블에서 선택한 것입니다:

| OrderID | CustomerID | EmployeeID | OrderDate | ShipperID |
| ------- | ---------- | ---------- | --------- | --------- |
| 10248   | 90         | 5          | 7/4/1996  | 3         |
| 10249   | 81         | 6          | 7/5/1996  | 1         |
| 10250   | 34         | 4          | 7/8/1996  | 2         |
| 10251   | 84         | 3          | 7/9/1996  | 1         |
| 10252   | 76         | 4          | 7/10/1996 | 2         |



### BETWEEN Dates Example

---

다음 SQL 문은 OrderDate가  '04 -July-1996 '및 '09-July-1996' 사이에 있는 모든 주문을 선택합니다.



### Example

```sql
SELECT * FROM Orders
WHERE OrderDate BETWEEN #07/04/1996# AND #07/09/1996#;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 5

| OrderID | CustomerID | EmployeeID | OrderDate | ShipperID |
| ------- | ---------- | ---------- | --------- | --------- |
| 10248   | 90         | 5          | 7/4/1996  | 3         |
| 10249   | 81         | 6          | 7/5/1996  | 1         |
| 10250   | 34         | 4          | 7/8/1996  | 2         |
| 10251   | 84         | 3          | 7/8/1996  | 1         |
| 10252   | 76         | 4          | 7/9/1996  | 2         |
---
layout: post
title: SQL COUNT(), AVG() and SUM() Functions
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





###The SQL COUNT(), AVG() and SUM() Functions

---



COUNT () 함수는 지정된 기준과 일치하는 행 수를 반환합니다.

AVG () 함수는 숫자 열의 평균값을 반환합니다.

SUM () 함수는 숫자 열의 총 합계를 반환합니다.




#### COUNT() Syntax

```sql
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```



#### AVG() Syntax

```sql
SELECT AVG(column_name)
FROM table_name
WHERE condition;
```



#### SUM() Syntax

```sql
SELECT SUM(column_name)
FROM table_name
WHERE condition;
```





###Demo Database

---



다음은 Northwind 샘플 데이터베이스의 "Products"테이블에서 선택한 것입니다:



| ProductID | ProductName                  | SupplierID | CategoryID | Unit                | Price |
| --------- | ---------------------------- | ---------- | ---------- | ------------------- | ----- |
| 1         | Chais                        | 1          | 1          | 10 boxes x 20 bags  | 18    |
| 2         | Chang                        | 1          | 1          | 24 - 12 oz bottles  | 19    |
| 3         | Aniseed Syrup                | 1          | 2          | 12 - 550 ml bottles | 10    |
| 4         | Chef Anton's Cajun Seasoning | 2          | 2          | 48 - 6 oz jars      | 22    |
| 5         | Chef Anton's Gumbo Mix       | 2          | 2          | 36 boxes            | 21.35 |





### COUNT() Example

---



다음 SQL 문은 제품 수를 찾습니다.



### Example

```sql
SELECT COUNT(ProductID)
FROM Products;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 1

| COUNT(ProductID) |
| ---------------- |
| 77               |





### AVG() Example

---



다음 SQL 문은 모든 제품의 평균 가격을 찾습니다.



### Example

```sql
SELECT AVG(Price)
FROM Products;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 1

| AVG(Price)         |
| ------------------ |
| 28.866363636363637 |



### Demo Database

------



아래는 Northwind 샘플 데이터베이스의 "OrderDetails"표에서 선택한 항목입니다:



| OrderDetailID | OrderID | ProductID | Quantity |
| ------------- | ------- | --------- | -------- |
| 1             | 10248   | 11        | 12       |
| 2             | 10248   | 42        | 10       |
| 3             | 10248   | 72        | 5        |
| 4             | 10249   | 14        | 9        |
| 5             | 10249   | 51        | 40       |



### SUM() Example

------



 다음 SQL 문은 OrderDetails 테이블의 "Quantity"필드의 합계를 찾습니다.



### Example

```sql
SELECT SUM(Quantity)
FROM OrderDetails;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 1

| SUM(Quantity) |
| ------------- |
| 12743         |


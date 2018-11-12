---
layout: post
title: SQL MIN() and MAX() Functions
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.






###The SQL MIN() and MAX() Functions

---



MIN () 함수는 선택된 컬럼의 가장 작은 값을 리턴합니다.

MAX () 함수는 선택된 열의 가장 큰 값을 반환합니다.




#### MIN() Syntax

```sql
SELECT MIN(column_name)
FROM table_name
WHERE condition;
```



#### MAX() Syntax

```sql
SELECT MAX(column_name)
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





### MIN() Example

---



 다음 SQL 문은 가장 저렴한 제품의 가격을 찾습니다.



### Example

```sql
SELECT MIN(Price) AS SmallestPrice
FROM Products;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 1

| SmallestPrice |
| ------------- |
| 2.5           |





### MAX() Example

---



 다음 SQL 문은 가장 비싼 제품의 가격을 찾습니다.



### Example

```sql
SELECT MAX(Price) AS LargestPrice
FROM Products;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 1

| LargestPrice |
| ------------ |
| 263.5        |



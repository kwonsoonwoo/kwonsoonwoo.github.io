---
layout: post
title: The SQL INSERT INTO Statement
category: SQL
tags:
  - SQL
  - SQL INSERT INTO Statement
  - SQL INSERT INTO 문
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.







## The SQL INSERT INTO Statement

---



INSERT INTO 문은 테이블에 새 레코드를 삽입하는 데 사용됩니다.





### INSERT INTO Syntax

두 가지 방법으로 INSERT INTO 문을 작성할 수 있습니다.

첫 번째 방법은 삽입 할 열 이름과 값을 모두 지정하는 것입니다.

```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```



표의 모든 열에 값을 추가하는 경우 SQL 조회에서 열 이름을 지정할 필요가 없습니다. 그러나 값의 순서가 표의 열과 동일한 순서인지 확인하십시오. INSERT INTO 구문은 다음과 같습니다:

```sql
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```







## Demo Database

---



다음은 Northwind 샘플 데이터베이스의 "Customers"테이블에서 선택한 것입니다.



| CustomerID | CustomerName         | ContactName     | Address                     | City     | PostalCode | Country |
| ---------- | -------------------- | --------------- | --------------------------- | -------- | ---------- | ------- |
| 89         | White Clover Markets | Karl Jablonski  | 305 - 14th Ave. S. Suite 3B | Seattle  | 98128      | USA     |
| 90         | Wilman Kala          | Matti Karttunen | Keskuskatu 45               | Helsinki | 21240      | Finland |
| 91         | Wolski               | Zbyszek         | ul. Filtrowa 68             | Walla    | 01-012     | Poland  |





## INSERT INTO Example

---



다음 SQL 문은 "Customers"테이블에 새 레코드를 삽입합니다:



### Example

```sql
INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country)
VALUES ('Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway');
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:

You have made changes to the database. Rows affected: 1

(데이터베이스를 변경했습니다. 영향을받은 행 : 1)





"Customers"테이블의 선택은 다음과 같습니다.



| CustomerID | CustomerName         | ContactName     | Address                     | City      | PostalCode | Country |
| ---------- | -------------------- | --------------- | --------------------------- | --------- | ---------- | ------- |
| 89         | White Clover Markets | Karl Jablonski  | 305 - 14th Ave. S. Suite 3B | Seattle   | 98128      | USA     |
| 90         | Wilman Kala          | Matti Karttunen | Keskuskatu 45               | Helsinki  | 21240      | Finland |
| 91         | Wolski               | Zbyszek         | ul. Filtrowa 68             | Walla     | 01-012     | Poland  |
| 92         | Cardinal             | Tom B. Erichsen | Skagen 21                   | Stavanger | 4006       | Norway  |

> CustomerID 필드에 숫자를 삽입하지 않았다는 것을 알았습니까?
>
> CustomerID 열은 자동 증가 필드이며 새 레코드가 테이블에 삽입 될 때 자동으로 생성됩니다.







## Insert Data Only in Specified Columns

---



특정 열에 만 데이터를 삽입 할 수도 있습니다.

다음 SQL 문은 새 레코드를 삽입하지만 "CustomerName", "City"및 "Country"열 에만 데이터를 삽입합니다.(CustomerID는 자동으로 업데이트됩니다).



### Example

```sql
INSERT INTO Customers (CustomerName, City, Country)
VALUES ('Cardinal', 'Stavanger', 'Norway');
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

You have made changes to the database. Rows affected: 1

(데이터베이스를 변경했습니다. 영향을받은 행 : 1)



"Customers"테이블의 선택은 다음과 같습니다.



| CustomerID | CustomerName         | ContactName     | Address                     | City      | PostalCode | Country |
| ---------- | -------------------- | --------------- | --------------------------- | --------- | ---------- | ------- |
| 89         | White Clover Markets | Karl Jablonski  | 305 - 14th Ave. S. Suite 3B | Seattle   | 98128      | USA     |
| 90         | Wilman Kala          | Matti Karttunen | Keskuskatu 45               | Helsinki  | 21240      | Finland |
| 91         | Wolski               | Zbyszek         | ul. Filtrowa 68             | Walla     | 01-012     | Poland  |
| 92         | Cardinal             | null            | null                        | Stavanger | null       | Norway  |

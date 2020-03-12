---
layout: post
title: SQL Aliases
category: SQL
tags:
  - SQL
  - Alias
  - Aliases
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





### SQL Aliases

---



SQL Aliases는 테이블 또는 테이블의 열에 임시 이름을 지정하는 데 사용됩니다.

앨리어스 (alias)는 컬럼 이름을 읽기 쉽게하기 위해 자주 사용됩니다.

별명은 조회 기간 동안 만 존재합니다.



#### Alias Column Syntax

```sql
SELECT column_name AS alias_name
FROM table_name;
```



#### Alias Table Syntax

```sql
SELECT column_name(s)
FROM table_name AS alias_name;
```





### Demo Database

---



이 튜토리얼에서는 잘 알려진 Northwind 샘플 데이터베이스를 사용합니다. 

다음은 'Customers' 테이블에서 선택한 항목입니다:



| CustomerID | CustomerName                       | ContactName    | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | -------------- | ----------------------------- | ----------- | ---------- | ------- |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo   | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy   | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |



"Orders" 테이블에서의 선택 항목:

| OrderID | CustomerID | EmployeeID | OrderDate  | ShipperID |
| ------- | ---------- | ---------- | ---------- | --------- |
| 10354   | 58         | 8          | 1996-11-14 | 3         |
| 10355   | 4          | 6          | 1996-11-15 | 1         |
| 10356   | 86         | 6          | 1996-11-18 | 2         |



### Alias for Columns Examples

---



다음 SQL 문은 CustomerID 열과 CustomerName 열의 두 가지 별칭을 만듭니다:



### Example

```sql
SELECT CustomerID as ID, CustomerName AS Customer
FROM Customers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:(일부만 발췌)

Number of Records: 93

| ID   | Customer                           |
| ---- | ---------------------------------- |
| 2    | Ana Trujillo Emparedados y helados |
| 3    | Antonio Moreno Taquería            |
| 4    | Around the Horn                    |
| 5    | Berglunds snabbköp                 |
| 6    | Blauer See Delikatessen            |
| 7    | Blondel père et fils               |
| 8    | Bólido Comidas preparadas          |
| 9    | Bon app'                           |
| 10   | Bottom-Dollar Marketse             |
| 11   | B's Beverages                      |
| 12   | Cactus Comidas para llevar         |

**총 93개의 Record가 있음**



다음 SQL 문은 CustomerName 열과 ContactName 열의 두 가지 별칭을 만듭니다. 

**참고 :** 별칭 이름에 공백이 포함되어 있으면 큰 따옴표 또는 대괄호가 필요합니다.



### Example

```sql
SELECT CustomerName AS Customer, ContactName AS [Contact Person]
FROM Customers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:(일부만 발췌)

Number of Records: 93

| Customer                           | Contact Person |
| ---------------------------------- | -------------- |
| Ana Trujillo Emparedados y helados | Juan           |
| Antonio Moreno Taquería            | Juan           |
| Around the Horn                    | Juan           |
| Berglunds snabbköp                 | Juan           |
| Blauer See Delikatessen            | Juan           |
| Blondel père et fils               | Juan           |
| Bólido Comidas preparadas          | Juan           |
| Bon app'                           | Juan           |
| Bottom-Dollar Marketse             | Juan           |
| B's Beverages                      | Juan           |
| Cactus Comidas para llevar         | Juan           |

**총 93개의 Record가 있음**



다음 SQL 문은 네 개의 열 (Address, PostalCode, City 및 Country)을 결합하는 "Address"라는 별칭을 만듭니다.



### Example

```sql
SELECT CustomerName, Address + ', ' + PostalCode + ' ' + City + ', ' + Country AS Address
FROM Customers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:(일부만 발췌)

Number of Records: 91

| CustomerName                       | Address                                                  |
| ---------------------------------- | -------------------------------------------------------- |
| Alfreds Futterkiste                | Obere Str. 57, 12209 Berlin, Germany                     |
| Ana Trujillo Emparedados y helados | Avda. de la Constitución 2222, 05021 México D.F., Mexico |
| Antonio Moreno Taquería            | Mataderos 2312, 05023 México D.F., Mexico                |
| Around the Horn                    | 120 Hanover Sq., WA1 1DP London, UK                      |
| Berglunds snabbköp                 | Berguvsvägen 8, S-958 22 Luleå, Sweden                   |
| Blauer See Delikatessen            | Forsterstr. 57, 68306 Mannheim, Germany                  |
| Blondel père et fils               | 24, place Kléber, 67000 Strasbourg, France               |
| Bólido Comidas preparadas          | C/ Araquil, 67, 28023 Madrid, Spain                      |

**총 91개의 Record가 있음**



**참고 :** MySQL에서 작동하도록 위의 SQL 문을 얻으려면 다음을 사용하십시오.



```sql
SELECT CustomerName, CONCAT(Address,', ',PostalCode,', ',City,', ',Country) AS Address
FROM Customers;
```





### Alias for Tables Example

---



다음 SQL 문은 CustomerID = 4 (Around the Horn) 인 고객의 모든 주문을 선택합니다.

"Customers"및 "Orders" 테이블을 사용하고 각각 "c"및 "o" 라는 테이블 별칭을 부여합니다. (여기서 별칭을 사용하여 SQL을 더 짧게 만듭니다).



### Example

```sql
SELECT o.OrderID, o.OrderDate, c.CustomerName
FROM Customers AS c, Orders AS o
WHERE c.CustomerName="Around the Horn" AND c.CustomerID=o.CustomerID;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 2

| OrderID | OrderDate  | CustomerName    |
| ------- | ---------- | --------------- |
| 10355   | 1996-11-15 | Around the Horn |
| 10383   | 1996-12-16 | Around the Horn |



다음 SQL 문은 위와 동일하지만 별칭이 없습니다.



### Example

```sql
SELECT Orders.OrderID, Orders.OrderDate, Customers.CustomerName
FROM Customers, Orders
WHERE Customers.CustomerName="Around the Horn" AND Customers.CustomerID=Orders.CustomerID;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 2

| OrderID | OrderDate  | CustomerName    |
| ------- | ---------- | --------------- |
| 10355   | 1996-11-15 | Around the Horn |
| 10383   | 1996-12-16 | Around the Horn |



Aliases는 다음과 같은 경우에 유용합니다:

- 쿼리에 두 개 이상의 테이블이 연관되어 있는 경우
- 함수가 쿼리에서 사용되는 경우
- Column 이름이 크거나 혹은 읽을 수 없는 경우
- 두 개 이상의 column이 결합되어 있는 경우
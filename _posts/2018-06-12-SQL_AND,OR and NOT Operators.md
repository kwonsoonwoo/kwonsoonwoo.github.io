---
layout: post
title: SQL AND, OR and NOT Operators
category: SQL
---



####[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

####기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

####결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.







## The SQL AND, OR and NOT Operators

---



WHERE 절은 AND, OR 및 NOT 연산자와 결합 할 수 있습니다.

AND 및 OR 연산자는 둘 이상의 조건에 따라 레코드를 필터링하는 데 사용됩니다.

- AND로 구분 된 모든 조건이 TRUE이면 AND 연산자는 레코드를 표시합니다.
- OR로 구분 된 조건이 TRUE 인 경우 OR 연산자는 레코드를 표시합니다.

NOT 연산자는 조건이 참이 아닌 경우 레코드를 표시합니다.



### AND Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```



### OR Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```



### NOT Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
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







## AND Example

---



다음 SQL 문은 country가 "Germany"이고 도시가 "Berlin"인 "Customers"의 모든 필드를 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE Country='Germany' AND City='Berlin';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:

Number of Records: 1

| CustomerID | CustomerName        | ContactName  | Address       | City   | PostalCode | Country |
| ---------- | ------------------- | ------------ | ------------- | ------ | ---------- | ------- |
| 1          | Alfreds Futterkiste | Maria Anders | Obere Str. 57 | Berlin | 12209      | Germany |







## OR Example

---



다음 SQL 문은 도시가 "Berlin"또는 "München"인 "Customers"의 모든 필드를 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE City='Berlin' OR City='München';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 2

| CustomerID | CustomerName        | ContactName   | Address           | City    | PostalCode | Country |
| ---------- | ------------------- | ------------- | ----------------- | ------- | ---------- | ------- |
| 1          | Alfreds Futterkiste | Maria Anders  | Obere Str. 57     | Berlin  | 12209      | Germany |
| 25         | Frankenversand      | Peter Franken | Berliner Platz 43 | München | 80805      | Germany |





## NOT Example

---



다음 SQL 문은 country가 "Germany"가 아닌 "Customers"의 모든 필드를 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE NOT Country='Germany';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:(일부만 발췌)

Number of Records: 80

| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ------------------ | ----------------------------- | ----------- | ---------- | ------- |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |
| 7          | Blondel père et fils               | Frédérique Citeaux | 24, place Kléber              | Strasbourg  | 67000      | France  |
| 8          | Bólido Comidas preparadas          | Martín Sommer      | C/ Araquil, 67                | Madrid      | 28023      | Spain   |
| 9          | Bon app'                           | Laurence Lebihans  | 12, rue des Bouchers          | Marseille   | 13008      | France  |
| 10         | Bottom-Dollar Marketse             | Elizabeth Lincoln  | 23 Tsawassen Blvd.            | Tsawassen   | T2F 8M4    | Canada  |
| 11         | B's Beverages                      | Victoria Ashworth  | Fauntleroy Circus             | London      | EC2 5NT    | UK      |







## Combining AND, OR and NOT

---



AND, OR 및 NOT 연산자를 결합 할 수도 있습니다.

다음 SQL 문은 country가 "Germany"이고 도시가 "Berlin"또는 "München"(복잡한 표현식을 형성하기 위해 괄호를 사용해야 함) 인 "Customers"의 모든 필드를 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE Country='Germany' AND (City='Berlin' OR City='München');
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:

Number of Records: 2

| CustomerID | CustomerName        | ContactName   | Address           | City    | PostalCode | Country |
| ---------- | ------------------- | ------------- | ----------------- | ------- | ---------- | ------- |
| 1          | Alfreds Futterkiste | Maria Anders  | Obere Str. 57     | Berlin  | 12209      | Germany |
| 25         | Frankenversand      | Peter Franken | Berliner Platz 43 | München | 80805      | Germany |





다음 SQL 문은 country가 "Germany"가 아니며 "USA"가 아닌 "Customers"의 모든 필드를 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE NOT Country='Germany' AND NOT Country='USA';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:(일부만 발췌)

Number of Records: 67

| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ------------------ | ----------------------------- | ----------- | ---------- | ------- |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |
| 7          | Blondel père et fils               | Frédérique Citeaux | 24, place Kléber              | Strasbourg  | 67000      | France  |
| 8          | Bólido Comidas preparadas          | Martín Sommer      | C/ Araquil, 67                | Madrid      | 28023      | Spain   |
| 9          | Bon app'                           | Laurence Lebihans  | 12, rue des Bouchers          | Marseille   | 13008      | France  |


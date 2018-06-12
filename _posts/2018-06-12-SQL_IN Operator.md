---
layout: post
title: SQL IN Operator
category: SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





###The SQL IN Operator

---



IN 연산자를 사용하여 WHERE 절에 여러 값을 지정할 수 있습니다.

IN 연산자는 여러 OR 조건의 줄임말입니다.



#### IN Syntax

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);
```



또는:



```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (SELECT STATEMENT);
```





###Demo Database

---



다음은 Northwind 샘플 데이터베이스의 "Customers"테이블에서 선택한 것입니다:



| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ------------------ | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Maria Anders       | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |



### IN Operator Examples

---



다음 SQL 문은 "Germany", "France"및 "UK"에있는 모든 고객을 선택합니다:



### Example

```sql
SELECT * FROM Customers
WHERE Country IN ('Germany', 'France', 'UK');
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:(일부만 발췌)

Number of Records: 28

| CustomerID | CustomerName              | ContactName | Address                      | City       | PostalCode | Country |
| ---------- | ------------------------- | ----------- | ---------------------------- | ---------- | ---------- | ------- |
| 4          | Around the Horn           | Juan        | 120 Hanover Sq.              | London     | WA1 1DP    | UK      |
| 6          | Blauer See Delikatessen   | Juan        | Forsterstr. 57               | Mannheim   | 68306      | Germany |
| 7          | Blondel père et fils      | Juan        | 24, place Kléber             | Strasbourg | 67000      | France  |
| 9          | Bon app'                  | Juan        | 12, rue des Bouchers         | Marseille  | 13008      | France  |
| 11         | B's Beverages             | Juan        | Fauntleroy Circus            | London     | EC2 5NT    | UK      |
| 16         | Consolidated Holdings     | Juan        | Berkeley Gardens 12 Brewery  | London     | WX1 6LT    | UK      |
| 17         | Drachenblut Delikatessend | Juan        | Walserweg 21                 | Aachen     | 52066      | Germany |
| 18         | Du monde entier           | Juan        | 67, rue des Cinquante Otages | Nantes     | 44000      | France  |
| 19         | Eastern Connection        | Juan        | 35 King George               | London     | WX3 6FW    | UK      |
| 23         | Folies gourmandes         | Juan        | 184, chaussée de Tournai     | Lille      | 59000      | France  |

**총 28개의 Record가 있음**



다음 SQL 문은 "Germany", "France"또는 "UK"에 있지 않은 모든 고객을 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE Country NOT IN ('Germany', 'France', 'UK');
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:(일부만 발췌)

Number of Records: 65

| CustomerID | CustomerName                       | ContactName | Address                       | City         | PostalCode | Country   |
| ---------- | ---------------------------------- | ----------- | ----------------------------- | ------------ | ---------- | --------- |
| 2          | Ana Trujillo Emparedados y helados | Juan        | Avda. de la Constitución 2222 | México D.F.  | 05021      | Mexico    |
| 3          | Antonio Moreno Taquería            | Juan        | Mataderos 2312                | México D.F.  | 05023      | Mexico    |
| 5          | Berglunds snabbköp                 | Juan        | Berguvsvägen 8                | Luleå        | S-958 22   | Sweden    |
| 8          | Bólido Comidas preparadas          | Juan        | C/ Araquil, 67                | Madrid       | 28023      | Spain     |
| 10         | Bottom-Dollar Marketse             | Juan        | 23 Tsawassen Blvd.            | Tsawassen    | T2F 8M4    | Canada    |
| 12         | Cactus Comidas para llevar         | Juan        | Cerrito 333                   | Buenos Aires | 1010       | Argentina |
| 13         | Centro comercial Moctezuma         | Juan        | Sierras de Granada 9993       | México D.F.  | 05022      | Mexico    |

**총 65개의 Record가 있음**



다음 SQL 문은 공급 업체와 동일한 국가의 모든 고객을 선택합니다.

 

### Example

```sql
SELECT * FROM Customers
WHERE Country IN (SELECT Country FROM Suppliers);
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:(일부만 발췌)

Number of Records: 71

| CustomerID | CustomerName              | ContactName | Address                     | City       | PostalCode | Country |
| ---------- | ------------------------- | ----------- | --------------------------- | ---------- | ---------- | ------- |
| 4          | Around the Horn           | Juan        | 120 Hanover Sq.             | London     | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp        | Juan        | Berguvsvägen 8              | Luleå      | S-958 22   | Sweden  |
| 6          | Blauer See Delikatessen   | Juan        | Forsterstr. 57              | Mannheim   | 68306      | Germany |
| 7          | Blondel père et fils      | Juan        | 24, place Kléber            | Strasbourg | 67000      | France  |
| 8          | Bólido Comidas preparadas | Juan        | C/ Araquil, 67              | Madrid     | 28023      | Spain   |
| 9          | Bon app'                  | Juan        | 12, rue des Bouchers        | Marseille  | 13008      | France  |
| 10         | Bottom-Dollar Marketse    | Juan        | 23 Tsawassen Blvd.          | Tsawassen  | T2F 8M4    | Canada  |
| 11         | B's Beverages             | Juan        | Fauntleroy Circus           | London     | EC2 5NT    | UK      |
| 15         | Comércio Mineiro          | Juan        | Av. dos Lusíadas, 23        | São Paulo  | 05432-043  | Brazil  |
| 16         | Consolidated Holdings     | Juan        | Berkeley Gardens 12 Brewery | London     | WX1 6LT    | UK      |

**총 71개의 Record가 있음** 




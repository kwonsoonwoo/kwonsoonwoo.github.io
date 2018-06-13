---
layout: post
title: SQL LIKE Operator
category: SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





###The SQL LIKE Operator

---



LIKE 연산자는 WHERE 절에서 열의 지정된 패턴을 검색하는 데 사용됩니다.

LIKE 연산자와 함께 사용되는 두 개의 와일드 카드가 있습니다.

- % - 백분율 기호는 0, 1 또는 하나 이상의 character를 나타냅니다.
- _ - 밑줄은 하나의 character를 나타냅니다.

[와일드카드 포스팅 참조]()



> 참고 : MS Access는 밑줄 (_) 대신 물음표 (?)를 사용합니다.



%와 '_' 은 조합하여 사용할 수도 있습니다!



### LIKE Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern;
```



> 팁 : AND 또는 OR 연산자를 사용하여 여러 조건을 결합 할 수도 있습니다.



다음은 '%'와 '_'와일드 카드가있는 다른 LIKE 연산자를 보여주는 몇 가지 예입니다:



| LIKE Operator                   | Description                               |
| ------------------------------- | ----------------------------------------- |
| WHERE CustomerName LIKE 'a%'    | “a”로 시작하는 모든 값                    |
| WHERE CustomerName LIKE '%a'    | “a”로 끝나는 모든 값                      |
| WHERE CustomerName LIKE '%or%'  | “or”이 있는 모든 값                       |
| WHERE CustomerName LIKE '_r%'   | 두 번째 인덱스에 “r” 이 있는 모든 값      |
| WHERE CustomerName LIKE 'a_%_%' | “a” 로 시작하며 최소 3글자 이상인 모든 값 |
| WHERE ContactName LIKE 'a%o'    | “a” 로 시작하여 “o” 로 끝나는 모든 값     |

#### SUM() Syntax

```sql
SELECT SUM(column_name)
FROM table_name
WHERE condition;
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



### SQL LIKE Examples

---



다음 SQL 문은 CustomerName이 "a"로 시작하는 모든 고객을 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE CustomerName LIKE 'a%';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 3

| CustomerID | CustomerName                       | ContactName | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ----------- | ----------------------------- | ----------- | ---------- | ------- |
| 2          | Ana Trujillo Emparedados y helados | Juan        | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Juan        | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Juan        | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |



 다음 SQL 문은 CustomerName이 "a"로 끝나는 모든 고객을 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE CustomerName LIKE '%a';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 7

| CustomerID | CustomerName               | ContactName | Address                   | City           | PostalCode | Country |
| ---------- | -------------------------- | ----------- | ------------------------- | -------------- | ---------- | ------- |
| 3          | Antonio Moreno Taquería    | Juan        | Mataderos 2312            | México D.F.    | 05023      | Mexico  |
| 13         | Centro comercial Moctezuma | Juan        | Sierras de Granada 9993   | México D.F.    | 05022      | Mexico  |
| 30         | Godos Cocina Típica        | Juan        | C/ Romero, 33             | Sevilla        | 41101      | Spain   |
| 61         | Que Delícia                | Juan        | Rua da Panificadora, 12   | Rio de Janeiro | 02389-673  | Brazil  |
| 62         | Queen Cozinha              | Juan        | Alameda dos Canàrios, 891 | São Paulo      | 05487-020  | Brazil  |
| 88         | Wellington Importadora     | Juan        | Rua do Mercado, 12        | Resende        | 08737-363  | Brazil  |
| 90         | Wilman Kala                | Juan        | Keskuskatu 45             | Helsinki       | 21240      | Finland |





 다음 SQL 문은 CustomerName이 "or"이 있는 모든 고객을 선택합니다.



###Example

```sql
SELECT * FROM Customers
WHERE CustomerName LIKE '%or%'
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 11

| CustomerID | CustomerName               | ContactName | Address                        | City        | PostalCode | Country |
| ---------- | -------------------------- | ----------- | ------------------------------ | ----------- | ---------- | ------- |
| 3          | Antonio Moreno Taquería    | Juan        | Mataderos 2312                 | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn            | Juan        | 120 Hanover Sq.                | London      | WA1 1DP    | UK      |
| 36         | Hungry Coyote Import Store | Juan        | City Center Plaza 516 Main St. | Elgin       | 97827      | USA     |
| 40         | La corne d'abondance       | Juan        | 67, avenue de l'Europe         | Versailles  | 78000      | France  |
| 43         | Lazy K Kountry Store       | Juan        | 12 Orchestra Terrace           | Walla Walla | 99362      | USA     |
| 52         | Morgenstern Gesundkost     | Juan        | Heerstr. 22                    | Leipzig     | 04179      | Germany |
| 53         | North/South                | Juan        | South House 300 Queensbridge   | London      | SW7 1RZ    | UK      |
| 55         | Old World Delicatessen     | Juan        | 2743 Bering St.                | Anchorage   | 99508      | USA     |
| 72         | Seven Seas Imports         | Juan        | 90 Wadhurst Rd.                | London      | OX15 4NB   | UK      |
| 80         | Tortuga Restaurante        | Juan        | Avda. Azteca 123               | México D.F. | 05033      | Mexico  |
| 88         | Wellington Importadora     | Juan        | Rua do Mercado, 12             | Resende     | 08737-363  | Brazil  |





 다음 SQL 문은 두 번째 인덱스(위치)에 "r"이있는 CustomerName을 가진 모든 고객을 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE CustomerName LIKE '_r%';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:

Number of Records: 11

| CustomerID | CustomerName                      | ContactName | Address                   | City      | PostalCode | Country   |
| ---------- | --------------------------------- | ----------- | ------------------------- | --------- | ---------- | --------- |
| 4          | Around the Horn                   | Juan        | 120 Hanover Sq.           | London    | WA1 1DP    | UK        |
| 17         | Drachenblut Delikatessend         | Juan        | Walserweg 21              | Aachen    | 52066      | Germany   |
| 20         | Ernst Handel                      | Juan        | Kirchgasse 6              | Graz      | 8010       | Austria   |
| 25         | Frankenversand                    | Juan        | Berliner Platz 43         | München   | 80805      | Germany   |
| 26         | France restauration               | Juan        | 54, rue Royale            | Nantes    | 44000      | France    |
| 27         | Franchi S.p.A.                    | Juan        | Via Monte Bianco 34       | Torino    | 10100      | Italy     |
| 32         | Great Lakes Food Market           | Juan        | 2732 Baker Blvd.          | Eugene    | 97403      | USA       |
| 33         | GROSELLA-Restaurante              | Juan        | 5ª Ave. Los Palos Grandes | Caracas   | 1081       | Venezuela |
| 60         | Princesa Isabel Vinhoss           | Juan        | Estrada da saúde n. 58    | Lisboa    | 1756       | Portugal  |
| 81         | Tradição Hipermercados            | Juan        | Av. Inês de Castro, 414   | São Paulo | 05634-030  | Brazil    |
| 82         | Trail's Head Gourmet Provisioners | Juan        | 722 DaVinci Blvd.         | Kirkland  | 98034      | USA       |





다음 SQL 문은 CustomerName이 "a"로 시작하고 길이가 3 자 이상인 모든 고객을 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE CustomerName LIKE 'a_%_%';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 3

| CustomerID | CustomerName                       | ContactName | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ----------- | ----------------------------- | ----------- | ---------- | ------- |
| 2          | Ana Trujillo Emparedados y helados | Juan        | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Juan        | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Juan        | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |





다음 SQL 문은 ContactName이 "a"로 시작하고 "o"로 끝나는 모든 고객을 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE ContactName LIKE 'a%o';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

No result.



 다음 SQL 문은 CustomerName이 "a"로 시작하지 않는 모든 고객을 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE ContactName NOT LIKE 'a%';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:(일부만 발췌)

Number of Records: 90

| CustomerID | CustomerName               | ContactName | Address              | City         | PostalCode | Country   |
| ---------- | -------------------------- | ----------- | -------------------- | ------------ | ---------- | --------- |
| 5          | Berglunds snabbköp         | Juan        | Berguvsvägen 8       | Luleå        | S-958 22   | Sweden    |
| 6          | Blauer See Delikatessen    | Juan        | Forsterstr. 57       | Mannheim     | 68306      | Germany   |
| 7          | Blondel père et fils       | Juan        | 24, place Kléber     | Strasbourg   | 67000      | France    |
| 8          | Bólido Comidas preparadas  | Juan        | C/ Araquil, 67       | Madrid       | 28023      | Spain     |
| 9          | Bon app'                   | Juan        | 12, rue des Bouchers | Marseille    | 13008      | France    |
| 10         | Bottom-Dollar Marketse     | Juan        | 23 Tsawassen Blvd.   | Tsawassen    | T2F 8M4    | Canada    |
| 11         | B's Beverages              | Juan        | Fauntleroy Circus    | London       | EC2 5NT    | UK        |
| 12         | Cactus Comidas para llevar | Juan        | Cerrito 333          | Buenos Aires | 1010       | Argentina |

**총 테이블의 개수가 90개**


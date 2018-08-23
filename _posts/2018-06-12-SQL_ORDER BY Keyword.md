---
layout: post
title: SQL ORDER BY Keyword
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.







## The SQL ORDER BY Keyword

---



ORDER BY 키워드는 결과 집합을 오름차순 또는 내림차순으로 정렬하는 데 사용됩니다.

ORDER BY 키워드는 기본적으로 레코드를 오름차순으로 정렬합니다. 내림차순으로 레코드를 정렬하려면 DESC 키워드를 사용하십시오.





### ORDER BY Syntax

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
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







## ORDER BY Example

---



다음 SQL 문은 "Customers"테이블의 모든 고객을 "Country"열로 정렬하여 선택합니다.



### Example

```sql
SELECT * FROM Customers
ORDER BY Country;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:(일부만 발췌)

Number of Records: 91

| CustomerID | CustomerName               | ContactName      | Address                             | City         | PostalCode | Country   |
| ---------- | -------------------------- | ---------------- | ----------------------------------- | ------------ | ---------- | --------- |
| 12         | Cactus Comidas para llevar | Patricio Simpson | Cerrito 333                         | Buenos Aires | 1010       | Argentina |
| 54         | Océano Atlántico Ltda.     | Yvonne Moncada   | Ing. Gustavo Moncada 8585 Piso 20-A | Buenos Aires | 1010       | Argentina |
| 64         | Rancho grande              | Sergio Gutiérrez | Av. del Libertador 900              | Buenos Aires | 1010       | Argentina |
| 20         | Ernst Handel               | Roland Mendel    | Kirchgasse 6                        | Graz         | 8010       | Austria   |
| 59         | Piccolo und mehr           | Georg Pipps      | Geislweg 14                         | Salzburg     | 5020       | Austria   |
| 50         | Maison Dewey               | Catherine Dewey  | Rue Joseph-Bens 532                 | Bruxelles    | B-1180     | Belgium   |
| 76         | Suprêmes délices           | Pascale Cartrain | Boulevard Tirou, 255                | Charleroi    | B-6000     | Belgium   |
| 15         | Comércio Mineiro           | Pedro Afonso     | Av. dos Lusíadas, 23                | São Paulo    | 05432-043  | Brazil    |





## ORDER BY DESC Example

---



다음 SQL 문은 "Customers" 테이블의 모든 고객을 "Country"열을 기준으로 DESCENDING으로 정렬하여 선택합니다.

- 예제의 결과를 통해 보면 위 문장의 의미는 내림차순으로 정렬하여 출력된다는걸 알수 있다.(기본은 오름차순)
- 이 Example에선 Country열에서 알파벳 순으로 출력됨.(알파벳 역순 순서대로)



### Example

```sql
SELECT * FROM Customers
ORDER BY Country DESC;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 91

| CustomerID | CustomerName               | ContactName      | Address                                        | City            | PostalCode | Country   |
| ---------- | -------------------------- | ---------------- | ---------------------------------------------- | --------------- | ---------- | --------- |
| 33         | GROSELLA-Restaurante       | Manuel Pereira   | 5ª Ave. Los Palos Grandes                      | Caracas         | 1081       | Venezuela |
| 35         | HILARIÓN-Abastos           | Carlos Hernández | Carrera 22 con Ave. Carlos Soublette #8-35     | San Cristóbal   | 5022       | Venezuela |
| 46         | LILA-Supermercado          | Carlos González  | Carrera 52 con Ave. Bolívar #65-98 Llano Largo | Barquisimeto    | 3508       | Venezuela |
| 47         | LINO-Delicateses           | Felipe Izquierdo | Ave. 5 de Mayo Porlamar                        | I. de Margarita | 4980       | Venezuela |
| 32         | Great Lakes Food Market    | Howard Snyder    | 2732 Baker Blvd.                               | Eugene          | 97403      | USA       |
| 36         | Hungry Coyote Import Store | Yoshi Latimer    | City Center Plaza 516 Main St.                 | Elgin           | 97827      | USA       |
| 43         | Lazy K Kountry Store       | John Steel       | 12 Orchestra Terrace                           | Walla Walla     | 99362      | USA       |





## ORDER BY Several Columns Example

---



다음 SQL 문은 "Customers"테이블의 모든 고객을 "Country"및 "CustomerName"열로 정렬하여 선택합니다.



### Example

```sql
SELECT * FROM Customers
ORDER BY Country, CustomerName;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:(일부만 발췌)

Number of Records: 91

| CustomerID | CustomerName               | ContactName      | Address                             | City         | PostalCode | Country   |
| ---------- | -------------------------- | ---------------- | ----------------------------------- | ------------ | ---------- | --------- |
| 12         | Cactus Comidas para llevar | Patricio Simpson | Cerrito 333                         | Buenos Aires | 1010       | Argentina |
| 54         | Océano Atlántico Ltda.     | Yvonne Moncada   | Ing. Gustavo Moncada 8585 Piso 20-A | Buenos Aires | 1010       | Argentina |
| 64         | Rancho grande              | Sergio Gutiérrez | Av. del Libertador 900              | Buenos Aires | 1010       | Argentina |
| 20         | Ernst Handel               | Roland Mendel    | Kirchgasse 6                        | Graz         | 8010       | Austria   |
| 59         | Piccolo und mehr           | Georg Pipps      | Geislweg 14                         | Salzburg     | 5020       | Austria   |
| 50         | Maison Dewey               | Catherine Dewey  | Rue Joseph-Bens 532                 | Bruxelles    | B-1180     | Belgium   |
| 76         | Suprêmes délices           | Pascale Cartrain | Boulevard Tirou, 255                | Charleroi    | B-6000     | Belgium   |
| 15         | Comércio Mineiro           | Pedro Afonso     | Av. dos Lusíadas, 23                | São Paulo    | 05432-043  | Brazil    |
| 21         | Familia Arquibaldo         | Aria Cruz        | Rua Orós, 92                        | São Paulo    | 05442-030  | Brazil    |





## ORDER BY Several Columns Example 2

---



다음 SQL 문은 "Customers"테이블의 모든 고객을 "Country"로 오름차순으로 정렬하고 "CustomerName"열로 내림차순으로 정렬합니다.



### Example

```sql
SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:(일부만 발췌)

Number of Records: 91

| CustomerID | CustomerName               | ContactName      | Address                             | City         | PostalCode | Country   |
| ---------- | -------------------------- | ---------------- | ----------------------------------- | ------------ | ---------- | --------- |
| 64         | Rancho grande              | Sergio Gutiérrez | Av. del Libertador 900              | Buenos Aires | 1010       | Argentina |
| 54         | Océano Atlántico Ltda.     | Yvonne Moncada   | Ing. Gustavo Moncada 8585 Piso 20-A | Buenos Aires | 1010       | Argentina |
| 12         | Cactus Comidas para llevar | Patricio Simpson | Cerrito 333                         | Buenos Aires | 1010       | Argentina |
| 59         | Piccolo und mehr           | Georg Pipps      | Geislweg 14                         | Salzburg     | 5020       | Austria   |
| 20         | Ernst Handel               | Roland Mendel    | Kirchgasse 6                        | Graz         | 8010       | Austria   |
| 76         | Suprêmes délices           | Pascale Cartrain | Boulevard Tirou, 255                | Charleroi    | B-6000     | Belgium   |
| 50         | Maison Dewey               | Catherine Dewey  | Rue Joseph-Bens 532                 | Bruxelles    | B-1180     | Belgium   |
| 88         | Wellington Importadora     | Paula Parente    | Rua do Mercado, 12                  | Resende      | 08737-363  | Brazil    |

---
layout: post
title: SQL Comments
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.



### SQL Comments

---

주석은 SQL 문의 섹션을 설명하거나 SQL 문의 실행을 막는 데 사용됩니다.

> **참고 :이 장의 예제는 Firefox 및 Microsoft Edge에서 작동하지 않습니다! **
>
> 주석은 Microsoft Access 데이터베이스에서 지원되지 않습니다. Firefox와 Microsoft Edge는 예제에서 Microsoft Access 데이터베이스를 사용하고 있습니다.





### Single Line Comments

---

한 줄 주석은 -로 시작합니다.

 -와 행 끝 사이의 모든 텍스트는 무시됩니다 (실행되지 않습니다).

다음 예제는 한 줄 주석을 설명으로 사용합니다.



#### Example



```sql
--Select all:
SELECT * FROM Customers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:(일부만 발췌)

Number of Records: 154

| CustomerID | CustomerName                       | ContactName | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ----------- | ----------------------------- | ----------- | ---------- | ------- |
| 2          | Ana Trujillo Emparedados y helados | Juan        | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Juan        | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Juan        | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Juan        | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |
| 6          | Blauer See Delikatessen            | Juan        | Forsterstr. 57                | Mannheim    | 68306      | Germany |
| 7          | Blondel père et fils               | Juan        | 24, place Kléber              | Strasbourg  | 67000      | France  |
| 8          | Bólido Comidas preparadas          | Juan        | C/ Araquil, 67                | Madrid      | 28023      | Spain   |
| 9          | Bon app'                           | Juan        | 12, rue des Bouchers          | Marseille   | 13008      | France  |

**총 154개의 Record가 있음**



다음 예제에서는 한 줄 주석을 사용하여 줄 끝을 무시합니다:

#### Example

```sql
SELECT * FROM Customers -- WHERE City='Berlin';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result(일부만 발췌):

Number of Records: 154

| CustomerID | CustomerName                       | ContactName | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ----------- | ----------------------------- | ----------- | ---------- | ------- |
| 2          | Ana Trujillo Emparedados y helados | Juan        | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Juan        | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Juan        | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Juan        | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |
| 6          | Blauer See Delikatessen            | Juan        | Forsterstr. 57                | Mannheim    | 68306      | Germany |
| 7          | Blondel père et fils               | Juan        | 24, place Kléber              | Strasbourg  | 67000      | France  |
| 8          | Bólido Comidas preparadas          | Juan        | C/ Araquil, 67                | Madrid      | 28023      | Spain   |
| 9          | Bon app'                           | Juan        | 12, rue des Bouchers          | Marseille   | 13008      | France  |

**총 154개의 Record가 있음**



다음 예제에서는 한 줄 주석을 사용하여 문을 무시합니다:

#### Example

```sql
--SELECT * FROM Customers;
SELECT * FROM Products;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result(일부만 발췌):

Number of Records: 77

| ProductID | ProductName                     | SupplierID | CategoryID | Unit                | Price |
| --------- | ------------------------------- | ---------- | ---------- | ------------------- | ----- |
| 1         | Chais                           | 1          | 1          | 10 boxes x 20 bags  | 18    |
| 2         | Chang                           | 1          | 1          | 24 - 12 oz bottles  | 19    |
| 3         | Aniseed Syrup                   | 1          | 2          | 12 - 550 ml bottles | 10    |
| 4         | Chef Anton's Cajun Seasoning    | 2          | 2          | 48 - 6 oz jars      | 22    |
| 5         | Chef Anton's Gumbo Mix          | 2          | 2          | 36 boxes            | 21.35 |
| 6         | Grandma's Boysenberry Spread    | 3          | 2          | 12 - 8 oz jars      | 25    |
| 7         | Uncle Bob's Organic Dried Pears | 3          | 7          | 12 - 1 lb pkgs.     | 30    |
| 8         | Northwoods Cranberry Sauce      | 3          | 2          | 12 - 12 oz jars     | 40    |
| 9         | Mishi Kobe Niku                 | 4          | 6          | 18 - 500 g pkgs.    | 97    |
| 10        | Ikura                           | 4          | 8          | 12 - 200 ml jars    | 31    |
| 11        | Queso Cabrales                  | 5          | 4          | 1 kg pkg.           | 21    |

**총 77개의 Record가 있음**



### Multi-line Comments

---

여러 줄 주석은 / *로 시작하고 */로 끝납니다.

/ *와 */ 사이의 모든 텍스트는 무시됩니다.

다음 예제에서는 설명을 위해 여러 줄 주석을 사용합니다:



#### Example

```sql
/*Select all the columns
of all the records
in the Customers table:*/
SELECT * FROM Customers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result(일부만 발췌):

Number of Records: 154

| CustomerID | CustomerName                       | ContactName | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ----------- | ----------------------------- | ----------- | ---------- | ------- |
| 2          | Ana Trujillo Emparedados y helados | Juan        | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Juan        | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Juan        | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Juan        | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |
| 6          | Blauer See Delikatessen            | Juan        | Forsterstr. 57                | Mannheim    | 68306      | Germany |
| 7          | Blondel père et fils               | Juan        | 24, place Kléber              | Strasbourg  | 67000      | France  |
| 8          | Bólido Comidas preparadas          | Juan        | C/ Araquil, 67                | Madrid      | 28023      | Spain   |
| 9          | Bon app'                           | Juan        | 12, rue des Bouchers          | Marseille   | 13008      | France  |

**총 154개의 Record가 있음**



다음 예제에서는 여러 줄 주석을 사용하여 여러 줄을 무시합니다:

#### Example

```sql
/*SELECT * FROM Customers;
SELECT * FROM Products;
SELECT * FROM Orders;
SELECT * FROM Categories;*/
SELECT * FROM Suppliers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 29

| SupplierID | SupplierName                           | ContactName                | Address                                       | City          | PostalCode | Country     | Phone           |
| ---------- | -------------------------------------- | -------------------------- | --------------------------------------------- | ------------- | ---------- | ----------- | --------------- |
| 1          | Exotic Liquid                          | Charlotte Cooper           | 49 Gilbert St.                                | Londona       | EC1 4SD    | UK          | (171) 555-2222  |
| 2          | New Orleans Cajun Delights             | Shelley Burke              | P.O. Box 78934                                | New Orleans   | 70117      | USA         | (100) 555-4822  |
| 3          | Grandma Kelly's Homestead              | Regina Murphy              | 707 Oxford Rd.                                | Ann Arbor     | 48104      | USA         | (313) 555-5735  |
| 4          | Tokyo Traders                          | Yoshi Nagase               | 9-8 Sekimai Musashino-shi                     | Tokyo         | 100        | Japan       | (03) 3555-5011  |
| 5          | Cooperativa de Quesos 'Las Cabras'     | Antonio del Valle Saavedra | Calle del Rosal 4                             | Oviedo        | 33007      | Spain       | (98) 598 76 54  |
| 6          | Mayumi's                               | Mayumi Ohno                | 92 Setsuko Chuo-ku                            | Osaka         | 545        | Japan       | (06) 431-7877   |
| 7          | Pavlova, Ltd.                          | Ian Devling                | 74 Rose St. Moonie Ponds                      | Melbourne     | 3058       | Australia   | (03) 444-2343   |
| 8          | Specialty Biscuits, Ltd.               | Peter Wilson               | 29 King's Way                                 | Manchester    | M14 GSD    | UK          | (161) 555-4448  |
| 9          | PB Knäckebröd AB                       | Lars Peterson              | Kaloadagatan 13                               | Göteborg      | S-345 67   | Sweden      | 031-987 65 43   |
| 10         | Refrescos Americanas LTDA              | Carlos Diaz                | Av. das Americanas 12.890                     | São Paulo     | 5442       | Brazil      | (11) 555 4640   |
| 11         | Heli Süßwaren GmbH & Co. KG            | Petra Winkler              | Tiergartenstraße 5                            | Berlin        | 10785      | Germany     | (010) 9984510   |
| 12         | Plutzer Lebensmittelgroßmärkte AG      | Martin Bein                | Bogenallee 51                                 | Frankfurt     | 60439      | Germany     | (069) 992755    |
| 13         | Nord-Ost-Fisch Handelsgesellschaft mbH | Sven Petersen              | Frahmredder 112a                              | Cuxhaven      | 27478      | Germany     | (04721) 8713    |
| 14         | Formaggi Fortini s.r.l.                | Elio Rossi                 | Viale Dante, 75                               | Ravenna       | 48100      | Italy       | (0544) 60323    |
| 15         | Norske Meierier                        | Beate Vileid               | Hatlevegen 5                                  | Sandvika      | 1320       | Norway      | (0)2-953010     |
| 16         | Bigfoot Breweries                      | Cheryl Saylor              | 3400 - 8th Avenue Suite 210                   | Bend          | 97101      | USA         | (503) 555-9931  |
| 17         | Svensk Sjöföda AB                      | Michael Björn              | Brovallavägen 231                             | Stockholm     | S-123 45   | Sweden      | 08-123 45 67    |
| 18         | Aux joyeux ecclésiastiques             | Guylène Nodier             | 203, Rue des Francs-Bourgeois                 | Paris         | 75004      | France      | (1) 03.83.00.68 |
| 19         | New England Seafood Cannery            | Robb Merchant              | Order Processing Dept. 2100 Paul Revere Blvd. | Boston        | 02134      | USA         | (617) 555-3267  |
| 20         | Leka Trading                           | Chandra Leka               | 471 Serangoon Loop, Suite #402                | Singapore     | 0512       | Singapore   | 555-8787        |
| 21         | Lyngbysild                             | Niels Petersen             | Lyngbysild Fiskebakken 10                     | Lyngby        | 2800       | Denmark     | 43844108        |
| 22         | Zaanse Snoepfabriek                    | Dirk Luchte                | Verkoop Rijnweg 22                            | Zaandam       | 9999 ZZ    | Netherlands | (12345) 1212    |
| 23         | Karkki Oy                              | Anne Heikkonen             | Valtakatu 12                                  | Lappeenranta  | 53120      | Finland     | (953) 10956     |
| 24         | G'day, Mate                            | Wendy Mackenzie            | 170 Prince Edward Parade Hunter's Hill        | Sydney        | 2042       | Australia   | (02) 555-5914   |
| 25         | Ma Maison                              | Jean-Guy Lauzon            | 2960 Rue St. Laurent                          | Montréal      | H1J 1C3    | Canada      | (514) 555-9022  |
| 26         | Pasta Buttini s.r.l.                   | Giovanni Giudici           | Via dei Gelsomini, 153                        | Salerno       | 84100      | Italy       | (089) 6547665   |
| 27         | Escargots Nouveaux                     | Marie Delamare             | 22, rue H. Voiron                             | Montceau      | 71300      | France      | 85.57.00.07     |
| 28         | Gai pâturage                           | Eliane Noz                 | Bat. B 3, rue des Alpes                       | Annecy        | 74000      | France      | 38.76.98.06     |
| 29         | Forêts d'érables                       | Chantal Goulet             | 148 rue Chasseur                              | Ste-Hyacinthe | J2S 7S8    | Canada      | (514) 555-2955  |



명령문의 일부만 무시하려면 / * * / 주석도 사용하십시오.

다음 예제에서는 주석을 사용하여 행의 일부를 무시합니다:



#### Example

```sql
SELECT CustomerName, /*City,*/ Country FROM Customers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result(일부만 발췌):

Number of Records: 154

| CustomerName                       | Country   |
| ---------------------------------- | --------- |
| Ana Trujillo Emparedados y helados | Mexico    |
| Antonio Moreno Taquería            | Mexico    |
| Around the Horn                    | UK        |
| Berglunds snabbköp                 | Sweden    |
| Blauer See Delikatessen            | Germany   |
| Blondel père et fils               | France    |
| Bólido Comidas preparadas          | Spain     |
| Bon app'                           | France    |
| Bottom-Dollar Marketse             | Canada    |
| B's Beverages                      | UK        |
| Cactus Comidas para llevar         | Argentina |

**총 154개의 Record가 있음**



다음 예제에서는 주석을 사용하여 명령문의 일부를 무시합니다:

#### Example

```sql
SELECT * FROM Customers WHERE (CustomerName LIKE 'L%'
OR CustomerName LIKE 'R%' /*OR CustomerName LIKE 'S%'
OR CustomerName LIKE 'T%'*/ OR CustomerName LIKE 'W%')
AND Country='USA'
ORDER BY CustomerName;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 5

| CustomerID | CustomerName               | ContactName | Address                     | City          | PostalCode | Country |
| ---------- | -------------------------- | ----------- | --------------------------- | ------------- | ---------- | ------- |
| 43         | Lazy K Kountry Store       | Juan        | 12 Orchestra Terrace        | Walla Walla   | 99362      | USA     |
| 45         | Let's Stop N Shop          | Juan        | 87 Polk St. Suite 5         | San Francisco | 94117      | USA     |
| 48         | Lonesome Pine Restaurant   | Juan        | 89 Chiaroscuro Rd.          | Portland      | 97219      | USA     |
| 65         | Rattlesnake Canyon Grocery | Juan        | 2817 Milton Dr.             | Albuquerque   | 87110      | USA     |
| 89         | White Clover Markets       | Juan        | 305 - 14th Ave. S. Suite 3B | Seattle       | 98128      | USA     |
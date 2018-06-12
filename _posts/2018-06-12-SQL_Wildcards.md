---
layout: post
title: SQL Wildcards
category: SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





###SQL Wildcard Characters

---



와일드 카드 문자는 문자열의 다른 문자를 대체하는 데 사용됩니다.

와일드 카드 문자는 SQL LIKE 연산자와 함께 사용됩니다. LIKE 연산자는 WHERE 절에서 열의 지정된 패턴을 검색하는 데 사용됩니다.

LIKE 연산자와 함께 사용되는 두 개의 와일드 카드가 있습니다:

- % - 백분율 기호는 0, 1 또는 하나 이상의 character를 나타냅니다.
- _ - 밑줄은 하나의 character를 나타냅니다.

> 참고 : MS Access는 밑줄 (_) 대신 물음표 (?)를 사용합니다.



MS Access 및 SQL Server에서는 다음을 사용할 수도 있습니다:

- [charlist] - 일치시킬 문자와 세트의 범위를 정의합니다.
-  [ ^charlist] 또는 [! charlist] - 일치하지 않는 문자의 집합과 범위를 정의합니다.

 와일드 카드는 조합하여 사용할 수도 있습니다!

다음은 '%'와 '_'와일드 카드가있는 다른 LIKE 연산자를 보여주는 몇 가지 예입니다:



| LIKE Operator                   | Description                               |
| ------------------------------- | ----------------------------------------- |
| WHERE CustomerName LIKE 'a%'    | “a”로 시작하는 모든 값                    |
| WHERE CustomerName LIKE '%a'    | “a”로 끝나는 모든 값                      |
| WHERE CustomerName LIKE '%or%'  | “or”이 있는 모든 값                       |
| WHERE CustomerName LIKE '_r%'   | 두 번째 인덱스에 “r” 이 있는 모든 값      |
| WHERE CustomerName LIKE 'a_%_%' | “a” 로 시작하며 최소 3글자 이상인 모든 값 |
| WHERE ContactName LIKE 'a%o'    | “a” 로 시작하여 “o” 로 끝나는 모든 값     |



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



### Using the % Wildcard

---

다음 SQL 문은 City가 "ber"로 시작하는 모든 고객을 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE City LIKE 'ber%';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 2

| CustomerID | CustomerName                 | ContactName | Address                 | City    | PostalCode | Country     |
| ---------- | ---------------------------- | ----------- | ----------------------- | ------- | ---------- | ----------- |
| 14         | Chop-suey Chinese            | Juan        | Hauptstr. 29            | Bern    | 3012       | Switzerland |
| 49         | Magazzini Alimentari Riuniti | Juan        | Via Ludovico il Moro 22 | Bergamo | 24100      | Italy       |



 다음 SQL 문은 패턴이 "es"인 City가 있는 모든 고객을 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE City LIKE '%es%';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 9

| CustomerID | CustomerName               | ContactName | Address                             | City         | PostalCode | Country   |
| ---------- | -------------------------- | ----------- | ----------------------------------- | ------------ | ---------- | --------- |
| 12         | Cactus Comidas para llevar | Juan        | Cerrito 333                         | Buenos Aires | 1010       | Argentina |
| 18         | Du monde entier            | Juan        | 67, rue des Cinquante Otages        | Nantes       | 44000      | France    |
| 26         | France restauration        | Juan        | 54, rue Royale                      | Nantes       | 44000      | France    |
| 38         | Island Trading             | Juan        | Garden House Crowther Way           | Cowes        | PO31 7PJ   | UK        |
| 40         | La corne d'abondance       | Juan        | 67, avenue de l'Europe              | Versailles   | 78000      | France    |
| 50         | Maison Dewey               | Juan        | Rue Joseph-Bens 532                 | Bruxelles    | B-1180     | Belgium   |
| 54         | Océano Atlántico Ltda.     | Juan        | Ing. Gustavo Moncada 8585 Piso 20-A | Buenos Aires | 1010       | Argentina |
| 64         | Rancho grande              | Juan        | Av. del Libertador 900              | Buenos Aires | 1010       | Argentina |
| 88         | Wellington Importadora     | Juan        | Rua do Mercado, 12                  | Resende      | 08737-363  | Brazil    |

 

###Using the _ Wildcard

---



다음 SQL 문은 임의의 문자로 시작하고 "erlin" 다음에 City가 있는 모든 고객을 선택합니다.



###Example

```sql
SELECT * FROM Customers
WHERE City LIKE '_erlin';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

No result.





아래 SQL 문은 "L"로 시작하고 그 다음 위치엔 임의의 문자 그 다음 위치엔  "n" 문자 

그 다음에 임의의 문자, 그 다음에 "on"이 있는 City의 모든 고객을 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE City LIKE 'L_n_on';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:

Number of Records: 6

| CustomerID | CustomerName          | ContactName | Address                      | City   | PostalCode | Country |
| ---------- | --------------------- | ----------- | ---------------------------- | ------ | ---------- | ------- |
| 4          | Around the Horn       | Juan        | 120 Hanover Sq.              | London | WA1 1DP    | UK      |
| 11         | B's Beverages         | Juan        | Fauntleroy Circus            | London | EC2 5NT    | UK      |
| 16         | Consolidated Holdings | Juan        | Berkeley Gardens 12 Brewery  | London | WX1 6LT    | UK      |
| 19         | Eastern Connection    | Juan        | 35 King George               | London | WX3 6FW    | UK      |
| 53         | North/South           | Juan        | South House 300 Queensbridge | London | SW7 1RZ    | UK      |
| 72         | Seven Seas Imports    | Juan        | 90 Wadhurst Rd.              | London | OX15 4NB   | UK      |



### Using the [charlist] Wildcard

---



다음 SQL 문은 "b", "s"또는 "p"로 시작하는 City에 있는 모든 고객을 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE Ciry LIKE '[bsp]%';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:(일부만 발췌)

Number of Records: 29

| CustomerID | CustomerName               | ContactName        | Address              | City         | PostalCode | Country     |
| ---------- | -------------------------- | ------------------ | -------------------- | ------------ | ---------- | ----------- |
| 1          | Alfreds Futterkiste        | Maria Anders       | Obere Str. 57        | Berlin       | 12209      | Germany     |
| 7          | Blondel père et fils       | Frédérique Citeaux | 24, place Kléber     | Strasbourg   | 67000      | France      |
| 12         | Cactus Comidas para llevar | Patricio Simpson   | Cerrito 333          | Buenos Aires | 1010       | Argentina   |
| 14         | Chop-suey Chinese          | Yang Wang          | Hauptstr. 29         | Bern         | 3012       | Switzerland |
| 15         | Comércio Mineiro           | Pedro Afonso       | Av. dos Lusíadas, 23 | São Paulo    | 05432-043  | Brazil      |

**총 29개 Record가 있음**



다음 SQL 문은 "a", "b"또는 "c"로 시작하는 City의 모든 고객을 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE City LIKE '[a-c]%';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:(일부만 발췌)

Number of Records: 22

| CustomerID | CustomerName               | ContactName      | Address       | City         | PostalCode | Country     |
| ---------- | -------------------------- | ---------------- | ------------- | ------------ | ---------- | ----------- |
| 1          | Alfreds Futterkiste        | Maria Anders     | Obere Str. 57 | Berlin       | 12209      | Germany     |
| 12         | Cactus Comidas para llevar | Patricio Simpson | Cerrito 333   | Buenos Aires | 1010       | Argentina   |
| 14         | Chop-suey Chinese          | Yang Wang        | Hauptstr. 29  | Bern         | 3012       | Switzerland |
| 17         | Drachenblut Delikatessend  | Sven Ottlieb     | Walserweg 21  | Aachen       | 52066      | Germany     |
| 24         | Folk och fä HB             | Maria Larsson    | Åkergatan 24  | Bräcke       | S-844 67   | Sweden      |

**총 22개 Record가 있음**



### Using the [!charlist] Wildcard

---



다음 두 SQL 문은 "b", "s"또는 "p"로 시작하는 City가 아닌 모든 고객을 선택합니다.



### Example

```sql
SELECT * FROM Customers
WHERE City LIKE '[!bsp]%';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



또는:



### Example

```sql
SELECT * FROM Customers
WHERE City NOT LIKE '[bsp]%';
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것





### Result:(일부만 발췌)

Number of Records: 62

| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ------------------ | ----------------------------- | ----------- | ---------- | ------- |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |
| 6          | Blauer See Delikatessen            | Hanna Moos         | Forsterstr. 57                | Mannheim    | 68306      | Germany |

**총 62개 Record가 있음**




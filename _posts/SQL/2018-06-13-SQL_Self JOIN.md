---
layout: post
title: SQL Self JOIN
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





### SQL Self JOIN

---

self JOIN은 정규 조인이지만 테이블 자체는 조인됩니다.



####Self JOIN Syntax

```sql
SELECT column_name(S)
FROM table1 T1, table2 T2
WHERE condition;
```





### Demo Database

---

이 튜토리얼에서는 잘 알려진 Northwind 샘플 데이터베이스를 사용합니다.

다음은 "Customers" 테이블에서 선택한 항목입니다:

| CustomerID | CustomerName                       | ContactName    | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | -------------- | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Maria Anders   | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo   | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno | Mataderos 2312                | México D.F. | 05023      | Mexico  |



### SQL Self JOIN Example

---

다음 SQL 문은 같은 도시에 있는 고객과 일치합니다:



#### Example

```sql
SELECT A.CustomerName AS CustomerName1, B.CustomerName AS CustomerName2, A.City
FROM Customers A, Customers B
WHERE A.CustomerID <> B.CustomerID
AND A.City = B.City 
ORDER BY A.City;
```



### Result:(일부만 발췌)

Number of Records: 94

| CustomerName1                  | CustomerName2                  | City         |
| ------------------------------ | ------------------------------ | ------------ |
| Cactus Comidas para llevar     | Océano Atlántico Ltda.         | Buenos Aires |
| Cactus Comidas para llevar     | Rancho grande                  | Buenos Aires |
| Océano Atlántico Ltda.         | Cactus Comidas para llevar     | Buenos Aires |
| Océano Atlántico Ltda.         | Rancho grande                  | Buenos Aires |
| Rancho grande                  | Cactus Comidas para llevar     | Buenos Aires |
| Rancho grande                  | Océano Atlántico Ltda.         | Buenos Aires |
| Furia Bacalhau e Frutos do Mar | Princesa Isabel Vinhoss        | Lisboa       |
| Princesa Isabel Vinhoss        | Furia Bacalhau e Frutos do Mar | Lisboa       |
| Around the Horn                | B's Beverages                  | London       |
| Around the Horn                | Consolidated Holdings          | London       |
| Around the Horn                | Eastern Connection             | London       |

**총 94개의 Record가 있음**
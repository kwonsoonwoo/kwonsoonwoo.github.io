---
layout: post
title: SQL HAVING Clause
category: SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





### The SQL HAVING Clause

---

WHERE 키워드를 집계 함수와 함께 사용할 수 없으므로 HAVING 절이 SQL에 추가되었습니다.



####HAVING Syntax

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s);
```

---



### Demo Database

---

다음은 Northwind 샘플 데이터베이스의 "Customers"테이블에서 선택한 것입니다.



| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| ---------- | ---------------------------------- | ------------------ | ----------------------------- | ----------- | ---------- | ------- |
| 1          | Alfreds Futterkiste                | Maria Anders       | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |

---



### SQL HAVING Examples

---

다음 SQL 문은 각 국가의 고객 수를 나열합니다. 5 명 이상의 고객이 있는 국가만 포함 :



#### Example

```sql
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
HAVING COUNT(CustomerID) > 5;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 5

| COUNT(CustomerID) | Country |
| ----------------- | ------- |
| 9                 | Brazil  |
| 11                | France  |
| 10                | Germany |
| 7                 | UK      |
| 13                | USA     |



다음 SQL 문은 각 국가의 고객 수를 높은 순으로 정렬하여 나열합니다 (고객이 5 명 이상인 국가만 포함):



#### Example

```sql
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
HAVING COUNT(CustomerID) > 5
ORDER BY COUNT(CustomerID) DESC;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 5

| COUNT(CustomerID) | Country |
| ----------------- | ------- |
| 13                | USA     |
| 11                | France  |
| 10                | Germany |
| 9                 | Brazil  |
| 7                 | UK      |

---



### Demo Database

---

아래는 Northwind 샘플 데이터베이스의 "Orders"테이블에서 선택한 것입니다:

| OrderID | CustomerID | EmployeeID | OrderDate  | ShipperID |
| ------- | ---------- | ---------- | ---------- | --------- |
| 10248   | 90         | 5          | 1996-07-04 | 3         |
| 10249   | 81         | 6          | 1996-07-05 | 1         |
| 10250   | 34         | 4          | 1996-07-08 | 2         |



그리고 "Employees"테이블의 선택항목입니다:



| EmployeeID | LastName  | FirstName | BirthDate  | Photo      | Notes                       |
| ---------- | --------- | --------- | ---------- | ---------- | --------------------------- |
| 1          | Davolio   | Nancy     | 1968-12-08 | EmpID1.pic | Education includes a BA.... |
| 2          | Fuller    | Andrew    | 1952-02-19 | EmpID2.pic | Andrew received his BTS.... |
| 3          | Leverling | Janet     | 1963-08-30 | EmpID3.pic | Janet has a BS degree....   |

---



### More HAVING Examples

---

다음 SQL 문은 10 개 이상의 주문을 등록한 직원을 나열합니다:



#### Example

```sql
SELECT Employees.LastName, COUNT(Orders.OrderID) AS NumberOfOrders
FROM (Orders
INNER JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID)
GROUP BY LastName
HAVING COUNT(Orders.OrderID) > 10;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 8

| LastName  | NumberOfOrders |
| --------- | -------------- |
| Buchanan  | 11             |
| Callahan  | 27             |
| Davolio   | 29             |
| Fuller    | 20             |
| King      | 14             |
| Leverling | 31             |
| Peacock   | 40             |
| Suyama    | 18             |



"Davolio"또는 "Fuller"직원이 25 개가 넘는 주문을 등록한 경우 다음 SQL 문에 나열됩니다:



#### Example

```sql
SELECT Employees.LastName, COUNT(Orders.OrderID) AS NumberOfOrders
FROM Orders
INNER JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID
WHERE LastName = 'Davolio' OR LastName = 'Fuller'
GROUP BY LastName
HAVING COUNT(Orders.OrderID) > 25;
```

>[w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Number of Records: 1

| LastName | NumberOfOrders |
| -------- | -------------- |
| Davolio  | 29             |
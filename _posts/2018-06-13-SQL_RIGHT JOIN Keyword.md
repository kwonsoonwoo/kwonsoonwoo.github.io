---
layout: post
title: SQL RIGHT JOIN Keyword
category: SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





### SQL RIGHT JOIN Keyword

---

RIGHT JOIN 키워드는 오른쪽 테이블 (table2)의 모든 레코드와 왼쪽 테이블 (table1)의 일치 레코드를 반환합니다. 일치가없는 경우 왼쪽 결과가 NULL입니다.



####RIGHT JOIN Syntax

```sql
SELECT column_name(S)
FROM table1
RIGHT JOIN table2 ON table1.column_name = table2.column_name;
```
**참고** : 일부 데이터베이스에서는 RIGHT JOIN을 RIGHT OUTER JOIN이라고합니다.

>[홈페이지 그림 참조](https://www.w3schools.com/sql/sql_join_inner.asp)





### Demo Database

---

이 튜토리얼에서는 잘 알려진 Northwind 샘플 데이터베이스를 사용합니다.

다음은 "Orders" 테이블에서 선택한 항목입니다:



| OrderID | CustomerID | EmployeeID | OrderDate  | ShipperID |
| ------- | ---------- | ---------- | ---------- | --------- |
| 10308   | 2          | 7          | 1996-09-18 | 3         |
| 10309   | 37         | 3          | 1996-09-19 | 1         |
| 10310   | 77         | 8          | 1996-09-20 | 2         |



그리고 "Employees" 테이블에서 선택한 항목입니다 :

| EmployeeID | LastName  | FirstName | BirthDate | Photo      |
| ---------- | --------- | --------- | --------- | ---------- |
| 1          | Davolio   | Nancy     | 12/8/1968 | EmpID1.pic |
| 2          | Fuller    | Andrew    | 2/19/1952 | EmpID2.pic |
| 3          | Leverling | Janet     | 8/30/1963 | EmpID3.pic |



### SQL RIGHT JOIN Example

---

다음 SQL 문은 모든 직원과 모든 주문을 반환합니다:



#### Example

```sql
SELECT Orders.OrderID, Employees.LastName, Employees.FirstName
FROM Orders
RIGHT JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID
ORDER BY Orders.OrderID;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것

**참고** : RIGHT JOIN 키워드는 왼쪽 테이블 (Orders)에 일치하는 항목이 없더라도 오른쪽 테이블 (Employees)의 모든 레코드를 반환합니다.



### Result:(일부만 발췌)

Number of Records: 197

| OrderID | LastName  | FirstName |
| ------- | --------- | --------- |
|         | West      | Adam      |
| 10248   | Buchanan  | Steven    |
| 10249   | Suyama    | Michael   |
| 10250   | Peacock   | Margaret  |
| 10251   | Leverling | Janet     |
| 10252   | Peacock   | Margaret  |
| 10253   | Leverling | Janet     |
| 10254   | Buchanan  | Steven    |

**총 197개의 Records가 있음**
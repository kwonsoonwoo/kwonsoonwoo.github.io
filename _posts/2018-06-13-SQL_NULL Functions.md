---
layout: post
title: SQL NULL Functions
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.



### SQL IFNULL(), ISNULL(), COALESCE(), and NVL() Functions

---

다음 "Products" table을 보십시오:

| P_Id | ProductName | UnitPrice | UnitsInStock | UnitsOnOrder |
| ---- | ----------- | --------- | ------------ | ------------ |
| 1    | Jarlsberg   | 10.45     | 16           | 15           |
| 2    | Mascarpone  | 32.56     | 23           |              |
| 3    | Gorgonzola  | 15.67     | 9            | 20           |



"UnitsOnOrder"열이 선택적이며 NULL 값을 포함 할 수 있다고 가정합니다.

다음 SELECT 문을 살펴보십시오.

```sql
SELECT ProductName, UnitPrice * (UnitsInStock + UnitsOnOrder)
FROM Products;
```

위의 예제에서 "UnitsOnOrder"값 중 하나라도 NULL이면 결과는 NULL입니다.



### Solutions

---



**MySQL**



MySQL IFNULL () 함수를 사용하면 표현식이 NULL 인 경우 대체 값을 반환 할 수 있습니다:

```sql
SELECT ProductName, UnitPrice * (UnitsInStock + IFNULL(UnitsOnOrder, 0))
FROM Products
```



또는 다음과 같이 COALESCE () 함수를 사용할 수 있습니다 :

```sql
SELECT ProductName, UnitPrice * (UnitsInStock + COALESCE(UnitsOnOrder, 0))
FROM Products
```



**SQL Server**

SQL Server ISNULL () 함수를 사용하면 식이 NULL 일 때 대체 값을 반환 할 수 있습니다:

```sql
SELECT ProductName, UnitPrice * (UnitsInStock + ISNULL(UnitsOnOrder, 0))
FROM Products
```



**MS Access**

MS Access IsNull () 함수는식이 null 값이면 TRUE (-1)를 반환하고 그렇지 않으면 FALSE (0)을 반환합니다:

```sql
SELECT ProductName, UnitPrice * (UnitsInStock + IIF(IsNull(UnitsOnOrder), 0, UnitsOnOrder))
FROM Products
```



**Oracle**

Oracle NVL () 함수는 동일한 결과를 얻습니다:

```sql
SELECT ProductName, UnitPrice * (UnitsInStock + NVL(UnitsOnOrder, 0))
FROM Products
```


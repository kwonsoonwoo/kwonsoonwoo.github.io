---
layout: post
title: SQL DEFAULT Constraint
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





### SQL DEFAULT Constraint

DEFAULT 제약 조건은 열의 기본값을 제공하는 데 사용됩니다.

다른 값을 지정하지 않으면 기본값이 모든 새 레코드에 추가됩니다.

---



### SQL DEFAULT on CREATE TABLE

다음 SQL은 "Persons" 테이블을 만들 때 "City"열의 DEFAULT 값을 설정합니다:

**MySQL / SQL Server / Oracle / MS Access:**

```sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    City varchar(255) DEFAULT 'Sandnes'
);
```



DEFAULT 제약 조건은 GETDATE ()와 같은 함수를 사용하여 시스템 값을 삽입하는 데에도 사용할 수 있습니다:

```sql
CREATE TABLE Orders (
    ID int NOT NULL,
    OrderNumber int NOT NULL,
    OrderDate date DEFAULT GETDATE()
);
```

---



### SQL DEFAULT on ALTER TABLE

테이블이 이미 만들어 졌을 때 "City"열에 DEFAULT 제약 조건을 만들려면 다음 SQL을 사용하십시오:

**MySQL :**

```sql
ALTER TABLE Persons
ALTER City SET DEFAULT 'Sandnes';
```

**SQL Server / MS Access:**

```sql
ALTER TABLE Persons
ALTER COLUMN City SET DEFAULT 'Sandnes';
```

**Oracle:**

```sql
ALTER TABLE Persons
MODIFY City DEFAULT 'Sandnes';
```

---



### DROP a DEFAULT Constraint

DEFAULT 제약 조건을 삭제하려면 다음 SQL을 사용하십시오:


**MySQL:**

```sql
ALTER TABLE Persons
ALTER City DROP DEFAULT;
```

**SQL Server / Oracle / MS Access:**

```sql
ALTER TABLE Persons
ALTER COLUMN City DROP DEFAULT;
```

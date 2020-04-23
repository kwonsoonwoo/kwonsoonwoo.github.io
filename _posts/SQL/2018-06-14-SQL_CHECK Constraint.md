---
layout: post
title: SQL CHECK Constraint
category: SQL
tags:
  - SQL
  - SQL CHECK Constraint
  - SQL CHECK 제약조건
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





### SQL CHECK Constraint

CHECK 제약 조건은 열에 배치 할수 있는 값 범위를 제한하는 데 사용됩니다.

단일 열에 CHECK 제한 조건을 정의하면 이 열에 대해 특정 값만 허용됩니다.

테이블에 CHECK 제한 조건을 정의하면 행의 다른 컬럼에있는 값을 기준으로 특정 컬럼의 값을 제한 할 수 있습니다.

---



### SQL CHECK on CREATE TABLE

다음 SQL은 "Persons" 테이블이 작성 될 때 "Age" 컬럼에 CHECK 제한 조건을 작성합니다. CHECK 제약 조건은 18 세 미만의 사람을 가질 수 없도록 보장합니다:



**MySQL:**

```sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int CHECK (Age>=18)
);
```



**SQL Server / Oracle / MS Access:**

```sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int CHECK (Age>=18)
);
```



CHECK 제약 조건의 이름 지정 및 여러 열에 대한 CHECK 제약 조건 정의를 허용하려면 다음 SQL 구문을 사용하십시오:



**MySQL / SQL Server / Oracle / MS Access:**

```sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    City varchar(255),
    CONSTRAINT CHK_Person CHECK (Age>=18 AND City='Sandnes')
);
```

---



### SQL CHECK on ALTER TABLE

테이블이 이미 생성 된 경우 "Age"열에 CHECK 제약 조건을 만들려면 다음 SQL을 사용하십시오:

**MySQL / SQL Server / Oracle / MS Access:**

```sql
ALTER TABLE Persons
ADD CHECK (Age>=18);
```



CHECK 제약 조건의 이름 지정 및 여러 열에 대한 CHECK 제약 조건 정의를 허용하려면 다음 SQL 구문을 사용하십시오:

**MySQL / SQL Server / Oracle / MS Access:**

```sql
ALTER TABLE Persons
ADD CONSTRAINT CHK_PersonAge CHECK (Age>=18 AND City='Sandnes');
```

---



### DROP a CHECK Constraint

CHECK 제약 조건을 삭제하려면 다음 SQL을 사용하십시오:


**SQL Server / Oracle / MS Access:**

```sql
ALTER TABLE Persons
DROP CONSTRAINT CHK_PersonAge;
```

**MySQL:**

```sql
ALTER TABLE Persons
DROP CHECK CHK_PersonAge;
```


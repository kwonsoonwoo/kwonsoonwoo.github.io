---
layout: post
title: SQL UNIQUE Constraint
category: SQL
tags:
  - SQL
  - SQL UNIQUE Constraint
  - SQL UNIQUE 제약조건
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





### SQL UNIQUE Constraint

UNIQUE 제약 조건은 열의 모든 값이 서로 다른지 확인합니다.

UNIQUE 및 PRIMARY KEY 제약 조건은 열 또는 열 집합의 고유성을 보장합니다.

PRIMARY KEY 제약 조건에는 자동으로 UNIQUE 제약 조건이 있습니다.

그러나 테이블 당 UNIQUE 제약 조건은 많이 가질 수 있지만 PRIMARY KEY 제약 조건은 하나만 가질 수 있습니다.

---



### SQL UNIQUE Constraint on CREATE TABLE

다음 SQL은 "Person"테이블을 만들 때 "ID"열에 UNIQUE 제약 조건을 만듭니다:



**SQL Server / Oracle / MS Access:**

```sql
CREATE TABLE Persons (
	ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
```



**MySQL:**

```sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    UNIQUE (ID)
);
```

UNIQUE 제약 조건의 이름을 지정하고 여러 열에 UNIQUE 제약 조건을 정의하려면 다음 SQL 구문을 사용하십시오.:



**MySQL / SQL Server / Oracle / MS Access:**

```sql
CREATE TABLE Persons (
	ID int NOT NULL,
	LastName varchar(255) NOT NULL,
	FirstName varchar(255),
	Age int,
	CONSTRAINT UC_Person UNIQUE (ID,LastName)
);
```

---



### SQL UNIQUE Constraint on ALTER TABLE

테이블이 이미 만들어 졌을 때 "ID"열에 UNIQUE 제약 조건을 만들려면 다음 SQL을 사용하십시오:

**MySQL / SQL Server / Oracle / MS Access:**

```sql
ALTER TABLE Persons
ADD UNIQUE (ID);
```



UNIQUE 제약 조건의 이름을 지정하고 여러 열에 UNIQUE 제약 조건을 정의하려면 다음 SQL 구문을 사용하십시오:

**MySQL / SQL Server / Oracle / MS Access:**

```sql
ALTER TABLE Persons
ADD CONSTRAINT UC_Person UNIQUE (ID,LastName);
```

---



### DROP a UNIQUE Constraint

UNIQUE 제약 조건을 삭제하려면 다음 SQL을 사용하십시오:

**MySQL:**

```sql
ALTER TABLE Persons
DROP INDEX UC_Person;
```



**SQL Server / Oracle / MS Access:**

```sql
ALTER TABLE Persons
DROP CONSTRAINT UC_Person;
```





### Result:

Error 1: could not prepare statement (1 table Persons already exists)



> **Tip**: 테이블이 이미 작성된 경우, [ALTER TABLE](https://www.w3schools.com/sql/sql_alter.asp) 문으로 컬럼에 NOT NULL 제한 조건을 추가 할 수 있습니다.
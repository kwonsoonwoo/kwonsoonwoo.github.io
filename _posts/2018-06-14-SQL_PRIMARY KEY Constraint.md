---
layout: post
title: SQL PRIMARY KEY Constraint
category: SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





### SQL PRIMARY KEY Constraint

PRIMARY KEY 제약 조건은 데이터베이스 테이블의 각 레코드를 고유하게 식별합니다.

Primary 키는 UNIQUE 값을 포함해야하며 NULL 값을 포함 할 수 없습니다.

테이블에는 기본 키가 하나만 있을 수 있고 기본 키는 하나 또는 여러 개의 필드로 구성 될 수 있습니다.

---



### SQL PRIMARY KEY on CREATE TABLE

다음 SQL은 "Persons"테이블이 생성 될 때 "ID"열에 PRIMARY KEY를 만듭니다:



**MySQL:**

```sql
CREATE TABLE Persons (
	ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (ID)
);
```



**SQL Server / Oracle / MS Access:**

```sql
CREATE TABLE Persons (
    ID int NOT NULL PRIMARY KEY,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
```



PRIMARY KEY 제약 조건의 이름 지정을 허용하고 여러 열에 대해 PRIMARY KEY 제약 조건을 정의하려면 다음 SQL 구문을 사용합니다:



**MySQL / SQL Server / Oracle / MS Access:**

```sql
CREATE TABLE Persons (
	ID int NOT NULL,
	LastName varchar(255) NOT NULL,
	FirstName varchar(255),
	Age int,
	CONSTRAINT PK_Person PRIMARY KEY (ID,LastName)
);
```

**Note**: 위의 예에서는 오직 하나의 PRIMARY KEY (PK_Person) 만 있습니다. 그러나 기본 키의 VALUE는 두 개의 COLUMNS (ID + 성)로 구성됩니다.

---



### SQL PRIMARY KEY on ALTER TABLE

테이블이 이미 만들어 졌을 때 "ID"열에 PRIMARY KEY 제약 조건을 만들려면 다음 SQL을 사용하십시오:

**MySQL / SQL Server / Oracle / MS Access:**

```sql
ALTER TABLE Persons
ADD PRIMARY KEY (ID);
```



PRIMARY KEY 제약 조건의 이름 지정을 허용하고 여러 열에 대해 PRIMARY KEY 제약 조건을 정의하려면 다음 SQL 구문을 사용합니다:

**MySQL / SQL Server / Oracle / MS Access:**

```sql
ALTER TABLE Persons
ADD CONSTRAINT PK_Person PRIMARY KEY (ID,LastName);
```

**Note**: ALTER TABLE 문을 사용하여 기본 키를 추가하는 경우 기본 키 열은 (테이블이 처음 작성되었을 때) NULL 값을 포함하지 않도록 이미 선언되어 있어야합니다.

---



### DROP a PRIMARY KEY Constraint

PRIMARY KEY 제약 조건을 삭제하려면 다음 SQL을 사용하십시오:

**MySQL:**

```sql
ALTER TABLE Persons
DROP PRIMARY KEY;
```



**SQL Server / Oracle / MS Access:**

```sql
ALTER TABLE Persons
DROP CONSTRAINT PK_Person;
```


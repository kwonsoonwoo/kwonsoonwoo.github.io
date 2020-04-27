---
layout: post
title: SQL CREATE TABLE Statement
category: SQL
tags:
  - SQL
  - SQL CREATE TABLE Statement
  - SQL CREATE TABLE 문
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.



### The SQL CREATE TABLE Statement

---

CREATE TABLE 문은 데이터베이스에 새 테이블을 만드는 데 사용됩니다.



#### Syntax

```sql
CREATE TABLE table_name (
	column1 datatype,
	column2 datatype,
	column3 datatype,
	....
);
```

column 매개 변수는 테이블의 열 이름을 지정합니다.

datatype 매개 변수는 열에서 보유 할 수있는 데이터 유형 (예 : varchar, 정수, 날짜 등)을 지정합니다.

**Tip**: 사용 가능한 데이터 유형에 대한 개요는 [전체 데이터 유형 참조](https://www.w3schools.com/sql/sql_datatypes.asp)로 이동하십시오.



### SQL CREATE TABLE Example

---

다음 예에서는 PersonID, LastName, FirstName, Address 및 City라는 다섯 개의 열이 포함 된 "Persons"라는 테이블을 만듭니다:



#### Example

```sql
CREATE TABLE Persons (
	PersonID int,
	LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255)
);
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

You have made changes to the database.

(데이터베이스를 변경했습니다.)



PersonID 열은 int 유형이며 정수를 포함합니다.

LastName, FirstName, Address 및 City 열은 varchar 유형으로 문자를 포함하며 이 필드의 최대 길이는 255 자입니다.



빈 "Persons"테이블은 이제 다음과 같이 보입니다:

| PersonID | LastName | FirstName | Address | City |
| -------- | -------- | --------- | ------- | ---- |
|          |          |           |         |      |

**Tip**: 이제 빈 "Persons"테이블을 SQL [INSERT INTO](https://www.w3schools.com/sql/sql_insert.asp) 문으로 데이터로 채울 수 있습니다.

---



### Create Table Using Another Table

기존 테이블의 사본은 CREATE TABLE 문과 SELECT 문의 조합을 사용하여 작성할 수 있습니다.

새 테이블은 동일한 열 정의를 가져옵니다. 모든 열 또는 특정 열을 선택할 수 있습니다.

기존 테이블을 사용하여 새 테이블을 만들면 새 테이블은 이전 테이블의 기존 값으로 채워집니다.



#### Syntax

```sql
CREATE TABLE new_table_name AS
	SELECT column1, column2, ...
	FROM existing_table_name
	WHERE ....;
```


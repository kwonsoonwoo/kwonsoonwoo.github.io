---
layout: post
title: SQL ALTER TABLE Statement
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.



### SQL ALTER TABLE Statement

ALTER TABLE 문은 기존 테이블의 열을 추가, 삭제 또는 수정하는 데 사용됩니다.

ALTER TABLE 문은 기존 테이블에 다양한 제한 조건을 추가,삭제하는 데에도 사용됩니다.

---



###ALTER TABLE - ADD Column

테이블에 열을 추가하려면 다음 구문을 사용하십시오.

```sql
ALTER TABLE table_name
ADD column_name datatype;
```

---



### ALTER TABLE - DROP Column

테이블의 열을 삭제하려면 다음 구문을 사용하십시오 (일부 데이터베이스 시스템에서는 열 삭제가 허용되지 않음):

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

---

### ALTER TABLE - ALTER/MODIFY Column

테이블에 있는 열의 데이터 형식을 변경하려면 다음 구문을 사용합니다:



**SQL Server / MS Access:**

```sql
ALTER TABLE table_name
ALTER COLUMN column_name datatype;
```



**My SQL / Oracle (prior version 10G):**

```sql
ALTER TABLE table_name
MODIFY COLUMN column_name datatype;
```



**Oracle 10G and later:**

```sql
ALTER TABLE table_name
MODIFY column_name datatype;
```

---



### SQL ALTER TABLE Example

"Persons" 테이블을 보십시오:

| ID   | LastName  | FirstName | Address      | City      |
| ---- | --------- | --------- | ------------ | --------- |
| 1    | Hansen    | Ola       | Timoteivn 10 | Sandnes   |
| 2    | Svendson  | Tove      | Borgvn 23    | Sandnes   |
| 3    | Pettersen | Kari      | Storgt 20    | Stavanger |



이제 "Persons"테이블에 "DateOfBirth"라는 열을 추가하려고합니다.

다음 SQL 문을 사용합니다:

```sql
ALTER TABLE Persons
ADD DateOfBirth date;
```

새 열 "DateOfBirth"는 date 유형이며 날짜를 보유합니다. 데이터 유형은 컬럼이 보유 할 수 있는 데이터 유형을 지정합니다. MS Access, MySQL 및 SQL Server에서 사용할 수있는 모든 데이터 유형에 대한 완벽한 참조는 [전체 데이터 유형 참조](https://www.w3schools.com/sql/sql_datatypes.asp)로 이동하십시오.

'Persons' 테이블은 이제 다음과 같이 보입니다:

| ID   | LastName  | FirstName | Address      | City      | DateOfBirth |
| ---- | --------- | --------- | ------------ | --------- | ----------- |
| 1    | Hansen    | Ola       | Timoteivn 10 | Sandnes   |             |
| 2    | Svendson  | Tove      | Borgvn 23    | Sandnes   |             |
| 3    | Pettersen | Kari      | Storgt 20    | Stavanger |             |

---



### Change Data Type Example

이제 "Persons"테이블에서 "DateOfBirth"라는 열의 데이터 유형을 변경하려고 합니다.

다음 SQL 문을 사용합니다:

```sql
ALTER TABLE Persons
ALTER COLUMN DateOfBirth year;
```

"DateOfBirth"열은 이제 year 형식이며 2 자리 또는 4 자리 형식으로 연도를 유지합니다.

---



### DROP COLUMN Example

다음으로 "Persons"테이블에서 "DateOfBirth"라는 열을 삭제하려고 합니다.

다음 SQL 문을 사용합니다:

```sql
ALTER TABLE Persons
DROP COLUMN DateOfBirth;
```



"Persons" 테이블은 이제 다음과 같이 보입니다:

| ID   | LastName  | FirstName | Address      | City      |
| ---- | --------- | --------- | ------------ | --------- |
| 1    | Hansen    | Ola       | Timoteivn 10 | Sandnes   |
| 2    | Svendson  | Tove      | Borgvn 23    | Sandnes   |
| 3    | Pettersen | Kari      | Storgt 20    | Stavanger |
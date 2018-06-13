---
layout: post
title: SQL NOT NULL Constraint
category: SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





### SQL NOT NULL Constraint

기본적으로 열은 NULL 값을 포함 할 수 있습니다.

NOT NULL 제약 조건은 열이 NULL 값을 허용하지 않도록 강제합니다.

이렇게하면 필드에 항상 값이 포함될 수 있습니다. 즉, 새 레코드를 삽입하거나 이 필드에 값을 추가하지 않고 레코드를 업데이트 할 수 없습니다.

다음 SQL은 "ID", "LastName"및 "FirstName"열이 NULL 값을 허용하지 않도록 합니다:



#### Example

```sql
CREATE TABLE Persons (
	ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Age int
);
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

Error 1: could not prepare statement (1 table Persons already exists)



> **Tip**: 테이블이 이미 작성된 경우, [ALTER TABLE](https://www.w3schools.com/sql/sql_alter.asp) 문으로 컬럼에 NOT NULL 제한 조건을 추가 할 수 있습니다.
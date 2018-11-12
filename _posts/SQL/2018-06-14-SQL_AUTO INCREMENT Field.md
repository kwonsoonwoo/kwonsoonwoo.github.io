---
layout: post
title: SQL AUTO INCREMENT Field
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.



####  AUTO INCREMENT Field

Auto-increment는 새 레코드가 테이블에 삽입 될 때 고유 번호가 자동으로 생성되도록 합니다.

종종 이것은 새로운 레코드가 삽입 될 때마다 자동으로 생성되기를 원하는 기본 키 필드입니다.

---



#### Syntax for MySQL

다음 SQL 문은 "Persons" 테이블의 자동 증가 기본 키 필드로 "ID"열을 정의합니다.

```sql
CREATE TABLE Persons (
    ID int NOT NULL AUTO_INCREMENT,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (ID)
);
```

MySQL은 AUTO_INCREMENT 키워드를 사용하여 자동 증가 기능을 수행합니다.

기본적으로 AUTO_INCREMENT의 시작 값은 1이며 새 레코드마다 1 씩 증가합니다.



AUTO_INCREMENT 시퀀스를 다른 값으로 시작하려면 다음 SQL 문을 사용하십시오:

```sql
ALTER TABLE Persons AUTO_INCREMENT=100;
```



"Persons"테이블에 새 레코드를 삽입하려면 "ID"열에 값을 지정할 필요가 없습니다 (고유 한 값이 자동으로 추가됩니다):

```sql
INSERT INTO Persons (FirstName,LastName)
VALUES ('Lars','Monsen');
```



위의 SQL 문은 "Persons"테이블에 새 레코드를 삽입합니다. "ID"열에 고유 한 값이 할당됩니다. "FirstName"열은 "Lars"로 설정되고 "LastName"열은 "Monsen"으로 설정됩니다.

---



### Syntax for SQL Server

다음 SQL 문은 "Persons" 테이블의 자동 증가 기본 키 필드로 "ID"열을 정의합니다:

```sql
CREATE TABLE Persons (
    ID int IDENTITY(1,1) PRIMARY KEY,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
```

MS SQL Server는 IDENTITY 키워드를 사용하여 자동 증가 기능을 수행합니다.

위의 예에서 IDENTITY의 시작 값은 1이며 새 레코드마다 1 씩 증가합니다.

**Tip:** "ID"열이 값 10에서 시작하여 5 씩 증가하도록 지정하려면 IDENTITY (10,5)로 변경하십시오.



"Persons"테이블에 새 레코드를 삽입하려면 "ID"열에 값을 지정할 필요가 없습니다 (고유 한 값이 자동으로 추가됩니다):

```sql
INSERT INTO Persons (FirstName,LastName)
VALUES ('Lars','Monsen');
```

위의 SQL 문은 "Persons"테이블에 새 레코드를 삽입합니다. "ID"열에 고유 한 값이 할당됩니다. "FirstName"열은 "Lars"로 설정되고 "LastName"열은 "Monsen"으로 설정됩니다.

---



### Syntax for Access

다음 SQL 문은 "Person"테이블의 자동 증가 기본 키 필드로 "ID"열을 정의합니다:

```sql
CREATE TABLE Persons (
    ID Integer PRIMARY KEY AUTOINCREMENT,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
```

MS Access는 AUTOINCREMENT 키워드를 사용하여 자동 증가 기능을 수행합니다.

기본적으로 AUTOINCREMENT의 시작 값은 1이며 새 레코드마다 1 씩 증가합니다.

**Tip:** "ID"열이 값 10에서 시작하여 5 씩 증가하도록 지정하려면 자동 증가를 AUTOINCREMENT (10,5)로 변경하십시오.



"Persons"테이블에 새 레코드를 삽입하려면 "ID"열에 값을 지정할 필요가 없습니다 (고유 한 값이 자동으로 추가됩니다).

```sql
INSERT INTO Persons (FirstName,LastName)
VALUES ('Lars','Monsen');
```

위의 SQL 문은 "Persons"테이블에 새 레코드를 삽입합니다. "P_Id"열에 고유 한 값이 할당됩니다. "FirstName"열은 "Lars"로 설정되고 "LastName"열은 "Monsen"으로 설정됩니다.

---



### Syntax for Oracle

오라클에서는 코드가 좀 더 까다롭습니다.

시퀀스 객체로 자동 증가 필드를 만들어야합니다 (이 객체는 숫자 시퀀스를 생성합니다).

다음 CREATE SEQUENCE 구문을 사용하십시오:

```sql
CREATE SEQUENCE seq_person
MINVALUE 1
START WITH 1
INCREMENT BY 1
CACHE 10;
```

위의 코드는 seq_person이라는 시퀀스 객체를 생성합니다. seq_person은 1부터 시작하여 1 씩 증가합니다. 또한 성능을 위해 최대 10 개의 값을 캐시합니다. 캐시 옵션은 더 빠른 액세스를 위해 얼마나 많은 순서 값이 메모리에 저장 될지 지정합니다.



"Persons"테이블에 새 레코드를 삽입하려면 nextval 함수를 사용해야합니다 (이 함수는 seq_person 시퀀스에서 다음 값을 검색합니다):

```sql
INSERT INTO Persons (ID,FirstName,LastName)
VALUES (seq_person.nextval,'Lars','Monsen');
```

위의 SQL 문은 "Persons"테이블에 새 레코드를 삽입합니다. "ID"열에는 seq_person 시퀀스의 다음 번호가 할당됩니다.

"FirstName"열은 "Lars"로 설정되고 "LastName"열은 "Monsen"으로 설정됩니다.
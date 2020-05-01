---
layout: post
title: SQL FOREIGN KEY Constraint
category: SQL
tags:
  - SQL
  - SQL FOREIGN KEY Constraint
  - SQL FOREIGN KEY 제약조건
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.





### SQL FOREIGN KEY Constraint

FOREIGN KEY는 두 테이블을 서로 연결하는 데 사용되는 키입니다.

FOREIGN KEY는 다른 테이블의 PRIMARY KEY를 참조하는 테이블의 필드 (또는 필드 모음)입니다.

foreign key가 들어있는 테이블을 하위 테이블이라고하고 후보 키가 들어있는 테이블을 참조 된 테이블 또는 상위 테이블이라고합니다.

다음 두 테이블을 보십시오:



"Persons" table:

| PersonID | LastName  | FirstName | Age  |
| -------- | --------- | --------- | ---- |
| 1        | Hansen    | Ola       | 30   |
| 2        | Svendson  | Tove      | 23   |
| 3        | Pettersen | Kari      | 20   |



"Orders" table:

| OrderID | OrderNumber | PersonID |
| ------- | ----------- | -------- |
| 1       | 77895       | 3        |
| 2       | 44678       | 3        |
| 3       | 22456       | 2        |
| 4       | 24562       | 1        |

"Orders"테이블의 "PersonID"열이 "Persons"테이블의 "PersonID"열을 가리키는 것을 확인하십시오.

"Persons"테이블의 "PersonID"열은 "Person"테이블의 PRIMARY KEY입니다.

"Orders"테이블의 "PersonID"열은 "Orders"테이블의 FOREIGN KEY입니다.

FOREIGN KEY 제약 조건은 테이블 간의 연결이 끊어지는 작업을 방지하는 데 사용됩니다.

FOREIGN KEY 제약 조건은 또한 가리키는 테이블에 포함 된 값 중 하나 여야하기 때문에 잘못된 데이터가 foreign key 열에 삽입되는 것을 방지합니다.

---





### SQL FOREIGN KEY on CREATE TABLE

다음 SQL은 "Orders" 테이블을 만들 때 "PersonID"열에 FOREIGN KEY를 만듭니다:



**MySQL:**

```sql
CREATE TABLE Orders (
	OrderID int NOT NULL,
    OrderNumber int NOT NULL,
    PersonID int,
    PRIMARY KEY (OrderID),
    FOREIGN KEY (PersonID) REFERENCES Persons(PersonID)
);
```



**SQL Server / Oracle / MS Access:**

```sql
CREATE TABLE Orders (
    OrderID int NOT NULL PRIMARY KEY,
    OrderNumber int NOT NULL,
    PersonID int FOREIGN KEY REFERENCES Persons(PersonID)
);
```



FOREIGN KEY 제약 조건의 이름 지정 및 여러 열의 FOREIGN KEY 제약 조건 정의를 허용하려면 다음 SQL 구문을 사용합니다:



**MySQL / SQL Server / Oracle / MS Access:**

```sql
CREATE TABLE Orders (
	OrderID int NOT NULL,
	OrderNumber int NOT NULL,
	PersonID int,
	PRIMARY KEY (OrderID),
	CONSTRAINT FK_PersonOrder FOREIGN KEY (PersonID)
    REFERENCES Persons(PersonID)
);
```

---



### SQL FOREIGN KEY on ALTER TABLE

"Orders" 테이블이 이미 생성 된 경우 "PersonID"열에 FOREIGN KEY 제약 조건을 만들려면 다음 SQL을 사용하십시오:

**MySQL / SQL Server / Oracle / MS Access:**

```sql
ALTER TABLE Orders
ADD FOREIGN KEY (PersonID) REFERENCES Persons(PersonID);
```



FOREIGN KEY 제약 조건의 이름 지정 및 여러 열의 FOREIGN KEY 제약 조건 정의를 허용하려면 다음 SQL 구문을 사용합니다:

**MySQL / SQL Server / Oracle / MS Access:**

```sql
ALTER TABLE Orders
ADD CONSTRAINT FK_PersonOrder 
FOREIGN KEY (PersonID) REFERENCES Persons(PersonID);
```

---



### DROP a FOREIGN KEY Constraint

FOREIGN KEY 제약 조건을 삭제하려면 다음 SQL을 사용하십시오:

**MySQL:**

```sql
ALTER TABLE Orders
DROP FOREIGN KEY FK_PersonOrder;
```



**SQL Server / Oracle / MS Access:**

```sql
ALTER TABLE Orders
DROP CONSTRAINT FK_PersonOrder;
```


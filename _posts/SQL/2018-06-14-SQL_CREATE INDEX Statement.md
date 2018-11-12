---
layout: post
title: SQL CREATE INDEX Statement
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.



####  CREATE INDEX Syntax

테이블에 인덱스를 만듭니다. 중복 된 값이 허용됩니다:

```sql
CREATE INDEX index_name
ON table_name (column1, column2, ...);
```



#### CREATE UNIQUE INDEX Syntax

테이블에 고유 인덱스를 작성합니다. 중복 값은 허용되지 않습니다.

```sql
CREATE UNIQUE INDEX index_name
ON table_name (column1, column2, ...);
```

**Note:** 인덱스를 만드는 구문은 데이터베이스마다 다릅니다. 따라서 데이터베이스의 인덱스 작성 구문을 확인하십시오.

---



### CREATE INDEX Example

아래의 SQL 문은 "Persons"테이블의 "LastName"열에 "idx_lastname"이라는 인덱스를 만듭니다:

```sql
CREATE INDEX idx_lastname
ON Persons (LastName);
```



열의 조합에 대해 색인을 작성하려면 괄호 안에 쉼표로 구분 된 열 이름을 나열 할 수 있습니다:

```sql
CREATE INDEX idx_pname
ON Persons (LastName, FirstName);
```

---



### DROP INDEX Statement

DROP INDEX 문은 테이블의 인덱스를 삭제하는 데 사용됩니다:

**MS Access :**

```sql
DROP INDEX index_name ON table_name;
```

**SQL Server:**

```sql
DROP INDEX table_name.index_name;
```

**DB2/Oracle:**

```sql
DROP INDEX index_name;
```

**MySQL:**

```sql
ALTER TABLE table_name
DROP INDEX index_name;
```


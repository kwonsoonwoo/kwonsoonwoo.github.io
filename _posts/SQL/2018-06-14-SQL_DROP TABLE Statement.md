---
layout: post
title: SQL DROP TABLE Statement
category: SQL
tags:
  - SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.



### The SQL DROP TABLE Statement

DROP TABLE 문은 데이터베이스의 기존 테이블을 삭제하는 데 사용됩니다.



#### Syntax

```sql
DROP TABLE table_name;
```

> **Note**: 테이블을 삭제하기 전에 주의하십시오. 테이블을 삭제하면 테이블에 저장된 완전한 정보가 손실됩니다!

---



### SQL DROP TABLE Example

다음 SQL 문은 기존 테이블 "Shippers"를 삭제합니다:



#### Example

```sql
DROP TABLE Shippers;
```

> [w3schools.com](www.w3schools.com/sql)에서 직접 실행해볼것



### Result:

You have made changes to the database.

(데이터베이스를 변경했습니다.)

---



### SQL TRUNCATE TABLE

TRUNCATE TABLE 문은 테이블 내부의 데이터는 삭제하지만 테이블 자체는 삭제하지 않습니다.



#### Syntax

```sql
TRUNCATE TABLE table_name;
```


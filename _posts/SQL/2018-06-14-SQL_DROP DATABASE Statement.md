---
layout: post
title: SQL DROP DATABASE Statement
category: SQL
tags:
  - SQL
  - SQL DROP DATABASE Statement
  - SQL DATABASE 삭제문
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.



### The SQL DROP DATABASE Statement

---

DROP DATABASE 문은 기존 SQL 데이터베이스를 삭제하는 데 사용됩니다.



#### Syntax

```sql
DROP DATABASE databasename;
```

> **Note** : 데이터베이스를 삭제하기 전에 주의하십시오. 데이터베이스를 삭제하면 데이터베이스에 저장된 전체 정보가 손실됩니다.



### DROP DATABASE Example

---

다음 SQL 문은 기존 데이터베이스 "testDB"를 삭제합니다:



#### Example

```sql
DROP DATABASE testDB;
```

>**Tip** : 데이터베이스를 삭제하기 전에 관리자 권한이 있어야합니다. 데이터베이스가 삭제되면 다음 SQL 명령을 사용하여 데이터베이스 목록에서 데이터베이스를 확인할 수 있습니다. SHOW DATABASES;
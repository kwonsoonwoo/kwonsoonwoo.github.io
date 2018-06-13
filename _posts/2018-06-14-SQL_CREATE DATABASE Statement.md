---
layout: post
title: SQL CREATE DATABASE Statement
category: SQL
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.



### The SQL CREATE DATABASE Statement

---

CREATE DATABASE 문은 새 SQL 데이터베이스를 만드는 데 사용됩니다.



#### Syntax

```sql
CREATE DATABASE databasename;
```





### CREATE DATABASE Example

---

다음 SQL 문은 "testDB"라는 데이터베이스를 생성합니다:



#### Example

```sql
CREATE DATABASE testDB;
```

>**Tip** : 데이터베이스를 만들기 전에 관리자 권한이 있어야합니다. 데이터베이스가 생성되면 다음 SQL 명령을 사용하여 데이터베이스 목록에서 데이터베이스를 확인할 수 있습니다. SHOW DATABASES;
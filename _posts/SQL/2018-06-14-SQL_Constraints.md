---
layout: post
title: SQL Constraints
category: SQL
tags:
  - SQL
  - SQL Constraints
  - SQL 제약조건
---



[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.



---

SQL 제한 조건은 테이블의 데이터에 대한 규칙을 지정하는 데 사용됩니다.

---



### SQL Create Constraints

CREATE TABLE 문으로 테이블이 작성 될 때 또는 ALTER TABLE 문으로 테이블이 작성된 후에 제한 조건을 지정할 수 있습니다.



#### Syntax

```sql
CREATE TABLE table_name (
	column1 datatype constrait,
	column2 datatype constrait,
	column3 datatype constrait,
	....
);
```

---



### SQL Constraints

SQL 제약 조건은 테이블의 데이터에 대한 규칙을 지정하는 데 사용됩니다.

제약 조건은 테이블에 들어갈 수 있는 데이터 유형을 제한하는 데 사용됩니다. 이렇게하면 표의 데이터 정확성과 신뢰성이 보장됩니다. 제한 조건과 데이터 조치 사이에 위반이 있으면 조치가 중단됩니다.

제약 조건은 열 수준 또는 테이블 수준 일 수 있습니다. 컬럼 레벨 제한 조건은 컬럼에 적용되고 테이블 레벨 제한 조건은 전체 테이블에 적용됩니다.

SQL에서 일반적으로 사용되는 다음 제약 조건이 있습니다:

- [NOT NULL](https://www.w3schools.com/sql/sql_notnull.asp) - 열이 NULL 값을 가질 수 없음을 보장합니다.
- [UNIQUE](https://www.w3schools.com/sql/sql_unique.asp) - 한 열에 있는 모든 값이 다른지 확인합니다.
- [PRIMARY KEY](https://www.w3schools.com/sql/sql_primarykey.asp) - NOT NULL과 UNIQUE의 조합. 테이블의 각 행을 고유하게 식별합니다.
- [FOREIGN KEY](https://www.w3schools.com/sql/sql_foreignkey.asp) - 다른 테이블의 행 / 레코드를 고유하게 식별합니다.
- [CHECK](https://www.w3schools.com/sql/sql_check.asp) - 한 열의 모든 값이 특정 조건을 만족하는지 확인합니다.
- [DEFAULT](https://www.w3schools.com/sql/sql_default.asp) - 값이 지정되지 않은 경우 열의 기본값을 설정합니다.
- [INDEX](https://www.w3schools.com/sql/sql_create_index.asp) - 데이터베이스에서 매우 신속하게 데이터를 작성하고 검색하는 데 사용됩니다.


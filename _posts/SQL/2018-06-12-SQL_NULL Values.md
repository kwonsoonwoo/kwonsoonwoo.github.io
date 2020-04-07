---
layout: post
title: SQL NULL Values(티스토리 이전)
category: SQL
tags:
  - SQL
  - SQL NULL
  - SQL IS NULL
  - SQL IS NOT NULL
---



[여기로 이동](https://lifetutorial.tistory.com/26)



<!--

[w3schools.com](www.w3schools.com/sql) 을 참조하여 해석해본 자료입니다.

기본적으로 실행문의 결과값은 사이트에 직접가서 실행해보고 결과를 확인하는것이 좋습니다.

결과값이 너무 큰 경우 일부만 발췌하거나 기록하지 않았습니다.







## What is a NULL Value?

---



NULL 값이 있는 필드는 값이 없는 필드입니다.

테이블의 필드가 선택적이면 이 필드에 값을 추가하지 않고 새 레코드를 삽입하거나 레코드를 업데이트 할 수 있습니다. 그런 다음 필드는 NULL 값으로 저장됩니다.

>참고 : NULL 값이 0 값 또는 공백이있는 필드와 다른 것을 이해하는 것이 매우 중요합니다. NULL 값이있는 필드는 레코드를 생성하는 동안 비어있는 필드입니다!!!





## How to Test for NULL Values?

---



=, <또는 <>과 같은 비교 연산자로 NULL 값을 테스트 할 수 없습니다.

대신에 IS NULL 연산자와 IS NOT NULL 연산자를 사용해야합니다.



### IS NULL Syntax

```sql
SELECT column_names
FROM table_name
WHERE column_name IS NULL;
```





### IS NOT NULL Syntax

```sql
SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
```







## Demo Database

---



다음의 "Person" 테이블이 있다고 가정합니다:



| ID   | LastName | FirstName | Address            | City     |
| ---- | -------- | --------- | ------------------ | -------- |
| 1    | Doe      | John      | 542 W. 27th Street | New York |
| 2    | Bloggs   | Joe       |                    | London   |
| 3    | Roe      | Jane      |                    | New York |
| 4    | Smith    | John      | 110 Bishopsgate    | London   |



"Persons" 테이블의 "Address" 열이 선택 사항이라고 가정합니다. "Address"에 값이없는 레코드가 삽입되면 "Address"열은 NULL 값으로 저장됩니다.





## The IS NULL Operator

---



다음 SQL 문은 IS NULL 연산자를 사용하여 주소가없는 모든 사람들을 나열합니다.

```sql
SELECT LastName, FirstName, Address FROM Persons
WHERE Address IS NULL;
```



결과 세트는 다음과 같습니다:



| LastName | FirstName | Address |
| -------- | --------- | ------- |
| Bloggs   | Joe       |         |
| Roe      | Jane      |         |



> 팁 : NULL 값을 찾으려면 항상 IS NULL을 사용하십시오.







## The IS NOT NULL Operator

---



다음 SQL 문은 IS NOT NULL 연산자를 사용하여 주소가 있는 모든 사람을 나열합니다.

```sql
SELECT LastName, FirstName, Address FROM Persons
WHERE Address IS NOT NULL;
```



결과 세트는 다음과 같습니다:



| LastName | FirstName | Address            |
| -------- | --------- | ------------------ |
| Doe      | John      | 542 W. 27th Street |
| Smith    | John      | 110 Bishopsgate    |

-->
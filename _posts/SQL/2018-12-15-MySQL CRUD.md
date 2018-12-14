---
layout: post
title: MySQL CRUD
category: SQL
tags:
  - SQL
  - MySQL
  - CRUD
  - INSERT 구문
  - SELECT 구문
  - UPDATE 구문
  - DELETE 구문
---



> [생활코딩 - MySQL](https://opentutorials.org/course/3161)을 듣고 공부목적으로 정리한 포스팅입니다.



#### CRUD

- **C**reate
- **R**ead
- **U**pdate
- **D**elete

**Create**와 **Read**는 데이터베이스라면 반드시 가지고 있는 기능이기 때문에

상대적으로 **Update**와 **Delete**보다 중요한 개념

------

#### INSERT 구문(Create)

- Create 기능을 담당하는 구문

- **`SHOW TABLES;`**를 입력하면 이전에 만들었던 `topic`이라는 테이블이 생성된걸 확인할수 있다.

  ![sqlshowtables](/assets/database/mysql/sqlshowtables.png)

- INSERT를 해야하는데 헷갈리는 경우 명시적으로 테이블을 보이게 할수 있다

  - **`DESC 테이블명;`**
    ![sqldesc](/assets/database/mysql/sqldesc.png)

- ```mysql
  mysql> INSERT INTO topic (title,description,created,author,profile) VALUES('MySQL','MySQL is ...',NOW(),'egoing','developer');
  ```

  - **`VALUES`**의 ()에 있는 컬럼이 어떤 컬럼인지 앞에 있는 ()를 통해서 유추
  - 그렇기 때문에 ()에 있는 값들은 순서대로 짝이 맞아야 한다.

------

#### SELECT 구문(Read)

![sqlselect](/assets/database/mysql/sqlselect.png)

**`SELECT * FROM 테이블명;`**

- 해당 테이블의 모든 자료를 가져온다.

![sqlwhere](/assets/database/mysql/sqlwhere.png)

**`SELECT column FROM 테이블명 WHERE column='column name'`**

- 해당 테이블에서 선택한 `column들`중 특정 `column name`명이 포함된 자료를 가져온다



![sqlorderby](/assets/database/mysql/sqlorderby.png)

**`SELECT column FROM 테이블명 WHERE column='column name'ORDER BY id DESC;`**

- `id` column을 기준으로 큰 것부터 나오게(Descending, 내림차순) 정렬



![sqlorderbylimit](/assets/database/mysql/sqlorderbylimit.png)

**`SELECT column FROM 테이블명 WHERE column='column name'ORDER BY id DESC LIMIT 2;`**

- 위에서부터 2개만 선택해서 가져온다

------

#### UPDATE 구문(Update)

![sqlupdate](/assets/database/mysql/sqlupdate.png)

**`UPDATE 테이블명 SET 업데이트할column='업데이트내용' WHERE id=적용하려는 id;`**

- 해당 테이블의 특정 column을 `'업데이트 내용'`으로 바꾸고 특정 id에 적용
- WHERE 문 없이 적용할 경우 테이블 전체에 다 적용되버리기 때문에 특히 주의해야한다

------

#### DELETE 구문(Delete)

![sqldelete](/assets/database/mysql/sqldelete.png)



---



### Reference

> [생활코딩-MySQL의 CRUD](https://opentutorials.org/course/3161/19538)
>
> [생활코딩-SQL의 INSERT 구문](https://opentutorials.org/course/3161/19539)
>
> [생활코딩-SQL의 SELECT 구문](https://opentutorials.org/course/3161/19540)
>
> [생활코딩-SQL의 UPDATE 구문](https://opentutorials.org/course/3161/19541)
>
> [생활코딩-SQL의 DELETE 구문](https://opentutorials.org/course/3161/19542)

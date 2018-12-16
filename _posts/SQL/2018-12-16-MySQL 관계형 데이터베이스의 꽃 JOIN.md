---
layout: post
title: (MySQL)-관계형 데이터베이스의 꽃 JOIN
category: SQL
tags:
  - SQL
  - MySQL
  - JOIN
  - 관계형 데이터베이스
---



> [생활코딩 - MySQL](https://opentutorials.org/course/3161)을 듣고 공부목적으로 정리한 포스팅입니다.

---



#### 관계형 데이터베이스의 필요성

- 데이터 중복으로 발생하는 문제들을 해결할수 있다
  - ex) `column`명 혹은 해당 `column`과 연관된 정보들의 일괄 변경 등



![sqlrelationaldatabase](/assets/database/mysql/sqlrelationaldatabase.png)

**이해하기 쉽게 시트를 예로 들었음**

- 하나의 `Table`내에 있는 여러 `column`중 필요한 부분 선택

- 해당 `column`과 연관된 정보들로 다시 테이블을 구성



**Trade-off**

- **장점**: 한번에 다 있는 경우 데이터를 직관적으로 보기가 쉽다

- **단점**: 데이터에 해당되는 행의 별도 데이터를 비교해가면서 봐야한다.

- MySQL에서는 위와 같은 trade-off를 상쇄할수 있도록 

  **데이터를 분산해서 저장**하고 **합쳐서 한번에 보여줄수 있다.**

---

#### 테이블 분리하기

**기존 `topic`테이블을 `topic`과 `author` 테이블로 분리**

- 기존 `topic` 테이블을 `topic_backup`으로 변경

  ```sql
  RENAME TABLE 해당 테이블명 TO 바꿀 이름;
  ```

- 수업 예제를 기준으로 하면 아래와 같다

  ```sql
  RENAME TABLE topic TO topic_backup;
  ```

- `topic` 테이블 생성

  ```sql
  CREATE TABLE `topic` (
    `id` int(11) NOT NULL AUTO_INCREMENT,
    `title` varchar(30) NOT NULL,
    `description` text,
    `created` datetime NOT NULL,
    `author_id` int(11) DEFAULT NULL,
    PRIMARY KEY (`id`)
  );
  ```

- `author` 테이블 생성

  ```sql
  CREATE TABLE `author` (
    `id` int(11) NOT NULL AUTO_INCREMENT,
    `name` varchar(20) NOT NULL,
    `profile` varchar(200) DEFAULT NULL,
    PRIMARY KEY (`id`)
  );
  ```

- `author`테이블에 데이터 입력

  ```sql
  INSERT INTO `author` VALUES (1,'egoing','developer');
  INSERT INTO `author` VALUES (2,'duru','database administrator');
  INSERT INTO `author` VALUES (3,'taeho','data scientist, developer');
  ```

  ![sqlauthortable](/assets/database/mysql/sqlauthortable.png)

- `topic`테이블에 데이터 입력

  ```sql
  INSERT INTO `topic` VALUES (1,'MySQL','MySQL is...','2018-01-01 12:10:11',1);
  INSERT INTO `topic` VALUES (2,'Oracle','Oracle is ...','2018-01-03 13:01:10',1);
  INSERT INTO `topic` VALUES (3,'SQL Server','SQL Server is ...','2018-01-20 11:01:10',2);
  INSERT INTO `topic` VALUES (4,'PostgreSQL','PostgreSQL is ...','2018-01-23 01:03:03',3);
  INSERT INTO `topic` VALUES (5,'MongoDB','MongoDB is ...','2018-01-30 12:31:03',1);
  ```

  ![sqltopictable](/assets/database/mysql/sqltopictable.png)

---

#### 관계형 데이터베이스의 꽃 JOIN

- 각각 독립적인 테이블을 Read할때 마치 하나의 테이블로 저장되어 있었던것과 같이 보여준다.

  ```sql
  SELECT * FROM 테이블1 LEFT JOIN 테이블2 ON 기준;
  ```

- 예제를 기준으로 하면 아래의 명령과 같다

  ```sql
    SELECT * FROM topic LEFT JOIN author ON topic.author_id = author.id;
  ```
  
  - `topic`과 `author` 테이블을 결합하는데 `topic`의 `author_id column`과 `author의 id column`이 같다는 기준으로 하나의 테이블로 합성
  
  ![sqljoin1](/assets/database/mysql/sqljoin1.png)


**실행 결과**

- `author_id`와 `id`가 굳이 필요하지 않기 때문에 나머지 정보들만 나오게끔 수정

  ```sql
  SELECT topic.id,title,description,created,name,profile FROM topic LEFT JOIN author ON topic.author_id = author.id;
  ```

![sqljoin2](/assets/database/mysql/sqljoin2.png)

**실행 결과**

- 모든 테이블이 각자의 식별자 값을 갖고 있다면 JOIN을 통해서 얼마든지 관계를 맺을수 있다.

---



### Reference

> [생활코딩-관계형 데이터베이스의 필요성](https://opentutorials.org/course/3161/19544)
>
> [생활코딩-테이블 분리하기](https://opentutorials.org/course/3161/19521)
>
> [생활코딩-관계형 데이터베이스의 꽃 JOIN](https://opentutorials.org/course/3161/19545)

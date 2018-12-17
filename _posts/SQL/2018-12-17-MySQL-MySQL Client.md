---
layout: post
title: (MySQL)-MySQL Client
category: SQL
tags:
  - SQL
  - MySQL
  - MySQL Clinet
  - MySQL workbench
---



> [생활코딩 - MySQL](https://opentutorials.org/course/3161)을 듣고 공부목적으로 정리한 포스팅입니다.

---

#### MySQL Client

- **MySQL monitor**
  - MySQL을 설치하면 기본으로 설치되는 프로그램
  - CLI 기반
  - 명령어를 잘 알고 있어야 이용할수 있음
- **MySQL Workbench**
  - GUI 기반
- 이외에 수많은 Client 들이 있고 검색엔진을 통해서 알수 있음

---

#### MySQL WorkBench

**설치 및 시작하기**

- [MySQL](https://www.mysql.com/products/workbench/) 사이트 접속하여 Download Now >> 버튼 클릭
- 맨 아래 화면에 본인 컴퓨터에 맞는 운영체제 선택 후 다운로드

![sqlworkbench0](/assets/database/mysql/sqlworkbench0.png)

설치 완료후 시작 화면



**MySQL 서버 접속하기**

- 위 그림의 + 버튼을 누른다

![sqlworkbench1](/assets/database/mysql/sqlworkbench1.png)

- **`Connection Name`**에 Server 이름을 입력
- **`Hostname`**같은 경우 `localhost`로 했을때 실패할 경우 `127.0.0.1`로 변경
- **`Test Connection`** 클릭

![sqlworkbench2](/assets/database/mysql/sqlworkbench2.png)

Connection 성공 메시지



**Schema 활성화하기**

![workbenchactiveschema](/assets/database/mysql/workbenchactiveschema.png)

- `opentutorials` 더블클릭 -> 해당 스키마를 활성화하겠다는 의미



**Schema에 Query 입력하기**

![workbenchquery](/assets/database/mysql/workbenchquery.png)

- Query 문을 입력하고 번개 표시를 누르면 Result Grid 화면이 나온다.



**새로운 Schema 생성하기**

![workbenchschema1](/assets/database/mysql/workbenchschema1.png)

- 상단 버튼 클릭 -> Schema Name 입력 -> Apply

![workbenchschema2](/assets/database/mysql/workbenchschema2.png)

- 바로 실행되는게 아니고 명령에 해당하는 SQL문을 보여줌 -> 확인 후 Apply

![workbenchschema3](/assets/database/mysql/workbenchschema3.png)

- 실행의 결과는 MySQL Monitor에서도 확인할수 있다.



**새로운 Table 생성하기**

![workbenchtable1](/assets/database/mysql/workbenchtable1.png)

- `workbench`더블클릭 -> `workbench` 스키마 활성화
- 상단 버튼 클릭 -> Name 입력 -> Column Name, Datatype 등 입력 -> Apply

![workbenchtable2](/assets/database/mysql/workbenchtable2.png)

- 마찬가지로, 명령에 해당하는 SQL문을 먼저 보여줌 -> 확인 후 Apply



**새로운 Table에 데이터 입력하기**

![workbenchtable3](/assets/database/mysql/workbenchtable3.png)

- Topic 테이블이 생성된걸 확인
- Topic의 맨 오른쪽 버튼을 누르면 해당 테이블에서 데이터를 입력할 수 있음



그 외의 많은 기능은 그때 그때 검색을 통해서 알아가기

---



### Reference

> [생활코딩-관계형 데이터베이스의 필요성](https://opentutorials.org/course/3161/19544)
>
> [생활코딩-테이블 분리하기](https://opentutorials.org/course/3161/19521)
>
> [생활코딩-관계형 데이터베이스의 꽃 JOIN](https://opentutorials.org/course/3161/19545)

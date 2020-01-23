---
layout: post
title: mysqldump
category: SQL
tags:
  - SQL
  - mysql
  - mysqldump
  - 기존 db서버내용을 다른 db서버로 옮기기
---



### 상황

---

2020년의 개발 내용과 2019년의 개발 내용이 겹쳐지지 않게 하기 위해

`portal-db1`(A)의 db를 `portal-db2`(B)으로 옮겨야 함.

---

### 문제 해결

---

- (A)로 접속하여 `mysqldump`로 기존 데이터 백업 파일(~.sql) 만들기
  - `/var/lib/mysql`로 이동 (별도 mysql db 저장소가 있는 경우는 해당 위치로 이동)
  - `mysqldump -u [db계정] -p[db패스워드] 원본db명 > 백업파일명.sql`
  - 내 경우는 `mysqldump -u root -p[db패스워드] comm > ~/commbak.sql`
  - `~/`를 별도로 한 이유는 백업파일 저장경로를 설정하기 위해서

- dump가 제대로 떠졌는지 확인

  - ```
    ubuntu@portal-db:~$ ls -l
    total 39776
    -rw-rw-r-- 1 ubuntu ubuntu  7900230 Jan 13 16:12 commbak.sql
    ```

- `FileZilla`나 `scp 등의 명령어`로 로컬 PC로 파일 복사 혹은 다운로드

  - `FileZilla` 이용
  - (A)의 파일을 로컬 PC로 다운로드

  ![mysqldump](/assets/database/mysql/mysqldump.png)

  - 로컬 PC의 파일을 (B)로 업로드

  ![mysqldump1](/assets/database/mysql/mysqldump1.png)

- (B)로 접속하여 데이터 복구

  - `/var/lib/mysql`로 이동 (별도 mysql db 저장소가 있는 경우는 해당 위치로 이동)
  - `mysql -u [db계정] -p[db패스워드] db명 < 백업파일명.sql`
  - 내 경우는 `mysql -u root -p[db패스워드] comm < /home/ubuntu/commbak.sql`

공통적으로 `mysql` 명령어로 잘 안되는 경우엔 `sudo`를 붙여서 진행해봐야 한다.

---

### Reference

---

[MySQL DB 이전 절차 - ischo.net](http://www.ischo.net/bd_mysql/17394)

[mysql db를 전부 백업해서 옮기기(서버 이전 등)](https://raisonde.tistory.com/entry/mysql-db를-전부-백업해서-옮기기서버-이전-등)

[MySQL database 다른 서버로 이동](https://opentutorials.org/module/894/6654)
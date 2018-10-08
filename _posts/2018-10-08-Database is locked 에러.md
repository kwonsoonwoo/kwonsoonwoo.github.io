---
layout: post
title: Database is locked 에러 해결
category: SQL
tags:
  - SQL
  - Error
---



**문제상황**

Django로 새로운 app을 생성하고 모델을 추가한 다음

makemigrations 성공 후 migrate를 할 때 발생한 에러.

---



**해결법**

> 참고 사이트 : [Stackoverflow](https://stackoverflow.com/questions/151026/how-do-i-unlock-a-sqlite-database)

**linux와 macOS의 경우**

```python
$ fuser <locked된 파일명>
ex: $ fuser development.db
```

- 참고 사이트에 나온 예제의 경우 development.db가 locked된 파일명
- 이 명령어는 어떤 프로세스가 파일을 lock하고 있는지 보여줌.
  - 위 명령어를 입력하면 아래와 같은 결과가 나옴.

    ```
    <locked된 파일명>: <프로세스 숫자>
    ex: development.db: 5430 
    ```

```
$ kill -9 <해당 프로세스 숫자>
ex: $ kill -9 5430
```

- 위 명령어를 통해 해당 프로세스를 kill 하면 database가 unlocked 됨.

---



**원인**

> 참고 사이트: [SQLite](https://www.sqlite.org/cvstrac/wiki?p=DatabaseIsLocked)

- 동일한 데이터베이스 연결에서 동시에 데이터베이스와 호환되지 않는 

  두 가지 작업을 수행하려고 할 때 발생.

  - ex) SELECT 문이 중간에 있고 SELECT에 의해 읽혀지는 테이블 중 하나를 

    DROP하려고하면 SQLITE_LOCKED 오류가 발생


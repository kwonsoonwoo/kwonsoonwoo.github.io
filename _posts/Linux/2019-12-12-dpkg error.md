---
layout: post
title: Could not get lock /var/lib/dpkg/lock-frontend
category: Linux
tags:
  - linux
  - 리눅스
  - dpkg error
  - Could not get lock /var/lib/dpkg/lock-frontend
---





### 상황

---

- 깨끗한 우분투 18.04에서 터미널로 뭔가를 설치하려고 하자 아래와 같은 에러 발생
  - ```
    E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable)
    E: Unable to acquire the dpkg frontend lock(/var/lib/dpkg/lock-frontend), is another process using it?
    ```

---



### 해결

---

- 아래처럼 순차적으로 명령어 수행
  - `sudo rm /var/lib/apt/lists/lock`
  - `sudo rm /var/cache/apt/archives/lock`
  - `sudo rm /var/lib/dpkg/lock*`
- 위의 3개를 먼저 수행 후 아래 명령어 수행
  - `sudo dpkg --configure -a`
- 이후에 `sudo apt update` 를 하게 되면 정상작동하는것을 확인 할 수 있다.



---

### Reference

---

[병아리 개발자의 이야기](https://kgu0724.tistory.com/71)


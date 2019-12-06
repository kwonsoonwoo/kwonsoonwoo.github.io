---
layout: post
title: (error)-The port may already be in use or the connector may be misconfigured.
category: Spring
tags:
  - Spring
  - Spring-Boot
  - The port may already be in use or the connector may be misconfigured
---





### 상황

---

- 어제 로컬로 spring-boot를 띄워서 작업하고 오늘 다시 켰는데 아래 메시지가 나옴.

```
***************************
APPLICATION FAILED TO START
***************************
 
Description:
 
The Tomcat connector configured to listen on port 8081 failed to start. The port may already be in use or the connector may be misconfigured.
 
Action:
 
Verify the connector's configuration, identify and stop any process that's listening on port 8081, or configure this application to listen on another port.
```





### 해결

---

- cmd 창에서 진행

  - `> netstat -ao |find /i "listening"`

  ```
    TCP    0.0.0.0:135            LAPTOP-9O8LF0P0:0      LISTENING       1100
    TCP    0.0.0.0:445            LAPTOP-9O8LF0P0:0      LISTENING       4
    TCP    0.0.0.0:902            LAPTOP-9O8LF0P0:0      LISTENING       6496
    TCP    0.0.0.0:912            LAPTOP-9O8LF0P0:0      LISTENING       6496
    TCP    0.0.0.0:945            LAPTOP-9O8LF0P0:0      LISTENING       22188
    TCP    0.0.0.0:5040           LAPTOP-9O8LF0P0:0      LISTENING       10892
    TCP    0.0.0.0:5357           LAPTOP-9O8LF0P0:0      LISTENING       4
    TCP    0.0.0.0:7680           LAPTOP-9O8LF0P0:0      LISTENING       17672
    TCP    0.0.0.0:8081           LAPTOP-9O8LF0P0:0      LISTENING       16100
  ```

  - 문제가 된 port를 kill - 나의 경우는 8081이 문제여서 [PID] 부분이 16100

  `> TaskKill /F /IM [PID]`

- 이후 다시 Spring-Boot 를 run하면 정상작동.







### Reference

---

[spring boot failed to start : The port may already be in use or the connector may be misconfigured](https://soye0n.tistory.com/94)


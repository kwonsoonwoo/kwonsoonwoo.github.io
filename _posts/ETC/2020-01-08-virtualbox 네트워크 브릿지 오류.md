---
layout: post
title: virtualbox 네트워크 어댑터에 브리지 오류
category: ETC
tags:
  - ETC
  - virtualbox
  - virtualbox 네트워크 어댑터 브리지에서 이름이 없는 경우
---





### 문제상황

---

virtualbox를 켜서 업무를 진행하고자 했으나 네트워크 설정 이상으로 실행이 안됨.

설정을 가보니 네트워크 어댑터 브리지에 목록이 없었음.

![virtualbox 네트워크 브릿지1](/assets/cloud/virtualboxnetwork1.PNG)

---



### 해결방법

---

1. **네트워크 연결 - 이더넷 - 속성으로 들어감.**

- X 표시 없는 이더넷으로 들어갈것.

![virtualbox 네트워크 브릿지2](/assets/cloud/virtualboxnetwork2.PNG)



2. **이더넷 속성에서 설치**

![virtualbox 네트워크 브릿지3](/assets/cloud/virtualboxnetwork3.PNG)



3. **네트워크 기능 유형에서 서비스 선택 후 추가**

![virtualbox 네트워크 브릿지4](/assets/cloud/virtualboxnetwork4.PNG)



4. **네트워크 서비스 선택 - 디스크 있음(H)**

![virtualbox 네트워크 브릿지5](/assets/cloud/virtualboxnetwork5.PNG)



5. **디스크에서 설치 - 찾아보기(B)**

![virtualbox 네트워크 브릿지6](/assets/cloud/virtualboxnetwork6.PNG)



6. **VBoxNetLwf.inf 파일 찾아서 열기**

- **`C:\Program Files\Oracle\VirtualBox\drivers\network\netlwf`**
- 보통은 위 경로에 있는거 같은데 없는 경우엔 별도로 찾아봐야 함.

![virtualbox 네트워크 브릿지7](/assets/cloud/virtualboxnetwork7.PNG)



7. **파일 위치 제대로 변경됐는지 보고 확인**

![virtualbox 네트워크 브릿지8](/assets/cloud/virtualboxnetwork8.PNG)



8. **드라이버 추가 됐는지 보고 확인**

![virtualbox 네트워크 브릿지9](/assets/cloud/virtualboxnetwork9.PNG)



9. **항목 추가 됐는지 보고 닫기**

![virtualbox 네트워크 브릿지10](/assets/cloud/virtualboxnetwork10.PNG)

---



### 결과

---

네트워크 목록 재 생성 및 접속 잘됨!

![virtualbox 네트워크 브릿지11](/assets/cloud/virtualboxnetwork11.PNG)

---



### Reference

---

[한놈님의 블로그](https://hannom.tistory.com/112)




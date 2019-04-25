---
layout: post
title: Collections
category: Java
tags:
  - java
  - collections
  - list
  - map
---



> [실전 자바 강좌 (ver.2018) - 초보부터 개발자 취업까지!!](https://www.inflearn.com/course/%EC%8B%A4%EC%A0%84-%EC%9E%90%EB%B0%94_java-renew/) 강의를
>
> 개인공부하며 정리하는 용도의 포스팅입니다.



### 학습목표

---

- **배열과 같이 자료(데이터)를 효율적으로 관리하기 위한 방법에 대해서 학습**



### List

---

**List는 인터페이스로 이를 구현한 클래스는 인덱스를 이용해서 데이터를 관리한다.**



![list](/assets/Java/list.png)

**특징**

- 인덱스를 이용한다
- 데이터 중복이 가능하다



**코드구현**

```java
// ArrayList 객체 생성
ArrayList<String> list = new ArrayList<String>();

// 데이터 추가
list.add("Hello");
list.add("java");
list.add("World");

list.add(2, "Programming");

list.set(1, "C");

// 데이터 추출
String str = list.get(2);

// 데이터 제거
str = list.remove(2);

// 데이터 전체 제거
list.clear();

// 데이터 유무
boolean b = list.isEmpty();
```







### Map

---

**Map은 인터페이스로 이를 구현한 클래스는 key를 이용해서 데이터를 관리한다**



![map](/assets/Java/map.png)

**특징**

- key를 이용한다
- key는 중복될 수 없다
- 데이터 중복이 가능하다



**코드구현**

```java
// HashMap 객체 생성
HashMap<Integer, String> map = new HashMap<Integer, String>();

// 데이터 추가
map.put(5, "Hello");
map.put(6, "Java");
map.put(7, "World");

map.put(8, "!!");

// 데이터 교체
map.put(6, "C");

// 데이터 추출
map.get(5);

// 데이터 제거
map.remove(8);

// 특정 데이터 포함 유무
b = map.containsKey(7);

b = map.containsValue("World");

// 데이터 전체 제거
map.clear();

// 데이터 유무
b = map.isEmpty();
```







### Reference

---

> [실전 자바 강좌 (ver.2018) - Collections](https://www.inflearn.com/course/%EC%8B%A4%EC%A0%84-%EC%9E%90%EB%B0%94_java-renew/lecture/13703)


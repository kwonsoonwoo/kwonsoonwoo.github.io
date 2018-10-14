---
layout: post
title: (Cs with python)-레퍼런스 카운트(reference count) 
category: 컴퓨터 공학
tags:
  - 컴퓨터 공학
  - 컴퓨터사이언스 부트캠프 with 파이썬
  - 레퍼런스 카운트
  - reference count
  - 가비지 컬렉션
  - garbage collection
---



[컴퓨터사이언스 부트캠프 with 파이썬](http://www.yes24.com/24/goods/58552941) 책을 공부하며 정리한 포스팅입니다.

개인 공부후 정리용으로 남기는 포스팅으로 내용상에 오류가 있을수 있습니다.

예제 코드는 [Computer-Science](https://github.com/KwonSoonWoo/Computer-Science) 를 통해 실습하고 있습니다.



**핵심 개념**

- 레퍼런스 카운트(reference count)
- 가비지 컬렉션(garbage collection)

---

**가비지 컬렉션(garbage collection)**

- 사용하지 않는 메모리를 언어 차원에서 해제한다는 개념
  - 힙(heap)에 할당한 메모리는 프로그래머가 직접 해제해야 함.
  - 하지만 자바, C#, 파이썬 등에서는 해당 언어가 스스로 해제

- 가비지 컬렉션은 여러가지 종류가 있음
  - Mark and Sweep, Stop and Copy, Reference Counting 등
  - 기본적인 내용은 이곳을 [참조](https://ko.wikipedia.org/wiki/%EC%93%B0%EB%A0%88%EA%B8%B0_%EC%88%98%EC%A7%91_(%EC%BB%B4%ED%93%A8%ED%84%B0_%EA%B3%BC%ED%95%99)#%EC%97%AC%EB%9F%AC%EA%B0%80%EC%A7%80_%ED%8F%AC%EC%9D%B8%ED%84%B0_%EC%B6%94%EC%A0%81_%EA%B8%B0%EB%B2%95)

- 파이썬은 레퍼런스 카운팅(Reference Counting)으로 가비지 컬렉션 구현



---

**레퍼런스 카운트(Reference Count)**

```python
a = 10
b = a
```

- 위처럼 코드 작성시 변수 a와 b가 상수 객체 10을 가리킴.

```
a ------>  10
           ^
b ---------|
```

- 이렇게 되면 상수 객체 10의 레퍼런스 카운트가 2가 됨.(a -> 10, b -> 10)
- a와 b를 각각 다른 객체를 가리키도록 코드를 수정하면 
- 상수 객체 10을 가리키는 참조가 모두 없어지며 레퍼런스 카운트가 0이 됨.
- 레퍼런스 카운트가 0이 되면 메모리에서 자동 해제.
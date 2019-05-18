---
layout: post
title: (error)-InvalidDataAccessApiUsageException
category: Spring
tags:
  - Spring
  - Spring-Boot
  - JPA
  - InvalidDataAccessApiUsageException
  - @Transactional
---





#### 상황

---

도메인 삭제 기능을 활용하려는데 아래와 같은 에러메시지가 뜨면서

기능 구현이 되질 않았다.

api 단에서의 문제로 아래 에러메시지를 검색해서 해결.



#### Error

---

Servlet.service() for servlet [dispatcherServlet] in context with path [] threw exception [Request processing failed; nested exception is **org.springframework.dao.InvalidDataAccessApiUsageException**: No EntityManager with actual transaction available for current thread - cannot reliably process 'remove' call; nested exception is 

**javax.persistence.TransactionRequiredException**: No EntityManager with actual transaction available for current thread - cannot reliably process 'remove' call] with root cause

**javax.persistence.TransactionRequiredException**: No EntityManager with actual transaction available for current thread - cannot reliably process 'remove' call

---



자바에 대해서 아직은 명확하게 모르는 상황이기 때문에

참고 사이트에서 설명을 보는게 훨씬 더 이해하기 쉬울 것이다. 



### Reference

---

> [레드트레인님의 블로그](https://paintitcode.tistory.com/51)


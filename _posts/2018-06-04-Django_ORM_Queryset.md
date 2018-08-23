---
layout: post
title: Django ORM과 쿼리셋
category: Django
tags:
  - Django
  - ORM
  - Queryset
---





```ORM```: Object-Relational Mapping

데이터베이스에 있는 내용들을 언어로 쓸수 있게 클래스화로 포장을 했다고 생각하면 됨.



```QuerySet(쿼리셋)``` : ```ORM```을 사용해서 데이터베이스의 내용을 가져오면 객체 목록은 쿼리셋이라는 클래스 타입을 가짐.



```~~.objects.~~``` -> 객체에 접근하는 명령어.

e.g) Post.objects.all() -> Post객체의 모든 내용에 접근.

User.objects.all() -> User객체의 모든 내용에 접근.




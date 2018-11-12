---
layout: post
title: Djangogirls blog 앱 생성 및 관리자에 추가
category: Django
tags:
  - Django
  - Djangogirls
---



참고 : [Djangogirls](https://tutorial.djangogirls.org/ko/django_models/)



# Djangogirls blog 앱 생성

**Django 프로젝트 생성**

```
>>> python manage.py startapp blog
# pycharm에서 app 폴더안에 blog 폴더 생성

config -> settings.py -> INSTALLED_APPS -> 'blog' 입력
# blog라는 패키지를 관리 모듈로 추가하겠다는 의미
```



**git commit하기**

```
git add -A
git commit -m 'blog app추가 및 INSTALLED_APPS에 등록
```



**git branch 나눠서 작업**

```
git branch blog-model
git checkout blog-model
```



**블로그 글 모델 만들기**

```python
from datetime import timezone
from django.db import models
from django.conf import settings

# 엑셀로 치면 빈 시트에 이름 하나씩 채우는거라 생각하면 됨.
class Post(models.Model):
    author = models.ForeignKey(
        settings.AUTH_USER_MODEL,
        on_delete=models.CASCADE,
    )
    title = models.CharField(max_length=200)
    text = models.TextField(blank=True)
    created_date = models.DateTimeField(default=timezone.now)
    published_date = models.DateTimeField(blank=True)
    
	# post 클래스의 인스턴스 메서드
    # published_date에 timezone.now를 호출한 값을 넣어주고 
    # 세이브를 해준다.
    def publish(self):
        self.published_date = timezone.now()
        self.save()

    # 객체를 문자열로 표현하고 싶다.
    # python에서 __repr__과 같은 의미
    # title이 문자열로 바로 표현됨. 없으면 표현 안됨.
    def __str__(self):
        return self.title
```



- 아래와 같이 2가지 단계로 나누어짐.
  - 데이터베이스의 변경사항을 적용하기 위해 기록하는것
  - 데이터베이스의 변경사항을 적용하는것



**데이터베이스의 변경사항을 기록하기**

```python
>>> python manage.py makemigrations

# migration은 데이터베이스의 변경사항
Migrations for 'blog':
  blog/migrations/0001_initial.py
    - Create model Post

```



**데이터베이스의 변경사항을 기록하기**

```python
>>> python manage.py migrate
```



**git commit 후 master branch로 merge후 blog-model branch제거**

```python
git add -A
git commit -m 'Post 모델 추가 및 migration 생성'
git checkout master
git merge blog-model
git branch -d blog-model
git log --oneline --all --graph
```



**admin 브랜치 생성 및 admin.py에 내용입력**

```python
git checkout -b admin

migrations의 admin.py 파일 열기
아래 내용 입력

from django.contrib import admin

from .models import Post

admin.site.register(Post)

python manage.py runserver 입력
웹 창에 localhost:8000/admin 입력하여 정상작동하는지 확인
```



**admin 관리자 페이지 로그인 정보 만들기**

```python
python manage.py createsuperuser

Username과 Password 정보 입력
```



**urls.py 에 내용 입력**

```
urls.py 파일 열기
urlpatterns에 url(r'', include('blog.urls')) 입력
```



**git commit 및 admin branch 제거**

```
git add blog/admin.py
git commit -m 'Post모델을 admin에 추가'
git checkout master
git merge admin
git branch -d admin
```






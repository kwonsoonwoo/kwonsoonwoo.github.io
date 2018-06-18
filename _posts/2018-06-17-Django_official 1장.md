---
layout: post
title: Django tutorial 1장
category: Django
---



Django tutorial과 stop-out 과제를 하다보니 어떤 타이밍에 어떤 모듈에서 실행하는 순서인지를 파악하는게

중요하다고 느껴져서 Django tutorial강의를 들으며 전반적인 순서를 정리해보고자 한다.



#### 1. Django 기본 설정까지 하기

- Djangogirls 튜토리얼 포스팅에서 정리했던것 참조하여  Source Root폴더까지 지정

---



####2. starapp polls 실행하여 폴더 생성

- manage.py있는 폴더로 가서 python.manage.py startapp polls 실행

---



#### 3. polls.view에서 index 함수 만들기

```django
from django.http import HttpResponse

def index(request):
	# 화면에 ( ) 에 있는 내용을 출력해준다.
    return HttpResponse("Hello, world. You're at the polls index.")
```

---



####4. urls.py 만들기 

```django
from django.urls import path

from polls import views

urlpatterns = [
    # path(아무것도 없는 문자열이 오면, views의 index가 실행
    #    view.index를 실행하려면 config의 urls.py에 패턴추가
    path('', views.index, name='index')
]
```

---



#### 5. config폴더의  urls.py에서 패턴 추가하기

```django
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
	# 경로(url 끝에 polls입력하면, polls 폴더의 urls.py를 include한다.
    path('polls/', include('polls.urls')), <- 추가한것
]
```

localhost:8000/polls를 입력하면 Hello, world. You're at the polls index.가 출력된 화면이 나와야함.

---




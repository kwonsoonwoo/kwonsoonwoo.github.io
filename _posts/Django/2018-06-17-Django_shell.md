---
layout: post
title: Django shell
category: Django
tags:
  - Django
---



PyCharm안에서 Django의 실행결과를 바로바로 알아볼수 없으니 불편한 점이 있다.

그런 불편을 해소하고자 Django shell 및 notebook을 설치하여 활용할수 있다.



#### 1. Django-extension 설치

- notebook 설치

  ```python
  $ pip install notebook
  ```

- django_extensions 설치

  ```python
  $ pip install django_extensions
  ```

  - config/settings.py -> INSTALLED_APPS에 추가

    ```python
    INSTALLED_APPS = [
        'polls.apps.PollsConfig',
    
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
    
        # pip install django_extensions
        'django_extensions',
    ]
    ```

- shell_plus 실행

  ```python
  $ ./manage.py shell_plus
  
  # Shell Plus Model Imports
  from django.contrib.admin.models import LogEntry
  from django.contrib.auth.models import Group, Permission, User
  from django.contrib.contenttypes.models import ContentType
  from django.contrib.sessions.models import Session
  from polls.models import Choice, Question
  # Shell Plus Django Imports
  from django.core.cache import cache
  from django.conf import settings
  from django.contrib.auth import get_user_model
  from django.db import transaction
  from django.db.models import Avg, Case, Count, F, Max, Min, Prefetch, Q, Sum, When, Exists, OuterRef, Subquery
  from django.utils import timezone
  from django.urls import reverse
  Python 3.6.5 (default, May 17 2018, 17:07:58) 
  Type 'copyright', 'credits' or 'license' for more information
  IPython 6.4.0 -- An enhanced Interactive Python. Type '?' for help.
  
  In [1]: 
  
  ```

  - 그냥 shell을 실행했을때는 django모델들이 자동으로 import가 안되는 차이점이 있음

---



#### 2. notebook도 실행 가능

- `./manage.py shell_plus --notebook`을 입력
- Django Shell-Plus가 포함된 notebook 페이지 실행
- 오른쪽 상단 부분 new를 클릭하여 Django Shell-Plus를 클릭 하면
- Django 모듈들이 포함된 pynb가 실행되기 때문에 별도로 import를 안해도 되는 편리함이 있음.

---




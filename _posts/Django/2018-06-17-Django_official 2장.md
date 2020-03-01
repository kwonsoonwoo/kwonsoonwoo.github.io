---
layout: post
title: Django tutorial 2장
category: Django
tags:
  - Django
  - django tutorial
---



Django tutorial과 stop-out 과제를 하다보니 어떤 타이밍에 어떤 모듈에서 실행하는 순서인지를 파악하는게

중요하다고 느껴져서 Django tutorial강의를 들으며 전반적인 순서를 정리해보고자 한다.



#### 1. migrate 실행

- ./manage.py migrate
- config/settings.py에 있는 데이터베이스들 및 내용들을 적용하기 위함
- 정확히 어떤 의미인지는 파악이 되질 않음

---



#### 2. 모델 만들기

- polls/models.py에 가서 커멘드 작성

```django
from django.db import models

class Question(models.Model):
    qustion_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')
    

class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
```



---



#### 3. 모델 활성화

- config/settings.py의 내용중 추가

```django
INSTALLED_APPS = [
    'polls.apps.PollsConfig', <- 추가한 내용,
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```



- makemigrations 및 migrate명령어 실행
  - Django 모델의 변경사항을 저장함.

---



#### 4. API 가지고 놀기 

- ipython 설치 후 shell실행 

```django
$ pip install ipython
$ python manage.py shell
```



```python
>>> from polls.models import Choice, Question # 방금 작성한 모델 클래스를 가져옴.

# 아직 시스템에 question이 없다.
>>> Question.objects.all()
<QuerySet []>

# 새 질문을 만드십시오.
# 표준 시간대 지원이 기본 설정 파일에서 사용 가능하므로
# Django는 pub_date에 대해 tzinfo가 있는 datetime을 기대합니다. timezone.now () 사용
# datetime.datetime.now () 대신 # 올바른 일을 할 것입니다

>>> from django.utils import timezone
>>> q = Question(question_text="What's new?", pub_date=timezone.now())

# 개체를 데이터베이스에 저장하십시오. 명시 적으로 save ()를 호출해야합니다.
>>> q.save()

# 이제 ID가 있습니다.
>>> q.id
1

# Python 속성을 통해 모델 필드 값에 액세스합니다.
>>> q.question_text
"What's new?"
>>> q.pub_date
datetime.datetime(2012, 2, 26, 13, 0, 0, 775217, tzinfo=<UTC>)

# 속성을 변경하고 save ()를 호출하여 값을 변경하십시오.
>>> q.question_text = "What's up?"
>>> q.save()

# class명.objects.all()은 class에있는 모든 객체를 표시합니다.
>>> Question.objects.all()
<QuerySet [<Question: Question object (1)>]>
```



<QuerySet [<Question: Question object (1)> 이라고 표기되는 객체를 표현하기 위해서는

polls/models.py의 Question과 Choice 클래스 모델에 ```__str__``` 메소드를 추가해야 한다.

- polls/models.py

  ```python
  from django.db import models
  
  class Question(models.Model):
      # ...
      def __str__(self):
          return self.question_text
  
  class Choice(models.Model):
      # ...
      def __str__(self):
          return self.choice_text
  ```



변경된 사항을 알아보려면 기존 shell을 exit하고 다시 shell 실행

```python
from polls.models import Choice, Question

In [2]: from django.utils import timezone

In [3]: Question.objects.all()
Out[3]: <QuerySet [<Question: What's up?>]>

In [4]: Question.objects.filter(id=1)
Out[4]: <QuerySet [<Question: What's up?>]>

In [5]: Question.objects.filter(question_text__startswith='What')
Out[5]: <QuerySet [<Question: What's up?>]>

In [6]: current_year = timezone.now().year

In [7]: current_year
Out[7]: 2018

In [8]: Question.objects.get(pub_date__year=current_year)
Out[8]: <Question: What's up?>

In [9]: q = Question.objects.first()

In [10]: q
Out[10]: <Question: What's up?>

In [11]: q.pub_date
Out[11]: datetime.datetime(2018, 6, 17, 9, 56, 49, 537632, tzinfo=<UTC>)

In [12]: q.pub_date.year
Out[12]: 2018

In [13]: q.was_published_recently()
Out[13]: True

In [14]: q
Out[14]: <Question: What's up?>

# Choice에서 ForeignKey로 연결되어 있어서 Question에 choice list가 없어도
# Question에서도 나를 가리키는 choice는 누군지 알수 있음.
# 
In [15]: q.choice_set.all()
Out[15]: <QuerySet []>

# choice클래스의 객체를 생성한다.
# admin 페이지에서 객체 추가하는것과 같은 역할
In [16]: Choice.objects.create(
    ...:     question=q,
    ...:     choice_text='Not much',
    ...:     votes=0,
    ...: )
Out[16]: <Choice: Not much>

# 현재 ordering기준 가장 첫번째걸 가져옴.
In [17]: c1 = Choice.objects.first()

In [18]: c1.question
Out[18]: <Question: What's up?>

In [19]: q
Out[19]: <Question: What's up?>

In [20]: id(c1.question)
Out[20]: 139705220470152

In [21]: id(q)
Out[21]: 139705220764560

In [22]: c1.question == q
Out[22]: True

# is 는 memory가 같은지 비교하는 것.
In [23]: c1.question is q
Out[23]: False

In [24]: q
Out[24]: <Question: What's up?>

# Question에서 자기한테 연결된 choice목록을 뽑아오는 것.
In [25]: q.choice_set.all()
Out[25]: <QuerySet [<Choice: Not much>]>

In [26]: Question.objects.all()
Out[26]: <QuerySet [<Question: What's up?>]>

In [27]: Choice.objects.all()
Out[27]: <QuerySet [<Choice: Not much>]>

In [28]: q.choice_set.all()
Out[28]: <QuerySet [<Choice: Not much>]>

# q.choice_set 과 Choice.objects가 거의 같은 역할.
In [29]: q.choice_set
Out[29]:                   <django.db.models.fields.related_descriptors.create_reverse_many_to_one_manager.<locals>.RelatedManager at 0x7f0fa80a1208>

In [30]: Choice.objects
Out[30]: <django.db.models.manager.Manager at 0x7f0fa8080080>

# q(Question 인스턴스)가 이미 있기 때문에 Question을 따로 할당할 필요가 없다
In [31]: q.choice_set.create(
    ...:     choice_text='The sky',
    ...:     votes=0,
    ...: )
Out[31]: <Choice: The sky>

In [32]: q.choice_set.create(
    ...:     choice_text='Just hacking again',
    ...:     votes=0,
    ...: )
Out[32]: <Choice: Just hacking again>

In [33]: q.choice_set.all()
Out[33]: <QuerySet [<Choice: Not much>, <Choice: The sky>, <Choice: Just hacking again>]>

In [34]: Choice.objects.filter(question=q)
Out[34]: <QuerySet [<Choice: Not much>, <Choice: The sky>, <Choice: Just hacking again>]>

```



---



#### 5. Django admin 페이지 입력 

- 관리자 생성하기

  ```python
  python manage.py createsuperuser
  - Username : 원하는거 입력
  - Email : 안써도 됨
  - password : 원하는거 입력
  - password (again) : password 확인
  ```

- localhost:8000/admin으로 접속

- username과 password로 로그인

- 인덱스 페이지에 Question과 Choice 보이게 하기

  - polls/admin.py

    ```python
    from django.contrib import admin
    
    from .models import Question, Choice
    
    admin.site.register(Question)
    admin.site.register(Choice)
    ```



---




---
layout: post
title: Django tutorial 3장
category: Django
tags:
  - Django
  - django tutorial
---



Django tutorial과 stop-out 과제를 하다보니 어떤 타이밍에 어떤 모듈에서 실행하는 순서인지를 파악하는게

중요하다고 느껴져서 Django tutorial강의를 들으며 전반적인 순서를 정리해보고자 한다.



#### 1. view function과 urls 추가

- polls/views.py

  ```python
  def detail(request, question_id):
      return HttpResponse("You're looking at question %s." % question_id)
  
   def results(request, quetion_id):
        response = "You're looking at the results of question %s."
        return HttpResponse(response % quetion_id)
  
    def vote(request, question_id):
        return HttpResponse("You're voting on question %s." % question_id)
  
  ```

- polls/urls.py

  ```python
  from django.urls import path
  
  from polls import views
  
  urlpatterns = [
      # path(아무것도 없는 문자열이 오면, views의 index가 실행
      #    view.index를 실행하려면 config의 urls.py에 패턴추가
      path('', views.index, name='index'),
      """
    	추가된 부분
    	"""
      path('<int:question_id>/', views.detail, name='detail'),
      path('<int:question_id>/results/', views.results, name='results'),
      path('<int:question_id>/vote/', views.vote, name='vote'),
  ]
  ```


- config.url -> polls.url 순서

---



#### 2. view가 뭔가 하게 만들기

- polls/views.py

```python
from django.http import HttpResponse

from .models import Question


def index(request):
	# DB에 있는 Question중, 가장 최근에 발행(pub_date)된 순서대로 최대 5개에 해당하는 			# QuerySet을 latest_question_list변수에 할당
    latest_question_list = Question.objects.order_by('-pub_date')[:5]

	# latest_question_list의 각 Question의 question_text들을 ', '로 연결시킨
    # 문자열을 output변수에 할당
	output = ', '.join([q.question_text for q in latest_question_list])

	# 만들어진 질문 제목들을 모은 문자열을 HttpResponse클래스의 생성자로 전달, 인스턴스를 리턴
	return HttpResponse(output)
```



- 질문 추가

- shell 켜서 입력

  ```python
  # create를 써서 만들었기 때문에 save()를 하지 않아도 됨.
  # 그냥 인스턴스를 만들었으면 메모리에만 존재하니까 save를 호출해야 되지만
  # create는 DB에 들어가는거까지 한번에 됨.

  In [35]: Question.objects.create(question_text='가장 좋아하는 게임은?', pub_date
      ...: =timezone.now())
  Out[35]: <Question: 가장 좋아하는 게임은?>

  In [36]: Question.objects.create(question_text='가장 좋아하는 걸스데이 멤버는?',
      ...:  pub_date=timezone.now())
  Out[36]: <Question: 가장 좋아하는 걸스데이 멤버는?>

  ```



---



#### 3. Templates 디렉토리 만들기

- 아래 순서로 패키지(이해하기 쉽게 디렉토리) 생성
  - polls -> templates(directory) -> index.html(file)

```django
{% raw %}
{% if latest_question_list %}
<ul>
    {% for question in latest_question_list %}
    <li>
        <a href="/polls/{{ question.id }}">{{ question.question_text }}</a>
    </li>
    {% endfor %}
</ul>
{% else %}
<p>No polls are available</p>
{% endif %}
{% endraw %}
```



- polls/views.py에서 index 함수 수정

  ```python
  def index(request):
      # DB에 있는 Question중, 가장 최근에 발행(pub_date)된 순서대로 최대 5개에 해당하는 		# QuerySet을 latest_question_list변수에 할당
      latest_question_list = Question.objects.order_by('-pub_date')[:5]
      context = {
          'latest_question_list': latest_question_list,
      }
      return render(request, 'polls/index.html', context)
  ```

- 원래는 settings.py에 TEMPLATES_DIRS를 별도로 지정해야되는데 안해도 됨

- 루트 폴더를 기준으로 templates 폴더를 만든게 아니라

- 실제 동작하는 애플리케이션 패키지 안에 template 폴더를 만들었기 때문에

- 자동으로 templates 폴더까진 찾아줌. 그 이후엔 경로 설정을 해줘야 함

  - ex ) 'polls/index.html'



**3-1. return render(request, 'polls/index.html', context)의 추상화 과정**

```python
def index(request):
    # DB에 있는 Question중, 가장 최근에 발행(pub_date)된 순서대로 최대 5개에 해당하는 			# QuerySet을 latest_question_list변수에 할당
    latest_question_list = Question.objects.order_by('-pub_date')[:5]
    context = {
        'latest_question_list': latest_question_list,
    }
    # Django의 TEMPLATES설정에 정의된 방법으로,
    # 주어진 인자('polls/index.html')에 해당하는 템플릿 파일을 가지는 Template인스턴스를
    # 생성, 리턴
    template = loader.get_template('polls/index.html')

    # Template인스턴스의 render()함수를 실행, 인수로 context와 request를 전달
    # 결과로 렌더링 된 HTML문자열이 리턴됨
    html = template.render(context, request)

    # 결과 HTML문자열을 사용해 생성한 HttpResponse객체를 리턴
    return HttpResponse(html)

    # return render(request, 'polls/index.html', context)
```

- 축약하는걸 추상화라고 함

---



#### 4. 404 에러 일으키기

- polls/views.py에 detail 함수 수정

```python
# try-except구문 없이
    # polls/detail.html에 해당하는 Question인스턴스를 전달해서
    # HTML에서는 해당 Question의 question_text를 출력

def detail(request, question_id):
    # question 변수에 Question 클래스 객체중 id가 question_id인 애
    question = Question.objects.get(id=question_id)
    # question 이라는 이름으로 위의 question을 전달
    context = {
        'question': question,
    }
    return render(request, 'polls/detail.html', context)
```

- polls/templates 안에 detail.html 파일 만들기

```python
# HTML에서는 해당 Question의 question_text를 출력
## context에 있는 'question'으로 question 인스턴스를 전달했으니까
## 그 인스턴스의 question_text를 출력
{{ question.question_text }}
```



- polls/views.py에 detail 함수에 try-except구문 삽입.

  ```python
  def detail(request, question_id):
      try:
          question = Question.objects.get(id=question_id)
      except Question.DoesNotExist:
          raise Http404('Question does not exist')
      context = {
          'question': question,
      }
      return render(request, 'polls/detail.html', context)
  ```

  - try-except구문 추상화

    ```python
    question = get_object_or_404(Question, id=question_id)
    ```



- http://localhost:8000/polls/100/ 입력시 Page not found (404)로 바뀜.

- config/settings.py에서 명령어 2개변경

```python
# DEBUG가 True여야 어떤 부분이 잘못된건지 상세하게 알려줌
DEBUG = True -> False로 변경

ALLOWED_HOSTS = [
    'localhost' <- 빈 리스트에서 'localhost' 추가
]
```

- 최종 완료시 아래 문자열이 출력되는 화면을 얻을수 있음

  ```
  Not Found
  The requested URL /polls/100/ was not found on this server.
  ```



- 파이썬에서 동적으로 함수 콜을 하고 싶은 경우

```python
## 파이썬에서 동적으로 함수콜을 하고 싶다 하면 이런 방식을 할수 있다. 기억할것.
def custom_get_object_or_404(model, **kwargs):
    # 1번째 인자로 특정 Model Class를 받음
    # 최소 1개 이상의 키워드인자를 받아서, 받은 인자들을 사용해 주어진
    # Model Class의 get()메서드를 실행
    #   존재하면 해당 인스턴스를 리턴
    #   없으면 raise Http404를 실행 (메시지는 임의로 지정)
    try:
        return model.objects.get(**kwargs)
    except model.DoesNotExist:
        raise Http404()
```

- 매개변수에 **kwargs를 하게 되면 보다 많은 인자들이 사용 가능해지기 때문에 동적으로 작동시킬수 있음.

---



#### 5. Template 시스템 사용하기

- polls/templates/polls/detail.html

  ```django
  {% raw %}
  <h1>{{ question.question_text }}</h1>

  <ul>
      <!-- question이 갖고 있는 choice목록을 순회 -->
      {% for choice in question.choice_set.all %}
      <!-- choice가 갖고 있는 choice의 텍스트를 보여줌 -->
      <li>{{ choice.choice_text }}</li>
      {% endfor %}
  </ul>
  {% endraw %}
  ```



---



#### 6. Namespace

**6-1. blog 애플리케이션 생성**

```python
$ python manage.py startapp blog
```

```
# 1. config.urls에서 blog.urls를 include, path는 'blog/'를 사용
# 2. blog app내에 urls모듈을 생성하고 이 view를 위 URL과 연결되도록 설정
# 3. localhost:8000/blog/에서 Blog index텍스트가 출력되는지 확인
```

-  blog/views.py

  ```python
  from django.http import HttpResponse

  def index(request):
      return HttpResponse('Blog index')
  ```

- config/urls.py에 추가

  ```python
   path('blog/', include('blog.urls')),
  ```

- blog 패키지(폴더)내에 urls.py 파일 생성

  ```python
  from django.urls import path

  from blog import views

  urlpatterns = [
      path('', views.index, name='index')
  ]
  ```



**6-2. common 애플리케이션 생성**

```python
$ python manage.py startapp common
```

- common/views.py

  ```python
  from django.shortcuts import render

  def index(request):
  	return render(request, 'common/index.html')
  ```

- ```
  # 1. common app내에 templates/common/index.html파일 생성
  # 2. 해당 파일에서 /blog/로의 링크 , /polls/로의 링크(a태그)를 두개 생성
  # 3. INSTALLED_APPS에 common을 추가
  # 4. config.urls에서 이 view를 바로 연결 (include를 사용하지 않음)
  ```

  common 패키지 안에 templates 폴더 -> common 폴더 -> index.html 파일 순서로 생성

- templates/common/index.html(/blog/로의 링크 , /polls/로의 링크(a태그)를 두개 생성)

  ```
  <a href="/blog/">Blog index</a><br>
  <a href="/polls/">Polls index</a>
  ```

- config/setting.py (3. INSTALLED_APPS에 common을 추가)

  ```python
  INSTALLED_APPS = [
      'polls.apps.PollsConfig',
      'common.apps.CommonConfig',	<- 추가 / 이걸 추가해야 templates폴더 파일이 동작함
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

- config/urls.py (4. config.urls에서 이 view를 바로 연결 (include를 사용하지 않음)

  ```python
  from django.contrib import admin
  from django.urls import path, include
  from common.views import index <- 추가

  urlpatterns = [
      path('admin/', admin.site.urls),
      # 경로(url 끝에 polls입력하면, polls 폴더의 urls.py를 include한다.)
      path('polls/', include('polls.urls')),
      path('blog/', include('blog.urls')),
      path('', index), <- 추가
  ]
  ```



- 이렇게 하면 localhost:8000을 했을때 Blog index 혹은 Polls index로 갈수 있는 창이 생김

- 하지만 하드코딩 형태이기 때문에 url형태로 바꿔줄 필요가 있음.

  ```python
  {% raw %}
  <a href="/blog/">Blog index</a><br>
  -> <a href="{% url 'index' %}">Blog index</a><br>
  <a href="/polls/">Polls index</a>
  -> <a href="{% url 'index' %}">Polls index</a>
  {% endraw %}
  ```

- 문제는 blog.url이나 polls.url이나 index 이름이 같아서 저렇게 연결하면 blog걸로만 인식이 됨.

  - config.urls에서  blog path가 나중에 선언됐기 때문에 polls path를 덮어썼기 때문.

- 이런 문제를 해결하기 위해선 각 url에 app_name을 선언해줘야함

- blog/urls.py and polls/urls.py

  ```python
  from django.urls import path
  
  from blog import views
  
  app_name = 'blog'	<- 추가
  urlpatterns = [
      path('', views.index, name='index')
  ]
  ```

  ```python
  from django.contrib import admin
  from django.urls import path, include
  from common.views import index
  
  app_name = 'polls'	<- 추가
  urlpatterns = [
  path('admin/', admin.site.urls),
  
  # 경로(url 끝에 polls입력하면, polls 폴더의 urls.py를 include한다.)
  
  path('polls/', include('polls.urls')),
  path('blog/', include('blog.urls')),
  path('', index),
  ]
  ```


- 이후 polls/templates/polls/index.html에서 app_name 수정

  ```django
  {% raw %}
    {% if latest_question_list %}
    <ul>
        {% for question in latest_question_list %}
        <li>
            <a href="{% url 'detail -> polls:detail' question_id=question.id %}">{{ question.question_text }}</a>
        </li>
        {% endfor %}
    </ul>
    {% else %}
    <p>No polls are available</p>
    {% endif %}
    {% endraw %}
  ```


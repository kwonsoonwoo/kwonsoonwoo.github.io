---
layout: post
title: Djangogirls post list기본 구현
category: Django
tags:
  - Django
  - Djangogirls
---



참고 : [Djangogirls](https://tutorial.djangogirls.org/ko/django_models/)



# Djangogirls post list기본 구현

**post-list 브랜치 생성**

```
git checkout -b post-list
```



**blog 폴더에서 urls.py생성후 runserver**

```
blog 폴더에서 new file 생성 -> urls.py

terminal -> python manage.py runserver
(실행이 이미 되고있으면 Ctrl+c로 멈췄다가
다시 runserver 명령어 입력)

그러면 아래의 문구로 시작하는 오류메시지를 찾아볼수 있음.
django.core.exceptions.ImproperlyConfigured

아까 만들어놨던 urls.py 안에 urlpatterns = [] 만들고 runserver확인
```



### Django에서 처리 가능한 하나의 페이지를 만들 때

***

**최소 구현**

- url (특정 페이지의 URL을 설정)
- view (URL로 들어온 request를 처리하고 response를 돌려줄 함수)

```
urlpatterns의 정규표현식을 적용했을 경우

http://localhost:8000/
-> r'^$'

http://localhost:8000/admin/
->r'^admin/'

urlpatterns의 빈 리스트에 url(r'^$', ), 입력

views.py 파일 열기
from django.http import HttpResponse

def post_list(request):
	return HttpResponse('Post List입니다')입력

urlpatterns에 blog.views에 있는 post_list함수를 두 번째 인자로 전달.
# 임포트할때는 상대경로로 불러오는게 효율적임.
from .views import post_list
url(r'^$', post_list),
```



**post_list_html 저장하기**

- html파일을 효율적으로 사용하기 위해 따로 저장하고 꺼내는게 일반적.

```
app -> templates 폴더 생성 -> blog 폴더 생성 
-> post_list.html 파일 생성 -> html:5[tab]으로 기본 내용 작성.
```



- post_list에서 templates/blog/post_list.html파일의 내용을 읽어서

- return해주는 HttpResponse에 전달

  ```python
  import os
  
  from django.http import HttpResponse
  
  def post_list(request):
      """
      first/
          first_file.txt
          second/
              second_file.txt
              third/
                  module.py
                  fourth/
                      fourth_file.txt
  
      module.py에서
      0. 현재 경로
          os.path.abspath(__file__)
  
      1. second/ 폴더의 경로
          os.path.dirname(<현재경로>)
  
      1-1. second/ 폴더의 경로
          os.path.dirname(<현재경로>)
  
      2. second/second_file.txt의 경로
          os.path.join(<second폴더의 경로>, 'second_file.txt')
  
      3. fourth/ 폴더의 경로
          os.path.join(<현재경로>, 'fourth')
  
      4. fourth/fourth_file.txt의 경로
          os.path.join(<현재경로>, 'fourth', 'fourth_file.txt')
      """
  
  # dirname은 경로 위로 join은 경로 아래로
  # join은 한 번에 2단계정도까지 내려가는것도 가능
      cur_file_path = os.path.abspath(__file__)
      blog_dir = os.path.dirname(cur_file_path)
      app_dir = os.path.dirname(blog_dir)
      template_dir = os.path.join(app_dir, 'templates')
      post_list_template_path = os.path.join(template_dir, 'blog', 'post_list.html')
      html = open(post_list_template_path, 'rt').read()
  
  
      return HttpResponse('Post List')
  ```

- 현재 경로가 어디인지 위치를 확인하려면 각 경로별로 프린트 해볼것

  - runserver를 돌린 상태에서 블로그 페이지를 새로고침하면 출력확인.

---
layout: post
title: Django HTML 시작하기
category: Django
tags:
  - Django
  - django html로 rendering 하기
---





**views.py에 있는 코드들을 기본 settings.py로 변경**

---



```python
import os
# 기본 설정되있는거
BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))

# 현재 어디 위치에 있는지 알아보기 위해 프린트
print('BASE_DIR:', BASE_DIR)

# TEMPLATES 기본 경로 설정
TEMPLATES_DIR = os.path.join(BASE_DIR, 'templates')
print('TEMPLATE_DIR:', TEMPLATES_DIR)

TEMPLATES = [
    {
        'DIRS':[
            # Django가 render, render_to_string등의 함수로
            # 템플릿을 불러올 때 기준이 되는 폴더 목록
            ## 원래는 비어있는데 아래 텍스트 입력
            TEMPLATES_DIR,
        ]
    }
]
```

- 위의 경로는 terminal에서 확인가능
  - python manage.py runserver하면 자동으로 새로고침



**views.py 파일 수정**

---

```python
import os

from django.http import HttpResponse
from django.shortcuts import render
from django.template.loader import render_to_string


def post_list(request):
    """
    TEMPLATES 경로 설정해줬으니까 나머지는 # 되어있는거 지워도 됨
    """
    # cur_file_path = os.path.abspath(__file__)
    # blog_dir_path = os.path.dirname(cur_file_path)
    # app_dir_path = os.path.dirname(blog_dir_path)
    # templates_dir_path = os.path.join(app_dir_path, 'templates')
    # blog_template_file_path = os.path.join(templates_dir_path, 'blog', 'post_list.html')
    # html = open(blog_template_file_path, 'rt').read()
    

    # # 경로에 해당하는 HTML파일을 문자열로 로드해줌
    # html = render_to_string('blog/post_list.html')
    # # 가져온 문자열을 돌려주기
    # return HttpResponse(html)
    """
    html = render_to_string('blog/post_list.html')
    + return HttpResponse(html)
    """
    return render(request, 'blog/post_list.html')
```



- 위의 내용을 도식화 했을때 아래와 같다

---

```
Django

view function:
	html = render_to_string(path)
	# path: template_dir/path
	return HttpResponse()
	
template_dir
	template files....
	
settings.py
TEMPLATES = {
    'DIRS': [template_dir]
}
```


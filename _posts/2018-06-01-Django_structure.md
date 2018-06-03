---
layout: post
title: Django 프로젝트 구조 설정
category: Django
---



**ubuntu 18.04 LTS  버전에서 구현한것임을 참고로 알아둘 것.**



# Django 프로젝트 구조 설정

**Django 프로젝트 생성**

```
django-admin startproject mysite 입력
# mysite란 이름의 프로젝트성를 생성하겠다는 의미
-> pycharm에서 확인하게 되면 아래와 같은 구조로 폴더 및 패키지가 생성.

djangogirls-tutorial/
	mysite/				<-Django프로젝트 관련 코드 컨테이너 폴더
		manage.py
		mysite/			<-이 Django프로젝트의 설정 관련 패키지
			__init__.py
			settings.py


쓰기가 불편하기 때문에 아래와 같이 바꿔주는데 해야할일은 다음과 같다.
1. Django코드 컨테이너 폴더의 이름을 app으로 변경
2. Django프로젝트 설정 패키지의 이름을 config로 변경
절대적인 것은 아니고 각 회사의 상황에 따라 다름.


djangogirls-tutorial/	<-이 프로젝트의 컨테이너 폴더 (Root폴더)
	app/				<-Django프로젝트 관련 코드 컨테이너 폴더
		config/			<-Django프로젝트의 설정 관련 패키지
			settings.py
	
	.gitignore			<-Django프로젝트(애플리케이션) 코드와 
	.git/				관계없지만 프로젝트를 위해 필요한 파일/폴더들
	requirements.txt
	...		
```



**Django 프로젝트 설정 변경**

```
mysite 폴더 -> 우클릭 -> Refactor -> Rename(shift+f6) -> app입력
- Search for references / Search in comments and strings
체크해제 후 app입력
- root 폴더 외에 모든 폴더는 패키지로 취급됨.
- 체크가 되어 있으면 안에 있는 폴더 및 파일들도 변형됨.

mysite 패키지 -> 우클릭 -> Refactor -> Rename(shift+f6) 
-> config입력
- 이때는 폴더 생성때와는 반대로 체크해제 했던걸 다시 입력함.
```





**PyCharm은 현재 프로젝트 구조에서 가장 상위폴더를 파이썬 Source의 root로 인식한다**

```
project/	<-python 실행
	project_module1.py
	project_module2.py
	pac1/
		__init__.py
		pac1_module.py
		pac2/
			__init__.py
			pac2_module.py
			pac2_module2.py
			
			pac3/
				__init__.py

## python을 root에서 시작했을 때
# project_module1을 가져올때
import project_module1

# pac1패키지 내의 pac1_module을 가져올 때
from pac1 import pac1_module

# pac2패키지 내의 pac2_module을 가져올 때
from pac1.pac2 import pac2_module

## 하위 패키지에서의 동작
# pac2_module.py에서 pac2_module2.py를 가져오고 싶을 경우
(pac2_module.py의 내용)
from         . import pac2_module2 <- .은 현재 위치의 패키지
from pac1.pac2 import pac2_module2

# pac2_module.py에서 pac2_module2.py를 가져오고 싶을 경우
from   .. import pac1_module	<- 밑에 있는 코드와 같은 의미
from pac1 import pac1_module

## python을 root에서 시작했을 때
# project_module1을 가져오려면
불가능
```
- root 폴더를 기준으로 파이썬 코드가 서로를 참조하면서 왔다갔다 가능
- root 폴더가 어디냐에 따라 모듈을 불러옴에 있어 에러가 날 수도 있음.
  - 따라서, root 폴더를 지정하고 프로젝트 개발을 시작해야 함.



**Root 폴더 설정**

- PyCharm에서 루트 폴더 할거 우클릭
- 아래쪽 Mark Directory as -> Sources Root 선택
- 해당폴더는 파란색으로 변하면서 패키지 표시가 사라짐



**requirements.txt 생성**

- 파이썬 코드와 별개로 어떤 라이브러리 버전을 사용하고 있는 기록해야 함.

- git에 의해 관리된 소스코드를 누군가 클론해서 실행했을때 완벽히 실행되어야 하기 때문.

  ```
  pip freeze > requirement.txt(관용적으로 쓰는 파일명)
  ```
  
- requirement.txt파일이 생성되고 버전이 기록이 됨.



**여기까지 하는게 장고프로젝트 하기 전 기본설정.**



**git commit하기**

```
>>> git stauts
		.gitignore
        app/
        requirements.txt

>>> git status -u
		.gitignore
        app/config/__init__.py
        app/config/settings.py
        app/config/urls.py
        app/config/wsgi.py
        app/manage.py
        requirements.txt

>>> git add -A
>>> git commit -> vi 상태가 되고 자세한 내용을 기록

```


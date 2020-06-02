---
layout: post
title: Djangogirls 환경설정
category: Django
tags:
  - Django
  - Djangogirls
  - Djangogirls 환경설정
---



# Django 환경설정

**terminal에서 djangogirls-tutorial 폴더 생성(ubuntu terminal기준)**

```
projects 폴더에서 시작

➜  projects mkdir django     # django 폴더 생성
➜  projects cd django  		 # django 폴더 이동
➜  django mkdir djangogirls-tutorial   #djangogirls-tutorial
										폴더 생성
➜  django cd djangogirls-tutorial  # djangogirls-tutorial
									 폴더 이동
➜  djangogirls-tutorial git init  # git-init해서 git 파일만들기

Github에서 new Repository 만들고
➜ git remote add origin "Repo주소"

http://gitignore.io 접속
-> macos, linux, pycharm+all, python, git, django 입력
-> create 실행 및 전문 복사

➜  djangogirls-tutorial git:(master) vi .gitignore 
# 복사한거 붙여넣고 저장하고 닫기
```



**가상환경 설정**

```
➜  djangogirls-tutorial git:(master) ✗ pyenv virtualenv 3.6.5 fc-djangogirls
# fc-djangogirls 프로젝트 가상환경 생성

➜  djangogirls-tutorial git:(master) ✗ pyenv local fc-djangogirls
# fc-djangogirls 프로젝트에 적용

(fc-djangogirls) ➜  djangogirls-tutorial git:(master) ✗ charm .
# 적용이 되면 명령어 앞에 (프로젝트명이 생김)
# charm . -> pycharm 실행
```

이후 부분은 [Crawler](https://kwonsoonwoo.github.io/python/2018/05/28/Crawler.html) 포스팅의  PyCharm Interpreter설정하기 내용과 같음.



**가상환경 설정 최종확인**

```
(fc-djangogirls1) ➜  djangogirls-tutorial1 git:(master) ✗ pip list
# pip와 setuptools의 패키지명과 버전만 나오는지 확인
# (fc-djangogirls1) 과 pip, setuptools만 나오면 제대로 설치된것.

pip install django~=1.11.0 입력
# 지금은 2.x 버전이 최신이지만 이 튜토리얼에서는 1.x 버전을 쓰기 때문에
# 튜토리얼 기준에 맞게 예전버전의 django를 설치하여 실습진행.

pip install --upgrade pip
# pip 버전이 업데이트가 가능한 경우 해당 커멘드 입력
```
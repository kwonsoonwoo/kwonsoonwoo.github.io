---
layout: post
title: (Error)-command 'x86_64-linux-gnu-gcc' failed with exit status 1
category: Python
tags:
  - python error
  - gcc
  - pip
  - error
---



### 문제상황

- 오류 메시지: `error: command 'x86_64-linux-gnu-gcc' failed with exit status 1`
  - 앞에는 패키지 설치 중에 실패했다는 다량의 메시지들이 있음.
  - EC2로 배포하기 위해 로컬에 있는 프로젝트 폴더를 옮겨서 python, pipenv, pip 등을 설치하고 `pipenv install` 을 실행했으나 package들중 하나였던 pyproj가 설치가 안됨

------



### 해결법

- **아래 커맨드 실행**

```
sudo apt-get install python3-dev
```

------



### 원인

Python.h라는 헤더 파일이 없어서 gcc가 응용 프로그램을 빌드하는데 실패한 것.

이를 해결하기 위해서는 **`python-dev`**패키지 파일을 설치해야 하는데

이건 각자 설치되어있는 python version에 맞춰서 설치하면 될듯하다.

(나의 경우엔 python 3.6.6 버전)



보다 자세한 설명은 아래 Reference를 참조!

------

### Reference

> [Stackoverflow](https://stackoverflow.com/questions/26053982/setup-script-exited-with-error-command-x86-64-linux-gnu-gcc-failed-with-exit)
---
layout: post
title: (pipenv error)-'module' object is not callable
category: Python
tags:
  - Python
  - pipenv error
  - Pipfile lock error
  - 'module' object is not callable
---



### 문제상황

- 오류 메시지: `TypeError: 'module' object is not callable`
  - 프로젝트 폴더에 `pipenv shell`로 가상환경을 실행한 후
  - `pipenv install pygments`를 하자 위의 오류메시지가 나옴
  - Pipfile에는 관련 패키지가 설치 된것으로 나왔으나 Pipfile.lock 파일이 생성안됨

------



### 해결법

- **아래 커맨드 실행**

```
pipenv run pip install pip==18.0
pipenv install
```

------



### 원인

pip version이 18.1로 업데이트 되면서 발생하는 원인인듯 하다.

나의 경우엔 기존에 pip 18.0버전이 설치되어 있는 상태에서 18.1로 버전업데이트를 했고

그러다 보니 version간의 충돌이 일어나서 Pipfile.lock 파일이 생성되지 않았던듯 하다.

아예 새로 설치하는 경우엔 해당 오류가 발생하지 않는듯 하다.

------

### Reference

> [Stackoverflow](https://stackoverflow.com/questions/52711988/pipenv-on-windows-module-object-is-not-callable?noredirect=1&lq=1)

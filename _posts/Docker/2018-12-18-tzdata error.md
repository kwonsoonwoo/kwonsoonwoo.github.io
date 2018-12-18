---
layout: post
title: (Error)-tzdata,geographic area 선택 에러
category: Deploy
tags:
  - docker
  - tzdata
  - geographic area
---



### 문제상황

- 작성했던 `Dockerfile` 내용

  ```dockerfile
  FROM        ubuntu:18.04
  MAINTAINER  zenuine1@gmail.com
  
  # update, upgrade
  RUN         apt -y update && apt -y dist-upgrade
  
  # zsh
  RUN         apt -y install zsh curl git
  RUN         curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh | bash
  RUN         chsh -s /usr/bin/zsh
  
  # pyenv
  RUN         curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash
  RUN         apt -y install make build-essential libssl-dev zlib1g-dev libbz2-dev \
                     libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev                        libncursesw5-dev \
                     xz-utils tk-dev libffi-dev
  ```


- `Docker image`를 build하는 과정에서 `pyenv`를 설치하는데 

  geographic area를 선택하라는 메시지가 나오고 선택하면 build가 

  화면처럼 멈춘 상태에서 진행이 안된다

![dockertzdata](/assets/docker/dockertzdata.png)

------



### 해결법

- **# pyenv 바로 아래에 해당 커맨드 추가**

  ```dockerfile
  ENV         DEBIAN_FRONTEND=noninteractive
  ```


------



### 원인

이 부분은 확실하게 알게 되면 다시 써야 될듯하지만 Reference의 해석을 빌리자면 대략 이렇다.

**`dpkg`를 쌍방향 대화없이 실행하기 위해서는 하나의 환경변수를 다음과 같이 설정할수 있다.**

설치할때의 메시지를 통해 추측해보건데

`tzdata`를`dpkg` 명령어를 통해서 setting 하는데

이때, Dialog라는 대화형 프론트엔드를 사용한다. 이 과정에서 충돌이 일어나기 때문에

`DEBIAN_FRONTEND`를 noninteractive로 설정한게 아닐까 생각한다.

(혹시, 정확히 아시면 댓글 좀 부탁드립니다!!)



---

### Reference

> [askubuntu](https://askubuntu.com/questions/909277/avoiding-user-interaction-with-tzdata-when-installing-certbot-in-a-docker-contai)


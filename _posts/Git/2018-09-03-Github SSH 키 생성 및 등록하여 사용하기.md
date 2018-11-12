---
layout: post
title: Github SSH 키 생성 및 등록하여 사용하기
category: Git
tags:
  - git
  - github
  - SSH Key
---



SSH Key란 github에 push(연결)할때마다 아이디와 비밀번호를 사용하지 않게 해주는 기능

git push 할때마다 아이디(이메일)와 비번을 입력하는것이 처음에는 편할수 있으나

시간이 갈수록 효율이 떨어진다.(~~귀찮아진다~~)

처음 한번 고생하면 계속 편해질수 있으니 두려워말고 시도해보자!



> [nickjo님의 블로그](http://nickjoit.tistory.com/94)
>
> [농약먹은사과님의 블로그](http://jibak.tistory.com/9)



**1. 등록된 키가 있는지 확인**

- 터미널에서 아래와 같이 입력했을때 기존에 등록해놓은 ssh키가 있는지 확인한다.

  ```bash
  ls -al ~/.ssh
  ```

  - 기존에 만들어 놓은 키가 있는 경우 id_rsa.pub과 같은 키파일이 있을것이다.

**2. 없다면 새로운 SSH키 생성**

```bash
ssh-keygen -t rsa -C “your_email@example.com”
```

- 위 명령어 중 메일을 쓰는 부분은 git계정에 등록한 이메일 주소를 써준다.
- 그러면, 첫 질문은 ssh키를 만드는 경로가 맞는지 확인하는 질문이 나온다 -> Enter 누름
- 그 후, 본인만이 기억할수 있는 비밀번호를 입력한다.

**3. ssh-agent가 실행중인지 확인**

- ssh -agent에 만들어 놓은 ssh키를 추가하기 전에 ssh-agent가 정상 실행중인지 확인

```bash
eval $ (ssh-agent -s)
```

- "agent pid 12345" <- 명령어 밑에서 이런 문장이 출력된다면 정상 실행중인것.

**4. ssh-agent에 SSH 개인 키를 추가**

```bash
ssh-add ~/.ssh/id_rsa
```

- 다른이름으로 키를 작성하였거나, 다른 이름을 가진 기존 키를 추가하는 경우

  id_rsa의 개인용 키 파일의 이름을 바꿔야 함.

**5. 생성된 키를 github 홈페이지에 등록**

- github 홈페이지에서 오른쪽 상단 모서리의 프로필 사진 클릭 -> Settings 클릭
- 왼쪽 목록중 SSH and GPG keys 클릭 -> new SSH key 클릭

![ssh-key1](/assets/git/ssh-key1.png)

- 아래 명령어들 중 하나로 id_rsa.pub 파일의 내용을 전부 복사
  - vi ~/.ssh/id_rsa.pub
  - cat ~/.ssh/id_rsa.pub
  - bcopy < ~/.ssh/id_rsa.pub
- title은 마음대로 작성 -> key에다가는 복사한 내용 붙여넣기 -> Add SSH key

![ssh-key2](/assets/git/ssh-key2.png)

- 아래 화면처럼 나오면 완료

![ssh-key3](/assets/git/ssh-key3.png)



이렇게 완료하고 나면 이후부턴 새로운 Repo를 만들때에도 자동으로 ssh주소가 만들어지기

에 이메일과 비밀번호를 입력하는 번거로움이 사라진다!

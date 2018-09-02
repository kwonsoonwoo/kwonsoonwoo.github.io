---
layout: post
title: jekyll serve(Gem::LoadError) 해결
category: ETC
tags:
  - ETC
  - jekyll
---



jekyll serve를 실행했을 때 오류를 처음으로 경험해서 구글링을 통해 찾은 해결책을

기록한다.

> [CHEF-KOCH의 github](https://github.com/CHEF-KOCH/CHEF-KOCH.github.io)



**에러화면**

- jekyll serve를 입력했을때 아래와 같은 오류(Gem::LoadError)가 뜬다.

![jekyll serve 에러](/assets/jekyll/jekyll serve 에러.png)



**해결 방법**

- 아래 명령어 실행

```bash
bundle clean --force
```

- 이후 jekyll serve를 하게 되면 다시 잘 돌아감.



꼭 저렇게 하지 않아도 ```bundle exec jekyll server``` 를 입력해도 정상적으로 기능한다.


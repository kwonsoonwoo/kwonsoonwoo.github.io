---
layout: post
title: git commit 날짜 바꾸기
category: Git
tags:
  - git
  - github
  - commit 날짜 바꾸기
---









**문제 상황**

잔디 심기를 할때 특정일을 놓치는 경우 유용(?)하게 쓸수 있는 꼼수(-_-..)



**방법**

1. **마지막 Commit 날짜를 현재 날짜로 설정**

   `git commit --amend --no-edit --date "$(date)"`

2. **마지막 Commit 날짜를 임의의 날짜로 설정**

   `git commit --amend --no-edit --date "Mon 20 Aug 2018 20:19:19 KST"`

   `""` 사이에 원하는 날짜와 연도 및 시간을 기입하면 된다.



---

### Reference

[Code with Hugo](https://codewithhugo.com/change-the-date-of-a-git-commit/)

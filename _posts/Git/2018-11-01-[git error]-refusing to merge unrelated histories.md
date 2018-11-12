---
layout: post
title: (Error)-refusing to merge unrelated histories
category: Git
tags:
  - git
  - allow unrelated histories
  - refusing to merge unrelated histories
---

### 문제상황

- 오류 메시지: `fatal: refusing to merge unrelated histories`
  - 기존에 어느 정도 commit & push 했던 저장소가 있는 상황
  - 어떠한 이유로 갑자기 commit이 되지 않아 git을 삭제(.git 파일 삭제)하고 다시 `git init`
  - `git pull origin master`를 해서 기존에 push됐던걸 받아온 후
  - 다시 commit & push 를 하려고 했을때 위의 오류 발생

------



### 해결법

- **`git pull origin <branchname> --allow-unrelated-histories ` 커맨드 입력**
  - 나의 경우는 branchname이 master였음
  - 변경된 사항이 있을 경우 추가로 add & commit
  - `git push -u origin <branchname>` 을 해서 conflict 된 파일들 수정 후 다시 add + commit + push

------



### 원인

git을 삭제했다가 다시 `git init`을 하고 `git pull`을 하면

우리가 봤을땐 같은 프로젝트임에도 불구하고

git의 입장에서는 전혀 새로운 프로젝트로 인식하는듯 하다.

따라서 하나의 저장소에서 각각의 브랜치에서 작업하다가 합치는 `git merge`의 관점이 아닌

전혀 다른 2개의 저장소에서의 작업을 합치는 관점에서 바라봐야 하고

최초로 pull을 해오는 경우 뒤에 `--allow-unrelated-histories` 라는 커맨드를

추가로 입력해야 되는듯 하다.

---

### Reference

> [Stackoverflow](https://stackoverflow.com/questions/37937984/git-refusing-to-merge-unrelated-histories-on-rebase)

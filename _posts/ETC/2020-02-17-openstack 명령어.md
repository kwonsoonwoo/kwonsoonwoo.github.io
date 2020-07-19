---
layout: post
title: openstack 명령어 정리
category: ETC
tags:
  - ETC
  - openstack
  - openstack 명령어 정리
---



**개요**

---

openstack 관련 업무를 하다보니 horizon으로 업무를 처리할 때도 있지만

경우에 따라서는 Command Line으로 처리해야 할 경우도 생겨

리스트 업 하고 적용해 본 명령어를 지속 추가할 예정

---



**`openstack server list --host compute노드 --all`**

- 오픈스택 특정 컴퓨트 노드에 있는 vm 목록 보기
- ex) `openstack server list --host compute02 --all`




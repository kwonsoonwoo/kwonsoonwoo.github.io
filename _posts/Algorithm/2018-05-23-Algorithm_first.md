---
layout: post
title: 알고리즘 실습
category: Algorithm
tags:
  - Algorithm
  - 순차검색
  - Sequential Search
---



## 알고리즘

- 순차검색(Sequential Search)

  	i. 문자열과 키 문자 1개를 받는 함수 구현

         ii. while문을 이용, 문자열에서 키 문자가 존재하는 index위치를 검사 후 해당 index를 리턴
        
        iii. 찾지 못했을 경우 -1을 리턴

  ```python
  >>> def sequential_search(string, key):
      	index = 0
      	# 전체 문자열을 순회하며 각 글자를 char에 할당
      	for char in string:
          	print(char)
          	# 순회중인 문자(char)와 찾으려는 문자(key)가 같은 경우
          	if char == key:
              	# 메시지를 출력하고 해당 index를 리턴
              	print('찾는값이 나왔음, index:', index)
              	return index
          
          # 매 루프의 끝에서 index값을 1씩 증가
          index += 1
          
      # 전체 문자열을 순회했음에도 char와 key가 같은 경우가 없었다면
      # (같다면 return으로 함수가 종료됨)
      # -1을 리턴하며 함수 종료
      return -1
  
  >>> def sequential_search(string, key):
      	for index, char in enumerate(string):
          	if char == key:
              	return index
          	return -1
          
  >>> def sequential_search(string, key):
      	index = 0
      	# 5글자 문자열
      	#  length :   5
      	#  최대 index: 4
      	while index < len(string):
          	# 주어진 문자열(string)에서 index번째의 문자를
          	# char변수에 할당
          	char = string[index]
          	print(f'Index: {index}, 현재문자:{char}')
          	if char == key:
              	print('
          	index += 1
  
  >>> result = sequential_search('hello', 'x')
  h
  e
  l
  l
  o
  >>> print(result)
  -1
  ```




- 선택정렬(Selection sort)

  - [9, 1, 6, 8, 4, 3, 2, 0, 5, 7] 를 정렬한다.

  - 정렬과정

    a. 리스트 중 최소값을 검색

    b. 그 값을 맨 앞의 값과 교체

    c. 나머지 리스트에서 위의 과정을 반복

  - 해결방법

    a. 알고리즘 진행과정 그려보기

    b. 의사코드(Psuedo code) 작성

    c. 실제 코드 작성

```python
ori = [9,1,6,8,4,3,2,0]

# 의사코드
# ori = [9,1,6,8,4,3,2,0]

# # 총 8개 원소이므로
# for 0 부터 n - 1 까지:
#     ori[i]부터 ori[n - 1]까지 비교
#     만약 최소값이 j에 있다면
#     ori[i]와 ori[j]의 값을 서로 바꿔준다

# min함수 쓰지말고 각 Loop의 리스트에서 가장 작은값을 출력
for i in range(len(ori) - 1):
    print(f'Loop {i}, ori: {ori}')
    # 현재 loop의 첫 번째 값을 최소값으로 지정
    min = ori[i]
    # 현재 loop의 최소값의 ori에서의 index를 저장
    min_index = i
    # ori의 i번째부터 끝까지를 순회함
    # (i는 상위 Loop에서 1씩 증가)
    for inner_index, x in enumerate(ori[i:]):
        if x < min:
            min = x
            # 최소값을 지정하면서 현재 loop의 최소값 index갱신
            min_index = i + inner_index
        print('최소:', min, '최소 index:', min_index)
        
    # 최소값을 찾았으므로 i번째 요소와 위치를 바꿔줌
    ori[i], ori[min_index] = ori[min_index], ori[i]
```

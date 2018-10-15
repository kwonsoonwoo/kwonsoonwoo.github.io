---
layout: post
title: (Cs with python)-함수(람다함수) 
category: 컴퓨터 공학
tags:
  - 컴퓨터 공학
  - 컴퓨터사이언스 부트캠프 with 파이썬
  - 함수
  - 람다함수
  - lambda 함수
---



[컴퓨터사이언스 부트캠프 with 파이썬](http://www.yes24.com/24/goods/58552941) 책을 공부하며 정리한 포스팅입니다.

개인 공부후 정리용으로 남기는 포스팅으로 내용상에 오류가 있을수 있습니다.

예제 코드는 [Computer-Science](https://github.com/KwonSoonWoo/Computer-Science) 를 통해 실습하고 있습니다.



**핵심 개념**

- 람다(lambda) 함수

---

**람다(lambda) 함수**

- 이름이 없는 함수
- 이름이 없기 때문에 다음 행으로 넘어가면 사용불가
  - 자주 사용할 함수가 아닐 경우 람다 함수로 만들어 사용하면 유용

```python
li = [i for i in range(1, 11)]

# 실행결과
li
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# key인자에 람다함수를 전달
li.sort(key = lambda x: x % 2 == 0)

# 실행결과
li
[1, 3, 5, 7, 9, 2, 4, 6, 8, 10]
```

- li는 1부터 10까지 정수가 순차적으로 나열된 리스트
- 위의 경우처럼 key인자에 람다함수를 전달하면
  - 2의 배수가 아닌 경우 False이므로 0
  - 2의 배수인 경우 True이므로 1

---



```python
# 변수 f로 람다 함수를 참조
f = lambda x: x ** 2

# 실행결과
f(2)
4
f(5)
25
```

- 정렬 기준으로 사용하기 위해 함수를 따로 정의하는 것은 번거롭기 때문에
- 람다 함수를 변수로 받으면 함수 정의를 한 것처럼 사용 가능

---



- 람다 함수에는 값을 반환하는 return문이 없음
- 또한, 람다 함수의 몸체에는 반드시 식이 들어가야 함.

```python
# 변수 f1으로 람다 함수 참조
f1 = lambda li, idx: li[idx]

# 변수 f2로 람다 함수 참조 시도
f2 = lambda li, idx, value: li[idx] = value
# 에러메시지 출력
SyntaxError: can't assign to lambda
```

- **```li[idx] = value```**가 할당문(assignment statement)이기 때문에 오류 발생
  - 즉, 식이 아니기 때문에 오류가 발생.
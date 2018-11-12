---
layout: post
title: (Cs with python)-함수(전역변수, 지역변수, nonlocal키워드) 
category: 컴퓨터 공학
tags:
  - 컴퓨터 공학
  - 컴퓨터사이언스 부트캠프 with 파이썬
  - 함수
  - 전역변수
  - 지역변수
  - nonlocal 키워드
---



[컴퓨터사이언스 부트캠프 with 파이썬](http://www.yes24.com/24/goods/58552941) 책을 공부하며 정리한 포스팅입니다.

개인 공부후 정리용으로 남기는 포스팅으로 내용상에 오류가 있을수 있습니다.

예제 코드는 [Computer-Science](https://github.com/KwonSoonWoo/Computer-Science) 를 통해 실습하고 있습니다.



**핵심 개념**

- 전역 변수
- 지역 변수
- nonlocal 키워드

---



**전역 변수**

- 전역 변수(global variable)는 전체 영역에서 접근할수 있는 변수

```python
# g_var는 전역변수
g_var = 10

def func():
    # 함수안에서 전역변수에 접근
    print("g_var = {}".format(g_var))
    
if __name__ == "__main__":
    func()
    
# 실행결과 
g_var = 10
```

- 그렇다면, 함수 안에서 전역변수의 값을 변경할수 있지 않을까?

```python
g_var = 10

def func():
    # 전역변수 g_var의 값을 변경 시도
	g_var = 20
	print("g_var={} in function".format(g_var))
	
if __name__ == "__main__":
	func()
	print("g_var={} in main".format(g_var))
	
# 실행결과
g_var = 20 in function
g_var = 10 in main
```

- 안된다. 왜?

- 함수안에서 선언한 ```g_var=20```이 전역변수 값을 변경시킨게 아니라

  **새로운 지역변수를 생성**한것이기 때문.

---



**지역 변수**

- 특정 지역에서만 접근 할 수 있는 변수.
  - 특정 지역 = 함수 내부
  - 전역변수와 반대 개념
  - 함수 바깥에서는 접근 불가. 함수 호출시 생성 되었다가 끝나면 사라짐.
- 그럼 위의 예시에서 전역변수의 값을 변경이 불가능한가? 그건 아니다.

```python
g_var = 10

def func():
    # 전역변수 g_var를 함수 안에서 사용하겠다고 명시
    global g_var
    # global 키워드 다음은 전역변수 값을 변경하는것을 의미
    g_var = 20
	
	
if __name__ == "__main__":
	print("g_var={} before".format(g_var))
	func()
	print("g_var={} after".format(g_var))
	
# 실행결과
g_var = 10 before
g_var = 20 after
```

---



**nonlocal 키워드**

- 외부 함수의 지역변수 값에 접근 및 변경하겠다고 내부함수에서 명시하는것.

```python
def outer():
    a = 2
    b = 3
    
    def inner():
        # outer()의 a 변수에 접근하겠다고 명시
       	# nonlocal을 쓰지 않으면 새로운 지역변수 a가 생성
        nonlocal a
        # outer()의 a 값 변경
        a = 100
	inner()
    
    print(
    "locals in outer: a = {}, b = {}".format(a, b))
    
if __name__ = "__main__":
	outer()
    
# 실행결과
locals in outer : a = 100, b = 3

```


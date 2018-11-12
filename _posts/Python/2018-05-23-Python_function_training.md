---
layout: post
title: 함수 실습
category: Python
tags:
  - Python
---



## 실습

1. 매개변수로 문자열을 받고, 해당 문자열이 ```red```면 ```apple```을, ```yellow```면 ```banana```를, ```green```이면 ```melon``` 을, 어떤 경우도 아닐 경우 ```I don't know```를 리턴하는 함수를 정의하고, 사용하여 ```result```변수에 결과를 할당하고 ```print```해본다.

```python
def what_fruit(color):
    if color == 'red':
        return 'apple'
    elif color == 'yellow':
        return 'banana'
    elif color == 'green':
        return 'melon'
    else:
        return "I don't know"
```

```python
# dict를 사용하는 법
fruit_dict = {
    'red': 'apple',
    'yellow': 'banana',
    'green': 'melon',
}
# 대괄호를 사용해서 값을 검색
# dict['red']

# get()함수를 사용해서 값을 검색
# dict.get('red')

def what_fruit2(color):
    return fruit_dict.get(color, "I don't know")
```

```python
>>> what_fruit2('white')
"I don't know"

>>> fruit_dict['red']
'apple'

>>> result = fruit_dict.get('white', "I don't know")
print(result)
I don't know
```





2. 1번에서 작성한 함수에 `docstring`을 작성하여 함수에 대한 설명을 달아보고, `help(함수명)`으로 해당 설명을 출력해본다.

   ```python
   def what_fruit2(color):
       """
       색상 문자열을 받아 해당하는 과일 문자열을 돌려주는 함수
       @color: 색상 문자열
       return: 과일 문자열
       """
       return fruit_dict.get(color, "I don't know")
   ```

3. 한 개 또는 두 개의 숫자 인자를 전달받아, 하나가 오면 제곱, 두개를 받으면 두 수의 곱을 반환해주는 함수를 정의하고 사용해본다.

   ```python
   def square(x):
       return x ** 2
   
   def multi(x, y):
       return x * y
   
   # 1. 매개변수 중 1개에 기본값을 지정 (x, y=<Default>)
   # 2. 위치인자 묶음을 사용 (*args)
   def square_or_multi_default_parameter(x, y=None):
       if y is None:
           return x * x
       else:
           return x * y
       
   # None을 Boolean판단 기준으로 사용
   # if문에 해당할 경우 함수가 return 되므로 else문 생략
   def square_or_multi_default_parameter(x, y=None):
       if y:
           return x * y
       return x ** 2
       
   # 조건표현식을 사용해서 한 줄로 처리
   def square_or_multi_default_parameter(x, y=None):
       return x * y if y else x ** 2
   
   # 위치인자 묶음을 사용
   def square_or_multi_positional_args(*args):
       args_length = len(args)
       if len(args) == 2:
           return args[0] * args[1]
       return args[0] ** 2
   
   # 위치인자 묶음을 튜플 언패킹으로 사용
   def square_or_multi_positional_args(*args):
       if len(args) == 1:
           # 튜플 언패킹 시 좌,우변을 모두 'tuple'형태로 만들어야 함
           arg1, = args
           return arg1 ** 2
       elif len(args2) == 2:
           arg1, arg2 == args
           return arg1 * arg2
       
   def square_or_multi_positional_args(*args):
       if len(args) == 1:
           # 튜플 언패킹 시 좌,우변을 모두 'tuple'형태로 만들어야 함
           arg1, = args
       elif len(args2) == 2:
           arg1, arg2 = args
           
       # if문에 따라 달라진 locals() dict에서 
       # 'arg2'키가 있
       if 'arg2' in locals():
           return arg1 * arg2
       return arg1 ** 2
   ```

4. 두 개의 숫자를 인자로 받아 합과 차를 튜플을 이용해 동시에 반환하는 함수를 정의하고 사용해본다.

   ```python
   >>> def sum_sub(x, y):
             	   return (x+y, abs(x-y))
             	   
   >>> def sum_sub(x, y):
            if x > y:
                 sub = x - y
            else:
                sub = y - x
            return (x + y, sub)
        
   >>> def sum_sub(x, y):
           return (x + y, x - y if x > y else y - x)
           
   sum_sub(5,3)
   (8, 2)
   
   sum_sub(3,5)
   (8, 2)
   ```

5. 위치인자 묶음을 매개변수로 가지며, 위치인자가 몇 개 전달되었는지를 print하고 개수를 리턴해주는 함수를 정의하고 사용해본다.

   ```python
   >>> def get_args_num(*args):
       	print(f'위치인자는 총 {len(args)}개가 전달되었습니다')
       	return len(args)
   ...
   
   result = get_args_num(2,3,4,5,6)
   위치인자는 총 5개가 전달되었습니다
   
   >>> print(result)
   5
   ```

6. 람다함수와 리스트 컴프리헨션을 사용해 한 줄로 구구단의 결과를 갖는 리스트를 생성해본다.

   ```python
   [(lambda a, b: f'{a} * {b} = {a * b}')(x, y) for x in range(2, 10) for y in range (1,10)]
   ```

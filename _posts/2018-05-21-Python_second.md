---
layout: post
title: 함수
excerpt_separator:  <!--more-->
---

## 함수

반복적인 작업을 하는 코드를 재사용이 가능하게 정의해 놓은 것.

```python
def 함수명(매개변수[parameters]):
	동작
```

**함수의 정의, 실행**

```python
# 실행 시 'call func'를 print하는 함수 정의
>>> def func():
...		print('call func')
...

# 함수 자체는 function객체를 참조하는 변수
>>> func
<function func at 0X10dabf378>

# 함수를 실행시키기 위해 () 사용
>>> func()
call func
```



**리턴값이 있는 함수 정의**

```python
>>> def return_true():
...	  return True
...
>>> return_true()
True
```

함수의 결과로 Bool값을 갖는 데이터를 리턴하여 if문이나 while문의 조건으로 사용 가능.

**매개변수를 사용하는 함수 정의**

```python
>>> def print_arguments(something):
...	  print(something)
...
>>> print_arguments('ABC')
ABC
```



**매개변수(parameter)와 인자(인수라고도 함))(argument) 의 차이**

매개변수 : 함수 내부에서 함수에게 전달되어 온 변수.

인자(인수라고도 함): 함수를 호출할 때 전달하는 변수.

```python
# 함수 정의때는 매개변수
def func(매개변수1, 매개변수2):
  ...
  
# 함수 호출시에는 인자
>>> func(인자1, 인자2)
```

**리턴값이 없을 경우**

함수에서 리턴해 주는 값이 없을 경우, 아무것도 없다는 뜻을 가진 ```None```객체를 얻는다.

**위치 인자(Positional arguments)**

매개변수의 순서대로 인자를 전달하여 사용하는 경우

```
>>> def student(name, age, gender):
...	  return {'name': name, 'age': age, 'gender': gender}
...
>>> student('hanyeong.lee', 31, 'male')
{'name': 'hanyeong.lee'}
```


---
layout: post
title: Python 용어정리 및 숫자와 문자열
category: Python
tags:
  - Python
  - Python 용어정리 및 숫자와 문자열
---



## 용어정리

#### 리터럴

변하지 않는 고정된 데이터 자체의 표현

- 5 (정수형 데이터)
- 'Fastcampus' (문자열 데이터)
- 1.4937 (부동소수점 데이터)

#### 표현식(expression)

값을 의미하는 표현 또는 값을 반환하는 표현

```javascript
>>> sec = 60
>>> 365*24*sec  # 표현식
525600			# 정수 525600의 리터럴 값
```



#### 구문(statement)

값의 의미를 지니지 않으며, 어떠한 목적을 수행하는 코드

```python
>>> for char in '안녕하세요':   #구문 (제어문)
...		print(char)
...
안
녕
하
세
요
```



## 실습

1. 파이썬 인터프리터를 계산기처럼 사용해서 1년이 총 몇 초인지 계산해보시오.





## 문자열

> 파이썬3에서는 문자열에서 기본적으로 유니코드(Unicode)를 사용하며, 불변(immutable)하다.



### 문자열 표현

---

#### 작은 따옴표 또는 큰 따옴표

```python
>>> '권순우'
'권순우'
>>> "권순우"
'권순우'
```

작은 따옴표 또는 큰 따옴표를 사용했을 때, 사용하지 않은 인용 부호는 문자열 내부에서 사용 가능.

```python
>>> '패스트캠퍼스 "웹 프로그래밍 스쿨"'
'패스트캠퍼스 "웹 프로그래밍 스쿨"'
```

**세 개의 작은 따옴표 또는 큰 따옴표**

여러줄에 걸친 문자열을 나타낼 때 사용

``` python
>>> '''소환사 여러분.
...
... 7.1 패치를 소개합니다.
...
... 앞으로 있을 여러 번의 패치에 대해서는 차차...
... 하지만 그렇다고 이번 패치가 하향....
... 정의의 전장에서 승리를 기원합니다.'''
```



## 문자열 더하기

```
>>> notice = ''
>>> notice += '공지사항'
>>> notice += '(패치노트)'
>>> notice += ': 7.1 패치노트'
```



## 형변환

내장함수 **str**을 사용

```
>>> str(147)
'147'
```

문자열을 제외한 객체를 ```print``` 함수로 호출하면, 내부적으로 ```str```함수를 사용한 결과를 나타내준다.



## 인덱스 연산

문자열에서 문자를 추출하기 위해 대괄호와 오프셋을 지정할 수 있다.

가장 왼쪽은 0, 가장 오른쪽은 -1로 시작.

```
>>> lux = '빛으로 강타해요!'
>>> lux[0]
'빛'
>>> lux[-1]
'!'
>>> lux[50]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: string index out of range
```

문자열은 불변이므로 인덱싱한 부분에 새 값을 대입할 수 없다.

```
>>> lux[0] = '손'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
```



## 슬라이스 연산

```[start:end:step]```형식을 사용한다.

- ```[:]```
  - 처음부터 끝까지
- ```[start:]```
  - start오프셋부터 마지막까지
- ```[:end]```
  - 처음부터 end오프셋까지
- ```[start:end]```
  - start오프셋부터 end오프셋까지
- ```[start:end:step]```
  - start 오프셋부터 end 오프셋까지, step만큼씩 뛰어넘은 부분



## 길이

내장함수 **len** 을 사용



## 문자열 나누기(split)

문자열의 내장함수 **split**을 사용

**split**함수에 인자로 주어진 **구분자**를 기준으로 하나의 문자열을 리스트 형태로 반환.

```python
>>> girlsday = "민아,유라,소진,혜리"
>>> girlsday.split(',')
['민아', '유라', '소진', '혜리']
```

**split**함수에 인자를 주지 않을 경우, 공백문자를 구분자로 사용한다.



## 문자열 결합(join)

**split** 함수와 반대의 역할을 한다.

문자열 리스트를 하나의 문자열로 결합, 각 문자열을 결합해줄 구분자 문자열을 지정 후 **join**함수를 사용해줌.

``` python
>>> girlsday_list = girlsday.split(',')
>>> girlsday_str = ', '.join(girlsday_list)
>>> print(girlsday_str)
민아, 유라, 소진, 혜리
```



## 대소문자 다루기

```python
>>> lux = 'lux, the Lady of Luminosity'
>>> lux.capitalize()
'Lux, the lady of luminosity'
>>> lux.title()
'Lux, The Lady Of Luminosity'
>>> lux.upper()
'LUX, THE LADY OF LUMINOSITY'
>>> lux.lower()
'lux, the lady of luminosity'
>>> lux.swapcase()
'LUX, THE lADY OF lUMINOSITY'
```



## 공식문서

[Text Sequence - String Methods](https://docs.python.org/3/library/stdtypes.html#string-methods)



## 문자열 포맷

**옛 스타일(%)**

```
string % data

>>> '%s' % 42
'42'
>>> '%d x %d : %d' % (3, 4, 12)
'3 x 4 : 12'
```

**새 스타일 ({}, format)**

```python
{}.format(변수)

# 기본형태
>>> '{} {} {}'.format(d, f, s)
'37 3.14 Fastcampus'

# 각 인자의 순서를 지정
>>> '{1} {2} {0}'.format(d, f, s)
'3.14 Fastcampus 37'

# 각 인자에 이름을 지정
>>> '{d} {f} {s}'.format(d=50, f=1.432, s='WPS')
'50 1.432 WPS'

# 딕셔너리로부터 변수 할당
>>> dict = {'d': d, 'f': f, 's': s}
>>> '{0[d]} {0[f]} {0[s]} {1}'.format(dict, 'WPS')
'37 3.14 Fastcampus WPS'
```



**```f``` 표현법**

```
f'{변수 또는 표현식}'

# 기본 형태
apple = '사과'
banana = '바나나'
train = '기차'

f'{apple}는 맛있어 맛있으면 {banana} {banana}는 길어 길면 {train}'

# 옵션 지정
f'''{apple:^10}
{banana:^10}
{train:^10}'''
```

> format string의 경우 문자열로 만든 다음 나중에 활용이 가능하지만, f표현식은 바로 내부에 사용할 변수가 들어있어야 적용가능.



## 실습

1. 여러 줄의 텍스트를 `multi_lines`변수에 할당하고, `print()`함수로의 출력과 인터프리터의 자동 출력(변수명 입력)을 비교해보시오.

2. `str1`, `str2`변수에 각각 문자열을 할당하고, 두 변수를 결합해 `str3`변수에 할당해보시오.

3. `str1`변수에 `*`연산자를 사용한 결과를 출력해보시오.

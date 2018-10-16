---
layout: post
title: (Cs with python)-객체지향(클래스 메서드, 정적 메서드) 
category: 컴퓨터 공학
tags:
  - 컴퓨터 공학
  - 컴퓨터사이언스 부트캠프 with 파이썬
  - 객체지향
  - 클래스 메서드
  - 정적 메서드
  - classmethod
  - staticmethod
---



[컴퓨터사이언스 부트캠프 with 파이썬](http://www.yes24.com/24/goods/58552941) 책을 공부하며 정리한 포스팅입니다.

개인 공부후 정리용으로 남기는 포스팅으로 내용상에 오류가 있을수 있습니다.

예제 코드는 [Computer-Science](https://github.com/KwonSoonWoo/Computer-Science) 를 통해 실습하고 있습니다.



**핵심 개념**

- 클래스 메서드(classmethod)
- 정적 메서드(staticmethod)

---

**정적 메서드(staticmethod)**

```python
class A:
    @staticmethod
    def f():                #1
        print('static method')

    @classmethod
    def g(cls):             #2
        print(cls.__name__)


if __name__ == "__main__":
    a = A()
    a.f()
    a.g()

    
# 실행결과
static method
A
```

- ```def f():```은 정적 메서드(#1)
- 인자로 클래스나 객체를 받지 않는다
- 클래스 A의 namespace에 있을 뿐 일반 함수와 같으며 전역 함수를 대체하기에 가장 알맞다

---

**클래스 메서드(classmethod)**

- 위의 코드에서 ```def g():```는 클래스 메서드(#2)
- 첫 번째 인자로 클래스 A를 받는다
- 클래스 메서드는 **대체 생성자**로도 쓰인다.

---

**대체 생성자의 예시**

```python
class Person:
    def __init__(self, name, age):      #1
        self.name = name
        self.age = age
    @classmethod
    def init_from_string(cls, string):  #2
        '''
        string format : '<name>_<age>'
        '''
        name, age = string.split('_')
        return cls(name, int(age))      #3


if __name__ == "__main__":
    p = Person.init_from_string('greg_30') #4
    print(p.name)
    print(p.age)

# 실행결과
greg
30
```

- ```def __init__(self, name, age):```는 일반적인 생성자(#1)
  - 인자로 문자열 name과 숫자 age를 입력받는다.
- 하지만, 객체의 멤버 데이터가 문자열로 들어오고 그 형태가 ```<name>_<age>```라면
- 클래스 메서드로 대체 생성자를 만들어 일반 생성자 대신 객체를 만들 수 있다.
  - ```init_from_string()```메서드는 ```<name>_<age>```형태의 문자열을 인자로 받아(#2)
  - 이를 분석하여 일반적인 생성자를 다시 호출 -> ```return cls(name, int(age))```

- 이렇게 메서드를 설계해 두면 필요할 때마다 클래스 메서드를 호출해서 객체를 만들수 있어 편리함
  - ex) ```p = Person.init_from_string('greg_30')```
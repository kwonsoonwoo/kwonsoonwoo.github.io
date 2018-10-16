---
layout: post
title: (Cs with python)-객체지향(캡슐화, 객체, 인스턴스, 클래스) 
category: 컴퓨터 공학
tags:
  - 컴퓨터 공학
  - 컴퓨터사이언스 부트캠프 with 파이썬
  - 객체지향
  - 캡슐화
  - 객체
  - 인스턴스
  - 클래스
---



[컴퓨터사이언스 부트캠프 with 파이썬](http://www.yes24.com/24/goods/58552941) 책을 공부하며 정리한 포스팅입니다.

개인 공부후 정리용으로 남기는 포스팅으로 내용상에 오류가 있을수 있습니다.

예제 코드는 [Computer-Science](https://github.com/KwonSoonWoo/Computer-Science) 를 통해 실습하고 있습니다.



**핵심 개념**

- 캡슐화(encapsulation)
- 객체
- 인스턴스
- 클래스

---

**객체 지향 프로그래밍**

현실 세계를 모델링 하거나 프로그램을 구현하는 데 있어

변수와 함수를 가진 객체를 이용하는 패러다임.

---

**캡슐화(encapsulation)**

변수(데이터)와 함수를 하나의 단위(대부분 언어에서 클래스)로 묶는 것.

```python
# 인스턴스 멤버 초기화
# 두 개의 변수(데이터)와 세 개의 함수를 가진 객체 딕셔너리 반환
def person_init(name, money):
    # 딕셔너리에 두 변수(데이터)삽입
    obj = {'name': name, 'money': money}
    # Person(튜플)의 1번 인덱스 값(함수)부터 차례대로 삽입
    obj['give_money'] = Person[1]
    obj['get_money'] = Person[2]
    obj['show'] = Person[3]
    return obj

# 아래 3개의 함수는 person_init()함수에서 객체 obj에 삽입하는 함수
# 한 사람 객체(self)가 다른 사람 객체(other)에게 돈을 주는 함수
# 인자 중 other가 돈을 받는 사람 객체를 의미
def give_money(self, other, money):
    # 주는 사람 객체(self)의 돈은 줄어듬
    self['money'] -= money
    # 받는 사람 객체(other)의 돈은 늘어남
    # 밑에 있는 get_money() 함수를 호출하여 변수(money)변경
    other['get_money'](other, money)

# 메시지 패싱 <- 밑에 별도 개념 정리
def get_money(self, money):
    self['money'] += money

def show(self):
    print('{} : {}'.format(self['name'], self['money']))

# 클래스로 만들어지진 않지만 튜플로 묶고 있을 뿐, 정확히 클래스처럼 동작
Person = person_init, give_money, get_money, show

if __name__ == "__main__":
    # 5000원을 가진 greg객체 생성
    g = Person[0]('greg', 5000)
    # 2000원을 가진 john객체 생성
    j = Person[0]('john', 2000)

    # 돈 주기전의 greg과 john의 상태
    g['show'](g)
    j['show'](j)
    print('')
	
    # 메시지 패싱
    # greg이 john에게 2000원을 줌
    g['give_money'](g, j, 2000)

    # 돈을 주고 난후 greg과 john의 상태
    g['show'](g)
    j['show'](j)
    
# 실행결과
greg : 5000
john : 2000

greg : 3000
john : 4000
```

- **메시지 패싱(message passing)**

  - 서로 다른 객체가 함수 호출을 통해 상호 작용하여

    객체의 상태(데이터)가 변하는 것.

---

**인스턴스**

- 객체와 유사한 개념
- 둘의 차이점
  - 객체: **객체 자체에 초점**을 맞춘 용어
  - 인스턴스: 해당 객체가 어떤 **클래스에서 만들어졌는지에 초점**을 맞춘 용어

---

**클래스를 통해 객체 만들기**

```python
# Person이라는 클래스 선언
class Person:
    # 생성자(constructor)
    def __init__(self, name, money):
        # self는 객체 자신을 의미
        # self의 멤버인 name과 money를 전달받은 인자들에 할당
        self.name = name
        self.money = money

    # Person클래스의 메서드
    def give_money(self, other, money):
        self.money -= money
        other.get_money(money)

    # Person클래스의 메서드
    def get_money(self, money):
        self.money += money

    # Person클래스의 메서드
    def show(self):
        print('{} : {}'.format(self.name, self.money))
        
if __name__ == "__main__":
    # Person클래스의 인스턴스 만듬
    g = Person('greg', 5000)
    j = Person('john', 2000)

    g.show()
    j.show()

    # john에게 돈을 전달
    g.give_money(j, 2000)
    print('')

    g.show()
    j.show()
    
# 실행결과
greg : 5000
john : 2000

greg : 3000
john : 4000
```

- **생성자(constructor)** - 인스턴스 멤버를 초기화

- **메서드(method)** - 클래스안에서 동작하는 함수

- **속성(attribute)** - 멤버 + 메서드

- give_money()를 호출하는 부분에서 차이점이 발생한다.

  - 함수로만 짜여진 코드에서는 첫 번째 인자로 함수를 호출하는 객체를 전달

  - 이번 코드에서는 전달하지 않음

  - 그 이유는 인스턴스 메서드를 호출하면 객체가 자동으로 첫 번째 인자인

    self로 객체 자신을 전달하기 때문


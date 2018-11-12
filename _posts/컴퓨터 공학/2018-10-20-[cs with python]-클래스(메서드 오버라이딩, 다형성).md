---
layout: post
title: (Cs with python)-클래스(메서드 오버라이딩, 다형성, 추상클래스)
category: 컴퓨터 공학
tags:
  - 컴퓨터 공학
  - 컴퓨터사이언스 부트캠프 with 파이썬
  - 클래스
  - 메서드 오버라이딩
  - 다형성
  - polymorphism
  - 추상클래스
  - abstract class
---



> [컴퓨터사이언스 부트캠프 with 파이썬](http://www.yes24.com/24/goods/58552941) 책을 공부하며 정리한 포스팅입니다.
>
> 개인 공부후 정리용으로 남기는 포스팅으로 내용상에 오류가 있을수 있습니다.
>
> 예제 코드는 [Computer-Science](https://github.com/KwonSoonWoo/Computer-Science) 를 통해 실습하고 있습니다.

---

### 핵심개념

- 메서드 오버라이딩
- 다형성(polymorphism)
- 추상클래스(abstract class)

---

### 다형성

- [상속](https://kwonsoonwoo.github.io/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B3%B5%ED%95%99/2018/10/19/cs-with-python-%ED%81%B4%EB%9E%98%EC%8A%A4(IS-A-%EC%83%81%EC%86%8D,-HAS-A-%ED%95%A9%EC%84%B1-%EB%98%90%EB%8A%94-%ED%86%B5%ED%95%A9).html) 관계에 있는 다양한 클래스의 객체에서 같은 이름의 메서드를 호출할 때
- 각 객체가 서로 다르게 구현된 메서드를 호출함으로써
- 서로 다른 행동(behavior), 기능, 결과를 가져오는 것

---

### 코드예시

```python
class Animal:
    # 모든 파생 클래스가 공통으로 가질 메서드
    def eat(self):
        print('eat something')

# Lion 객체는 육식 동물이라 고기를 먹음
class Lion(Animal):
    # 메서드 오버라이딩
    def eat(self):
        print('eat meat')


# Deer 객체는 초식 동물이라 풀을 먹음
class Deer(Animal):
    # 메서드 오버라이딩
    def eat(self):
        print('eat grass')

# Human 객체는 잡식 동물이라 고기와 풀을 모두 먹음
class Human(Animal):
    # 메서드 오버라이딩
    def eat(self):
        print('eat meat and grass')


# 테스트 코드 실행
if __name__ == '__main__':
    animals = []
    animals.append(Lion())
    animals.append(Deer())
    animals.append(Human())

    for animal in animals:
        # 다형성을 구현한 부분
        animal.eat()


# 실행결과
eat meat
eat grass
eat meat and grass
```

- 다형성을 구현한 부분 - animal.eat()
  - 메서드를 호출한 쪽에서는 객체가 어떤 동물인지 신경 쓸 필요가 없다.
  - 각각의 객체는 자신의 클래스에 오버라이딩된 메서드를 호출하기 때문이다.
  - 실행 결과를 통해 모두 다르다는 걸 알수 있다.

---

### 추상 클래스(Abstract class)

- 세상에는 고기(meat)를 먹거나 풀(grass)을 먹거나 고기와 풀(meat and grass)을 모두 먹는 동물만 있다.
- 이러한 공통 특성을 가진 부모 클래스를 만들고 해당 클래스는 **객체 인스턴스를 생성할 수 없게** 하는것을 추상 클래스(abstract class)라고 한다.
  - 함수의 몸체(body)가 없는 추상 메서드(abstract method)를 하나 이상 가지고 있어야 하며
  - 추상 클래스를 상속받는 파생 클래스에서는 추상 메서드를 반드시 오버라이딩 해야됨
  - 그렇지 않으면 파생 클래스도 추상 클래스가 되어 인스턴스를 만들 수 없다.

---

### 코드예시

```python
# abc(abstract base class의 약자)모듈을 가져온다.
from abc import *

class Animal(metaclass = ABCMeta):
    # 추상메서드로 만들고 싶은 메서드 위에 데코레이터를 붙인다.
    @abstractmethod
    def eat(self):
        # 메서드 구현부를 pass로 해 함수 몸체를 비워두면 추상 메서드가 됨
        pass

class Lion(Animal):
    def eat(self):
        print('eat meat')

class Deer(Animal):
    def eat(self):
        print('eat grass')

class Human(Animal):
    def eat(self):
        print('eat meat and grass')

# 테스트 코드 실행
if __name__ == "__main__":
    animals = []
    animals.append(Lion())
    animals.append(Deer())
    animals.append(Human())

    for animal in animals:
        animal.eat()


a = Animal()

# 실행결과
eat meat
eat grass
eat meat and grass
Traceback (most recent call last):
  File "polymorphism_2.py", line 30, in <module>
    a = Animal()
TypeError: Can't instantiate abstract class Animal with abstract methods eat
```

- 추상 메서드를 만들게 되면 모든 파생 클래스는 내부의 eat() 메서드를 반드시 오버라이딩 해야됨.
- 실행결과를 보면 추상 메서드 eat을 가진 추상 클래스 Animal 의 인스턴스를 만들수 없다고 적혀 있음.

---

### 메서드 오버라이딩

- 다형성을 구현하기 위해 파생 클래스 안에서 상속받은 메서드를 다시 구현하는 것.

---

### 코드예시

```python
class CarOwner:
    def __init__(self, name):
        self.name = name

    def concentrate(self):
        print('{} can not do anything else'.format(self.name))

    # 나머지 메서드


class Car:
    def __init__(self, owner_name):
        self.owner = CarOwner(owner_name)

    def drive(self):
        # Car 객체는 반드시 차 주인인 CarOwner 객체가 운전해야 하며
        # 차 주인은 운전에만 집중해야 한다.
        # drive 메서드가 시작하자마자 concentrate() 메서드를 호출해
        # 차 주인이 운전 외에는 아무것도 하지 못하게 한다.
        self.owner.concentrate()
        # 차 주인이 현재 운전하는 상태임을 나타내는 print 문
        print('{} is driving now.'.format(self.owner.name))


# SelfDrivingCar 클래스는 Car 클래스를 상속받는다
# drive() 메서드를 뺀 나머지 멤버나 메서드는 여전히 유효
class SelfDrivingCar(Car):
    # 자율주행차에 drive() 메서드가 어울리지 않기 때문에
    # drive() 메서드만 다시 정의 <- 메서드 오버라이딩
    def drive(self):
        print('Car is driving by itself')


# 테스트 코드 작성
if __name__ == '__main__':
    car = Car('Greg')
    car.drive()
    print('')


    s_car = SelfDrivingCar('John')
    s_car.drive()

# 실행결과
Greg can not do anything else
Greg is driving now.

Car is driving by itself
```


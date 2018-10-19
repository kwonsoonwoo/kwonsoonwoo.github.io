---
layout: post
title: (Cs with python)-클래스(is-a, has-a)
category: 컴퓨터 공학
tags:
  - 컴퓨터 공학
  - 컴퓨터사이언스 부트캠프 with 파이썬
  - 클래스
  - is-a
  - has-a
---



> [컴퓨터사이언스 부트캠프 with 파이썬](http://www.yes24.com/24/goods/58552941) 책을 공부하며 정리한 포스팅입니다.
>
> 개인 공부후 정리용으로 남기는 포스팅으로 내용상에 오류가 있을수 있습니다.
>
> 예제 코드는 [Computer-Science](https://github.com/KwonSoonWoo/Computer-Science) 를 통해 실습하고 있습니다.

---

### 핵심개념

- is-a: 상속
- has-a: 합성 또는 통합



---

### IS-A: 상속

- "~은 ~의 한 종류다' 를 의미한다.
- 노트북은 컴퓨터의 한 종류다 라는 문장은 관계가 성립한다.
  - 따라서, Computer 클래스와 Laptop 클래스는 IS-A 관계.
- IS-A 관계를 프로그램에서 표현할 때는 상속(inheritance)을 사용
- 상속
  - 객체 지향의 근간.
  - IS-A 관계가 아닐때 상속을 하면 클래스를 설계하는 데 어려움이 따른다.
  - 상속을 하는 클래스: 기본(base)클래스, 부모(parent)클래스, 슈퍼(super)클래스
  - 상속받는 클래스: 파생(derived)클래스, 자식(child)클래스, 서브(sub)클래스

---

### 코드예시

```python
# 컴퓨터 클래스
class Computer:
    def __init__(self, cpu, ram):
        # 인스턴스 멤버
        self.CPU = cpu
        self.RAM = ram

    # 웹 서핑을 하는 메서드
    def browse(self):
        print('browse')


    # 일을 하는 메서드
    def work(self):
        print('work')


# 노트북 클래스
# (Computer) <- 컴퓨터 클래스를 상속한다
# 컴퓨터 클래스의 모든 멤버와 메서드를 가짐.
class Laptop(Computer):
    # 멤버 추가
    def __init__(self, cpu, ram, battery):
        # super는 현재 클래스의 슈퍼 클래스 즉, 기본 클래스를 의미
        super().__init__(cpu, ram)
        self.battery = battery

    # 메서드 추가
    def move(self, to):
        print('move to {}'.format(to))

# 테스트 코드
if __name__ == '__main__':
    lap = Laptop('intel', 16, 'powerful')
    lap.browse()
    lap.work()
    lap.move('office')

# 실행결과
browse
work
move to office
```

- class Laptop(Computer)
  - Computer 클래스 상속
  - Computer 클래스의 모든 멤버와 메서드를 가진다.
  - 즉, browse() 메서드나 work() 메서드를 정의하지 않아도 됨.

---

### HAS-A: 합성 또는 통합

- "~이 ~을 가진다 혹은 포함한다"를 의미
  - 컴퓨터는 CPU와 RAM을 가지고 있음
  - A Computer HAS-A CPU에서 가지고 있다 라는 의미가 HAS-A이므로 HAS-A 관계
- 프로그램에서 HAS-A 관계는 합성(composition) 혹은 통합(aggregation)을 이용해 표현
- 합성과 통합의 차이점에 대해 알아보자.

---

### 합성의 코드예시

- 컴퓨터와 CPU의 관계를 합성으로 표현한다

```python
class CPU:
    pass


class RAM:
    pass

class Computer:
    def __init__(self):
        # 생성자에서 CPU객체를 생성하여 멤버 cpu에 할당
        self.cpu = CPU()
        self.ram = RAM()

```

- 현실세계처럼 Computer 객체가 만들어지거나 사라질 때 CPU 객체도 함께 만들어지거나 사라짐
- Computer 객체와 CPU객체는 생명주기가 같고 컴퓨터가 CPU를 소유하고 있는 모양새

---

### 통합의 코드예시

- 경찰과 총의 관계를 통합으로 표현한다

```python
class Gun:
    def __init__(self, kind):
        self.kind = kind

    def bang(self):
        print('bang bang')


class Police:
    def __init__(self):
        # Police 인스턴스가 만들어질때 Gun객체를 갖고 있지 않다.
        self.gun = None

    # acquire_gun 메서드를 통해 Gun객체를 멤버로 가지게 됨.
    def acquire_gun(self, gun):
        self.gun = gun

	# release_gun 메서드를 통해 가지고 있던 총을 반납할수도 있음.
    def release_gun(self):
        gun = self.gun
        self.gun = None
        return Gun

    def shoot(self):
        if self.gun:
            self.gun.bang()
        else:
            print('Unable to shoot')

# 테스트 코드 작성
if __name__ == '__main__':
    p1 = Police()
    print('p1 shoots')
    p1.shoot()
    print('')

    # p1은 아직 총을 소유하지 않음
    revolver = Gun('Revolver')
    # p1이 revolver를 획득
    p1.acquire_gun(revolver)
    # 이제 p1이 총을 소유하므로
    # revolver는 None이 된다
    revolver = None
    print('p1 shoots again')
    p1.shoot()
    print('')

    # p1이 총을 반납했으므로
    # 더 이상 총을 소유하지 않는다
    revolver = p1.release_gun()
    print('p1 shoots again')
    p1.shoot()

    
# 실행결과
p1 shoots
Unable to shoot

p1 shoots again
bang bang!

p1 shoots again
Unable to shoot
```

- Police 객체와 Gun 객체는 생명주기를 함께 하지 않는 상대적으로 약한 관계
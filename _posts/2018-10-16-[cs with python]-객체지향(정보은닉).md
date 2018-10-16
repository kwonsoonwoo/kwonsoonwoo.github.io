---
layout: post
title: (Cs with python)-객체지향(정보은닉) 
category: 컴퓨터 공학
tags:
  - 컴퓨터 공학
  - 컴퓨터사이언스 부트캠프 with 파이썬
  - 객체지향
  - 정보은닉
  - information hiding
---



[컴퓨터사이언스 부트캠프 with 파이썬](http://www.yes24.com/24/goods/58552941) 책을 공부하며 정리한 포스팅입니다.

개인 공부후 정리용으로 남기는 포스팅으로 내용상에 오류가 있을수 있습니다.

예제 코드는 [Computer-Science](https://github.com/KwonSoonWoo/Computer-Science) 를 통해 실습하고 있습니다.



**핵심 개념**

- 정보은닉(information hiding)

---

**정보은닉(information hiding)**

- [캡슐화](https://kwonsoonwoo.github.io/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B3%B5%ED%95%99/2018/10/14/cs-with-python-%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5(%EC%BA%A1%EC%8A%90%ED%99%94,-%EA%B0%9D%EC%B2%B4,-%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4,-%ED%81%B4%EB%9E%98%EC%8A%A4).html)할 때 멤버와 메서드별로 유저 프로그래머가 사용할 수 있도록 공개하거나 접근할 수 없도록 할 것인지 정하는 것
- 캡슐화는 정보 은닉을 포함하는 개념.
- OOP에서 잘된 정보 은닉은 필요한 메서드만 공개하고 나머지는 모두 숨기는 것이다.

---

**C++의 정보 은닉**

```java
class Account{
// 유저 프로그래머가 접근하거나 호출할 수 있음
public:
  // 생성자: 파이썬 클래스의 __init__()과 같다
  Account(string name,, int money){
    user = name;
    balance = money;
  }
  // 인스턴스 메서드(멤버 함수)
  int get_balance(){
    return balance;
  }
  // 인스턴스 메서드(멤버 함수)
  void set_balance(int money){
    if(money < 0) {
      return;
    }

    balance = money;
  }

// 클래스 안에서만 사용할 수 있고 객체를 통해서는 접근하거나 호출할수 없음
private:
  // 인스턴스 멤버(멤버 변수)
  string user;
  int balance;
};

int main(void){
  Account my_acnt("greg", 5000);

  // my_acnt라는 객체를 사용해 balance 멤버에 접근.
  my_acnt.balance; // #1.
  
  my_acnt.set_balance(-3000); // #2.

  cout << my_acnt.get_balance() << end1;

  return 0;
}

// 실행결과
// #1 으로 실행했을 경우 컴파일 오류 발생
"Account::balance : cannot access private member declared in class 'Account'"

// #2 로 실행했을 경우
5000
```

- public, private : 접근 제어 지시자(access modifier)
  - 접근 제어 지시자의 키워드는 public, protected, private 총 3가지 종류가 있음.
- private으로 숨겨진 멤버에 명시적으로 접근했기 때문에 컴파일 오류가 남.
- 위 코드를 통해 본 멤버를 숨김으로써 얻을수 있는 장점
  - set_balance() 메서드를 보면 통장 잔액이 음수가 될수 는 없다.
  - 하지만, private으로 balance 멤버를 숨기지 않았다면 유저 프로그래머가 실수로 음수를 입력할 수 있다.
  - set_balance()를 통해서만 balance 값을 변경하게 만들어 실수 가능성을 줄이고
  - 이 경우에는 함수 안에서 인자로 음수를 전달하면 balance값을 변경하지 않고 함수를 종료하기 때문에 원천적으로 balance에 음수가 입력되는 상황을 막을 수 있음.

- 멤버가 접근하거나 변경해야 할 때는 엑세스 함수(access function)를 사용해야 함.
  - 이 코드의 경우 get_balance(), set_balance() 메서드가 엑세스 함수.

---

**파이썬의 정보 은닉**

파이썬은 기본적으로 정보 은닉을 지원하지 않음.

위의 C++코드를 파이썬으로 변경.

```python
class Account:
    def __init__(self, name, money):
        self.user = name
        self.balance = money

    def get_balance(self):
        return self.balance

    def set_balance(self, money):
        if money < 0:
            return

        self.balance = money

if __name__ == "__main__":
    my_acnt = Account('greg', 5000)
    # C++에서는 접근할 수 없었던 balance멤버에 접근해 음수로 값을 바꿈.
    my_acnt.balance = -3000

    print(my_acnt.get_balance())

# 실행 결과
-3000
```

- 파이썬에서는 정보 은닉이 불가능하지만 유저 프로그래머의 실수를 막을 수 있는 방법은 제공한다.
  - **숨기려는 멤버 앞에 언더바(_)를 두 개 붙이기**
  - **프로퍼티 기법**

---

**숨기려는 멤버 앞에 언더바(_)를 두 개 붙이기**

```python
class Account:
    def __init__(self, name, money):
        self.user = name
        self.__balance = money


    def get_balance(self):
        return self.__balance


    def set_balance(self, money):
        if money < 0:
            return
        self.__balance = money

if __name__ == "__main__":
    my_acnt = Account('greg', 5000)
    my_acnt.__balance = -3000


    print(my_acnt.get_balance())

# 실행 결과
5000
```

- balance멤버를 모두 __balance로 바꿈.
- 마치, 정보 은닉이 된 것처럼 보이지만 실제로 정보 은닉이 된 것은 아님.

```python
# REPL 환경에서 실행(ipython 혹은 python)
>>> my_acnt.__dict__
{'user': 'greg', '_Account__balance': 5000, '__balance': -3000}
```

- ```my_acnt.__dict__```를 통해 멤버를 확인할 수 있는데 만든적이 없는 ```_Account__balance```라는 멤버가 보인다.
- 이유는 클래스 안에서 **언더바(_)를 두 개** 붙이면 이 멤버는 객체가 만들어질 때 이름이 **"_클래스 이름"**이 멤버 앞에 붙게 된다.
  - 생성자에서 선언한 인스턴스 멤버 ```__balance```가 -> ```_Account_balance```로 바뀜
- 하지만, 유저 프로그래머도 이를 알수 있으므로 얼마든지 접근하여 변경 가능
- 파이썬은 유저 프로그래머의 실수는 막아주지만 의도적인 변경까지는 책임지지 않는다.

- -3000을 값으로 갖는 ```__balance```멤버는 my_acnt 객체만의 멤버를 새롭게 만든것.
  - 다른 Account 인스턴스와 달리 my_acnt는 ```__balance```라는 멤버를 하나 더 갖게된 것.

---

**프로퍼티(property)**

멤버에 접근하는 것 처럼 보이지만 실제로는 메서드를 호출한다.

```python
class Account:
    def __init__(self, name, money):
        self.user = name
        # 인스턴스 멤버 선언이 아니라 #3의 setter 메서드를 호출
        self.balance = money	#1


    # property 데코레이터를 함수 정의에 붙임
    # getter함수가 되어 C++코드의 get_balance() 메서드와 같은 역할을 함
    @property
    def balance(self):			#2
        return self._balance


    # C++코드의 set_balance() 메서드와 같은 역할을 함.
    @balance.setter
    def balance(self, money):	#3
        if money < 0:
            return


        # 실제 인스턴스 멤버 선언이 일어나는 부분(#1 실행시(생성자 호출시))
        self._balance = money

if __name__ == '__main__':
    my_acnt = Account('greg', 5000)
    # my_acnt 객체의 balance라는 멤버에 접근해 값을 변경하는 것이 아님
    # setter함수인 balance()를 호출하기 때문에
    # _balance 멤버의 값을 음수로 변경되지 않음.
    my_acnt.balance = -3000		#4

    # getter함수인 balance()메서드를 호출해 _balance 멤버에 접근
    # #4에서 음수로 변경되지 않았으므로 실행결과는 5000
    print(my_acnt.balance)		#5

# 실행결과
5000
```

- 하지만, 이 방법도 유저 프로그래머가 멤버로 접근하는 것을 원천적으로 막을수는 없음

```python
# REPL 환경에서 실행(ipython 혹은 python)
>>> my_acnt.__dict__
{'user: 'greg', '_balance': 5000}
>>> my_acnt._balance = -3000
>>> my_acnt.balance
-3000
```

- ```__dict__```로 멤버를 확인할 수 있고 ```_balance```멤버로 접근해 값을 음수로 변경하면 setter함수를 통해 변경하는 것이 아니므로 ```_balance```값이 음수로 바뀜


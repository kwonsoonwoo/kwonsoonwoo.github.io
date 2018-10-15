---
layout: post
title: (Cs with python)-함수호출방식(call-by-value, call-by-reference, call-by-assignment) 
category: 컴퓨터 공학
tags:
  - 컴퓨터 공학
  - 컴퓨터사이언스 부트캠프 with 파이썬
  - 함수
  - 값에 의한 전달
  - call by value
  - 참조에 의한 전달
  - call by reference
  - 객체 참조에 의한 전달
  - call by assignment
---



[컴퓨터사이언스 부트캠프 with 파이썬](http://www.yes24.com/24/goods/58552941) 책을 공부하며 정리한 포스팅입니다.

개인 공부후 정리용으로 남기는 포스팅으로 내용상에 오류가 있을수 있습니다.

예제 코드는 [Computer-Science](https://github.com/KwonSoonWoo/Computer-Science) 를 통해 실습하고 있습니다.



**핵심 개념**

- call by value(값에 의한 전달)
- call by reference(참조에 의한 전달)
- call by assignment(객체 참조에 의한 전달)

---



**call-by-value(값에 의한 전달)**

- 인자를 전달할 때 값을 복사해 전달하는 경우를 뜻함.

```c++
#include <iostream>
using namespace std;

void change_value(int x, int value) 
{
  x = value;                        
  cout << "x:" << x << "in change_value" << endl;
}

int main(void)
{
  // 지역 변수 x에 10 대입
  int x = 10;
  change_value(x, 20);               
  cout << "x:" << x <<" in main" << endl;

  return 0;
}

// 실행결과
x : 20 in change_value
x : 10 in main
```

- main()함수에서 change_value()함수를 호출하면서 value인자로 20을 전달했지만

  지역 변수 x값은 함수안에서만 변경되고 호출한 쪽에서는 변경이 안됨.

- 그 이유를 알기 위해선 자료구조-스택 에서 스택 프레임에 대한 개념을 알아야 함.

- 스택 프레임(Stack Frame): 함수 호출시 할당되는 메모리 블록(지역변수가 존재하는 영역)

  - 데이터 저장시 순차적으로, 꺼낼때는 맨 위부터 차례대로 내림.

- 위의 함수 동작을 스택프레임 측면에서 표현하면 아래와 같이 표현할수 있다.

**1. x = value; 가 실행되기 직전**

| change_value() 스택 프레임 |
| :------------------------: |
|           x = 10           |
|         value = 20         |

| main() 스택 프레임 |
| :----------------: |
|       x = 10       |



**2. x = value; 가 실행된 시점**

| change_value() 스택 프레임 |
| :------------------------: |
|           x = 20           |
|         value = 20         |

| main() 스택 프레임 |
| :----------------: |
|       x = 10       |

**3. change_value() 함수 호출 완료 후 change_value() 스택 프레임 사라짐.**

| main() 스택 프레임 |
| :----------------: |
|       x = 10       |



- 함수 호출로 x 값을 바꾸기 위해서는 call-by-reference로 인자를 전달하면 됨.

---

**call-by-reference(참조에 의한 전달)**

- 인자를 전달할 때 참조를 전달하는 방식.

```c++
#include <iostream>
using namespace std;

void change_value(int *x, int value)  
{
  *x = value;                         
  cout <<"x : " << *x << " in change_value" << endl;
}

int main(void)
{
  int x = 10;                       
  change_value(&x, 20);             
  cout << "x : " << x << " in main" << endl;
  return 0;
}


// 실행결과
x : 20 in change_value
x : 20 in main
```

- call by value코드와 비교했을 때의 차이점.
  - *연산자 추가 : int x -> int *x , x = value; -> *x = value;
  - &연산자 추가 : change_value(x, 20) -> change_value(&x, 20)
- 스택 프레임 측면에서 본 코드

**1. change_value()를 실행하고 *x = value; 가 실행되기 직전**

| change_value() 스택 프레임 |
| :------------------------: |
|      x = 0x1111 1111       |
|         value = 20         |

|              main() 스택 프레임              |
| :------------------------------------------: |
| x = 10               <- address: 0x1111 1111 |

- &x는 main() 스택 프레임의 x가 위치한 메모리 공간의 첫 번째 바이트 주소 값 전달.
- *x는 포인터 변수
  - 포인터 변수는 메모리 주소 데이터를 저장.
  - change_value() 안의  x가 main()의 x의 메모리주소 값을 가리킨다는 의미.
  - **가리킨다는 말 = 참조(reference)**

**2. *x=value; 를 실행한 후**

| change_value() 스택 프레임 |
| :------------------------: |
|      x = 0x1111 1111       |
|         value = 20         |


|              main() 스택 프레임              |
| :------------------------------------------: |
| x = 20               <- address: 0x1111 1111 |


- *x를 역참조(dereference)라고 하며 x에 저장된 주소 값(0x1111 1111)으로 접근.
- value를 대입하여 x 값을 20으로 변경

**3. change_value() 함수 호출 완료 후 change_value() 스택 프레임 사라짐.**

| main() 스택 프레임 |
| :----------------: |
|       x = 20       |



---

**call by assignment(객체 참조에 의한 전달)**

- 파이썬의 함수 호출 방식
- 파이썬에서는 모든 것이 객체이고, 객체에는 2가지 종류가 있음
  - immutable object(변경 불가능 객체) - int, float, str, tuple
  - mutable object(변경 가능 객체) - list, dict, set

**변경 불가능 객체를 전달할 때**

```python
def change_value(x, value):
    x = value
    print("x : {} in change_value".format(x))

if __name__ == "__main__":
    x = 10
    change_value(x, 20)
    print("x : {} in main".format(x))
    
# 실행결과
x : 20 in change_value
x : 10 in main
```

- 스택 프레임 측면에서 본 코드

**1. x = value를 실행하기 전**

| change_value() 스택 프레임 | 메모리 |
| :------------------------: | :----: |
|             x              |   10   |
|           value            |   20   |
|   **main() 스택 프레임**   |        |
|             x              |        |


- **파이썬은 C 언어처럼 변수라는 메모리 공간에 값을 직접 저장하지 않는다**

- 값을 가리킴(reference)
  - main(), change_value()의 x는 메모리의 10을 가리키고
  - change_value()의 value는 메모리의 20을 가리킴

**2. x = value를 실행한 후**

- change_value()의 x가 메모리의 20을 가리킴

- 변수 이름이 가리키는 메모리 공간의 값을 직접 바꾸는게 아니라

  바꾸고자 하는 상수 객체를 참조 하는것.

**3. change_value() 함수 호출 완료 후**

- change_value() 스택 프레임과 메모리에 있던 20이 사라짐.
  - change_value()안의 변수 x, value가 20을 가리키고 있었으나
  - 호출과 함께 사라지면서 메모리에 있던 20도 [레퍼런스 카운트](https://kwonsoonwoo.github.io/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B3%B5%ED%95%99/2018/10/14/cs-with-python-%EB%A0%88%ED%8D%BC%EB%9F%B0%EC%8A%A4-%EC%B9%B4%EC%9A%B4%ED%8A%B8.html)가 0이 되면서 사라짐.



**변경 가능 객체를 전달할 때**

**참조한 리스트에 접근해 변경을 시도**

```python
def func(li):
    # 리스트 li의 0번 인덱스 값을 변경
    li[0] = 'I am your father!'

if __name__ == "__main__":
    li = [1, 2, 3, 4]
    func(li)
    print(li)
    
    
# 실행결과
['I am your father!', 2, 3, 4]
```

- 스택프레임 측면에서 보면
- main()의 스택 프레임과 func() 스택 프레임이 li = [1,2,3,4]를 같이 참조.
- 따라서 li의 0번째 값이 1 -> 'I am your father!'로 바뀜.
- 값을 변경하기 위해 값 객체만 새로운 공간에 만들어 참조하면 됨.



**다른 리스트를 메모리 공간에 새로 만든 다음 이를 참조해 리스트를 변경**

```python
def func(li):
    li = ['I am your father', 2, 3, 4]


if __name__ == "__main__":
    li = [1, 2, 3, 4]
    func(li)
    print(li)
    
    
# 실행결과
[1, 2, 3, 4]
```

- main()스택 프레임은 li = [1, 2, 3, 4]를 참조
- func()스택 프레임은 li = ['I am your father', 2, 3, 4]를 참조
- func()함수 호출이 끝나면 스택 프레임이 사라지면서 참조하던 리스트가 사라짐
- 따라서 [1, 2, 3, 4]가 출력 됨.

---

call by assignment(객체 참조에 의한 전달 방식)를 최종적으로 정리하면 다음과 같다.

- 함수 인자로 변경 불가능 객체를 전달해 값을 변경할 수 없음.

  - 함수 안에서 새 객체를 만들어 참조하여 값을 바꾸려 하면

    함수 호출이 끝나고 스택 프레임이 사라지면서 참조도 사라지기 때문

- 함수 내부에서 객체를 새롭게 할당해야한 값을 변경할수 있는 객체

  - 변경 불가능 객체인 상수, 문자열, 튜플 뿐.

  - 리스트나 딕셔너리 같은 변경 가능 객체도 함수안에서 새로운 객체를 만들면

    함수 호출이 끝나면서 객체는 사라짐

  - 그러므로 인자로 전달된 객체에 접근하여 변경해야만 함수를 호출한 쪽의

    객체를 변경할 수 있음.
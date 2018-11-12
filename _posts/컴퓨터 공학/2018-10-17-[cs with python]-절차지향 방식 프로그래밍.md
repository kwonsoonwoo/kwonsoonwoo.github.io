---
layout: post
title: (Cs with python)-절차지향 방식 프로그래밍
category: 컴퓨터 공학
tags:
  - 컴퓨터 공학
  - 컴퓨터사이언스 부트캠프 with 파이썬
  - 절차지향
---



> [컴퓨터사이언스 부트캠프 with 파이썬](http://www.yes24.com/24/goods/58552941) 책을 공부하며 정리한 포스팅입니다.
>
> 개인 공부후 정리용으로 남기는 포스팅으로 내용상에 오류가 있을수 있습니다.
>
> 예제 코드는 [Computer-Science](https://github.com/KwonSoonWoo/Computer-Science) 를 통해 실습하고 있습니다.

---

[객체지향 방식으로 리팩토링한 코드](https://kwonsoonwoo.github.io/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B3%B5%ED%95%99/2018/10/17/cs-with-python-%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5-%EB%B0%A9%EC%8B%9D-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D,-%EC%BA%90%EC%8B%9C(cache).html)

---



### 개요

#### 작성할 프로그램

- 엑셀에 저장된 학생들의 점수를 가져와 평균과 표준편차를 구하고
- 이를 학년 전체 평균과 비교하여 평가하는 프로그램

---

#### 데이터

- [class_2_3.xlsx](https://github.com/KwonSoonWoo/Computer-Science/blob/master/oop1/oop1_1/class_2_3.xlsx)(2학년 3반 반 성적 파일)
- 상기 파일은 엑셀 형태의 파일.
- 데이터를 저장하거나 불러올때는 openpyxl 모듈을 사용해야 한다.
  - ```pip install openpyxl``` 로 패키지 별도로 설치 필요
- class_2_3.xlsx 파일내용

|  A   |  B  |
| :-----: | :--: |
|  greg   |  95  |
|  john   |  25  |
|  yang   |  50  |
| timothy |  15  |
| melisa  | 100  |
|  thor   |  10  |
|  elen   |  25  |
|  mark   |  80  |
|  steve  |  95  |
|  anna   |  20  |

---

### 코드작성

- [functions.py](https://github.com/KwonSoonWoo/Computer-Science/blob/master/oop1/oop1_1/functions.py)

```python
# openpyxl 모듈 불러오기
import openpyxl
import math

# 학년 전체 학생의 평균: 50점

# get_data_from_excel함수는 인자로 엑셀 파일의 이름을 받는다.
def get_data_from_excel(filename):
    """
    get_data_from_excel -> {'name1': 'score1','name2': 'score2', ...}
    엑셀 파일에서 데이터를 가져옵니다
    반환값은 key가 학생 이름이고 value가 점수인 딕셔너리입니다
    """
    dic = {}
    # openpyxl로 인자로 받는 엑셀 파일을 연다
    wb = openpyxl.load_workbook(filename)
    # 현재 활성화된 sheet를 받아온다
    ws = wb.active
    # rows는 데이터가 있는 모든 행을 발생자 객체로 리턴한다.
    # 발생자에 대한 개념은 아래 부분에 별도 정리
    g = ws.rows

    for name, score in g:
        dic[name.value] = score.value

    return dic


# 평균을 구하는 함수
def average(scores):
    s = 0
    for score in scores:
        s += score
    return round(s/len(scores), 1)

# 분산을 구하는 함수
def variance(scores, avrg):
    s = 0
    for score in scores:
        s += (score - avrg) ** 2
    return round(s/len(scores), 1)

# 표준편차를 구하는 함수
def std_dev(variance):
    return round(math.sqrt(variance), 1)


def evaluateClass(avrg, total_avrg, std_dev, sd):
    """
    evaluateClass(avrg, total_avrg, std_dev, sd) -> None
    avrg: 반 성적 평균
    total_avrg: 학년 전체 성적 평균
    std_dev: 반의 표준편차
    sd: 원하는 표준편차 기준
    """

    if avrg < total_avrg and std_dev > sd:
        print("성적이 너무 저조하고 학생들의 실력 차이가 너무 크다.")
    elif avrg > total_avrg and std_dev > sd:
        print("성적은 평균 이상이지만 학생들의 실력 차이가 크다. 주의 요망!")
    elif avrg < total_avrg and std_dev < sd:
        print("학생들의 실력 차이는 크지 않지만 성적이 너무 저조하다. 주의 요망!")
    elif avrg > total_avrg and std_dev < sd:
        print("성적도 평균 이상이고 학생들의 실력 차이도 크지 않다.")
```

- **발생자(generator)**
  - 반복자(iterator)의 일종으로 next() 함수를 호출할 때마다 데이터를 차례대로 반환.
  - 모든 데이터가 반환되면 Stopiteration 오류가 발생

- 평균, 분산, 표준편차를 구하는 함수 정의를 통해 인터페이스와 구현이 분리됨
  - 즉, 유저 프로그래머가 위의 식을 모른다고 하더라도 해당 함수를 호출해 값을 얻을수 있음.

---

### 메인 프로그램 작성

- [main.py](https://github.com/KwonSoonWoo/Computer-Science/blob/master/oop1/oop1_1/main.py)

```python
from functions import *

# 학년 전체 학생의 평균: 50점

if __name__ == "__main__":
    raw_data = get_data_from_excel('class_2_3.xlsx')    #1
    scores = list(raw_data.values())

    avrg = average(scores)                              #2
    variance = variance(scores, avrg)                   #3
    standard_deviation = std_dev(variance)              #4

    print("평균: {0}, 분산: {1}, 표준편차: {2}".format(
    avrg, variance, standard_deviation
    ))
    evaluateClass(avrg, 50, standard_deviation, 20)     #5
    
    
# 실행결과
# 평균: 51.5, 분산: 1240.2, 표준편차: 35.2
# 성적은 평균 이상이지만 학생들의 실력 차이가 크다. 주의 요망!
```

---

### 결론

- 절차지향의 특징과 장점
  - 함수 이름만 봐도 이 프로그램이 무슨 일을 하는지 쉽게 파악할 수 있음(#1 ~ #5)
  - 다른 프로그래머가 봐도 프로그램의 실행 흐름을 쉽게 파악할 수 있으며
  - 인터페이스만 알면 필요한 함수를 가져다 쓰면 되기 때문에 함수가 어떻게 구현됐는지 알 필요가 없고 다른 프로그램도 쉽게 작성할 수 있음.

---

### Reference

- [초보몽키의 개발공부로그](https://wayhome25.github.io/cs/2017/04/05/cs-05/)


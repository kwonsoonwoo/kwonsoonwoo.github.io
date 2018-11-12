---
layout: post
title: (Cs with python)-객체지향 방식 프로그래밍, 캐시(cache)
category: 컴퓨터 공학
tags:
  - 컴퓨터 공학
  - 컴퓨터사이언스 부트캠프 with 파이썬
  - 객체지향
  - 캐시
  - cache
---



> [컴퓨터사이언스 부트캠프 with 파이썬](http://www.yes24.com/24/goods/58552941) 책을 공부하며 정리한 포스팅입니다.
>
> 개인 공부후 정리용으로 남기는 포스팅으로 내용상에 오류가 있을수 있습니다.
>
> 예제 코드는 [Computer-Science](https://github.com/KwonSoonWoo/Computer-Science) 를 통해 실습하고 있습니다.

---



### 객체지향 방식 프로그래밍

- 절차지향에서 객체지향으로 리펙토링
- [절차지향으로 작성했던 코드](https://kwonsoonwoo.github.io/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B3%B5%ED%95%99/2018/10/17/cs-with-python-%EC%A0%88%EC%B0%A8%EC%A7%80%ED%96%A5-%EB%B0%A9%EC%8B%9D%EC%9C%BC%EB%A1%9C-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8-%EC%9E%91%EC%84%B1%ED%95%98%EA%B8%B0.html)
- [cache](https://ko.wikipedia.org/wiki/%EC%BA%90%EC%8B%9C) 메모리 개념을 활용한다.

---

### 개요

- [class_2_3.xlsx](https://github.com/KwonSoonWoo/Computer-Science/blob/master/oop1/oop1_1/class_2_3.xlsx) : 이름과 점수 데이터를 가진 엑셀 파일
- [statistics.py](https://github.com/KwonSoonWoo/Computer-Science/blob/master/oop1/oop1_3/statistics.py) : 평균, 분산, 표준편차를 연산하는 Stat class를 포함하는 파일
- [datahandler.py](https://github.com/KwonSoonWoo/Computer-Science/blob/master/oop1/oop1_3/datahandler.py) : DataHandler class 를 포함하는 파일
  - evaluator에 Stat 객체를 할당 받아 평균, 분산, 표준편차 연산 함수 공유
  - filename, year_class를 매개변수로 받는다
  - 객체에 연산 결과를 저장해 둘 캐시로 딕셔너리를 사용
  - 학급의 성적을 평가
  - 학급의 종합평가 출력
- [main.py](https://github.com/KwonSoonWoo/Computer-Science/blob/master/oop1/oop1_3/main.py) : DataHandler class에 실제로 매개변수를 넣어서 인스턴스를 생성후 테스트

---

### class_2_3.xlsx

- 이름과 점수 데이터를 가진 엑셀 파일
- 파이썬에서 엑셀 파일을 저장하거나 불러올 때는 openpyxl 모듈을 사용해야 한다.
  - ```pip install openpyxl```로 패키지 별도 설치 필요

|    A    |  B   |
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

### statistics.py

- Stat class를 포함하는 파일
  - def average() 메서드 : 평균
  - def variance() 메서드 : 분산
  - def std_dev() 메서드 : 표준편차

```python
import math


class Stat:
    def average(self, scores):
        s = 0
        for score in scores:
            s += score
        return round(s/len(scores), 1)

    def variance(self, scores, avrg):
        s = 0
        for score in scores:
            s += (score - avrg) ** 2
        return round(s/len(scores), 1)

    def std_dev(self, variance):
        return round(math.sqrt(variance), 1)
```

---

### datahandler.py

- DataHandler class를 포함하는 파일
  - evaluator 멤버변수 : Stat class의 인스턴스
  - get_data_from_excel 클래스 메서드 : filename으로 부터 데이터를 가져와 딕셔너리 형식으로 리턴
  - ```__init__```초기화 함수 : 인스턴스 변수 (rawdata, year_class, cache) 정의
  - get_scores 메서드 : rawdata에서 점수만 가져와서 리스트에 담는다
  - get_average 메서드
    - self.cache 에서 average 키에 해당하는 값을 가져온다. 없으면 클래스 멤버인 evaluator로 평균을 구하고 캐시에 저장한다.
  - get_variance 메서드
    - self.cache 에서 variance 키에 해당하는 값을 가져온다. 없으면 클래스 멤버인 evaluator로 분산을 구하고 캐시에 저장한다.
  - get_standard_deviation 메서드
    - if 문으로 키의 유무를 검사한 다음, 키가 없다면 get_variance 혹은 get_average 메서드를 차례대로 호출하여 연산 결과를 캐시에 쌓은 다음 값을 반환.

```python
from statistics import *
import openpyxl


class DataHandler:
    evaluator = Stat()

    @classmethod
    def get_data_from_excel(cls, filename):
        dic = {}
        wb = openpyxl.load_workbook(filename)
        ws = wb.active
        g = ws.rows

        for name, score in g:
            dic[name.value] = score.value


        return dic

    def __init__(self, filename, year_class):
        self.rawdata = DataHandler.get_data_from_excel(filename)
        self.year_class = year_class
        # 연산한 값을 저장해 두는 저장소
        # 필요할 때 연산하되
        # 이미 연산된 값이면 연산 없이 저장된 값을 반환
        self.cache = {}

    def get_scores(self):
        if 'scores' not in self.cache:
            self.cache['scores'] = list(self.rawdata.values())

        return self.cache.get('scores')

    def get_average(self):
        if 'average' not in self.cache:
            self.cache['average'] = self.evaluator.average(self.get_scores())

        return self.cache.get('average')

    def get_variance(self):
        if "variance" not in self.cache:
            self.cache["variance"] = self.evaluator.variance(self.get_scores(), self.get_average())


        return self.cache.get("variance")

    def get_standard_deviation(self):
        if "standard_deviation" not in self.cache:
            self.cache["standard_deviation"] = self.evaluator.std_dev(self.get_variance())

        return self.cache.get("standard_deviation")

    def evaluate_class(self, total_avrg, sd):
        avrg = self.get_average()
        std_dev = self.get_standard_deviation()


        if avrg <total_avrg and std_dev >sd:
            print("성적이 너무 저조하고 학생들의 실력 차이가 너무 크다")
        elif avrg > total_avrg and std_dev >sd:
            print("성적은 평균 이상이지만 학생들의 실력 차이가 크다. 주의 요망!")
        elif avrg < total_avrg and std_dev <sd:
            print("학생들의 실력 차이는 크지 않지만 성적이 너무 저조하다. 주의 요망!")
        elif avrg > total_avrg and std_dev <sd:
            print("성적도 평균 이상이고 학생들의 실력 차이도 크지 않다.")

    def get_evaluation(self, total_avrg, sd = 20):
        print('*' * 50)
        print('{}반 성적 분석 결과'.format(self.year_class))
        print(
        "{0}반의 평균은 {1}점이고 분산은 {2}이며 따라서 표준편차는 {3}이다.".format(
            self.year_class,
            self.get_average(),
            self.get_variance(),
            self.get_standard_deviation()))
        print('*' * 50)
        print('{}반 종합 평가'.format(self.year_class))
        print('*' * 50)
        self.evaluate_class(total_avrg, sd)
```

---

### main.py

```python
from datahandler import *

# 전체 학년 평균: 50점
dh = DataHandler('class_2_3.xlsx', '2-3')
dh.get_evaluation(50)

# 실행결과
"""
**************************************************
2-3반 성적 분석 결과
2-3반의 평균은 51.5점이고 분산은 1240.2이며 따라서 표준편차는 35.2이다.
**************************************************
2-3반 종합 평가
**************************************************
성적은 평균 이상이지만 학생들의 실력 차이가 크다. 주의 요망!
"""
```

---

### 캐시(cache)

- 컴퓨터 시스템의 성능을 향상시키기 위해 주로 CPU 칩 안에 포함되는 빠르고 작고 비싼 메모리이다. 프로그램에서 직접적으로 읽거나 쓸 수 없고 하드웨어의 메모리 관리 시스템이 내부적으로 제어한다. 대부분 프로그램은 한 번 사용한 데이터를 다시 사용할 가능성이 높고, 그 주변의 데이터도 곧 사용할 가능성이 높은 데이터 지역성을 가지고 있다. 데이터 지역성을 활용하여 캐시보다는 느리지만 용량이 큰 메인 메모리에 있는 데이터를 캐시 메모리에 불러와 두고, CPU가 필요한 데이터를 캐시에서 먼저 찾도록 하면 시스템 성능을 향상시킬 수 있다.
- 캐시 메모리는 데이터 지역성(Locality)의 원리를 사용한다. 데이터 지역성은 대표적으로 시간 지역성(Temporal locality)과 공간 지역성(Spatial Locality)으로 나뉘는데, 시간 지역성이란 for나 while 같은 반복문에 사용하는 조건 변수처럼 한 번 참조된 데이터는 잠시 후에 또 참조될 가능성이 높다는 것이고, 공간 지역성이란 A[0], A[1]과 같은 데이터 배열에 연속으로 접근할 때 참조된 데이터 근처에 있는 데이터가 잠시 후에 사용될 가능성이 높다는 것이다.
- 쉽게 예를 들자면 무지하게 지랄맞고 부지런한 상사가 2010년 재무결산 보고서를 가져오라고 했을 때, 무슨 일인지는 몰라도 또 가져오라고 할지도 모르니까 2010년 재무결산보고서를 일단 준비해 놓고, 2009년이나 2011년, 2012년 재무결산보고서도 가져오라고 할지 모르니까 그것도 준비해 놓는 식이다. 또 다른 예로는 캐시는 지갑이라고 생각하면 된다. 지갑 혹은 주머니가 없다면 우리가 현금이 필요할 때마다 매번 은행이나 ATM에 가야 할 것이다. 이는 당연히 매우 귀찮고 시간도 많이 걸린다. 하지만 우리가 현금을 지갑에 넣고 다님으로써 시간을 절약할 수 있다.
- CPU가 데이터를 요청했을 때 캐시 메모리가 해당 데이터를 가지고 있다면 이를 캐시 히트라 부르고, 해당 데이터가 없어서 DRAM에서 가져와야 한다면 캐시 미스라 부른다. 캐시 미스 발생시의 처리 방법은 캐시 정책에 따라 다르며, 데이터를 읽어 오는 시점으로 사용하기도 한다.

---

### Reference

- [초보몽키의 개발공부로그](https://wayhome25.github.io/cs/2017/04/11/cs-12/)
- [캐시(cache) 메모리](https://namu.wiki/w/%EC%BA%90%EC%8B%9C%20%EB%A9%94%EB%AA%A8%EB%A6%AC)
---
layout: post
title: Python 딕셔너리, 셋
category: Python
---



## 딕셔너리(dictionary)

Key-Value형태로 항목을 가지는 자료구조.

**딕셔너리 생성**

```python
>>> empty_dict1 = {}
>>> empty_dict2 = dict()
>>> champion_dict = {
... 'Lux': 'the Lady of Luminosity',
... 'Ahri': 'the Nine-Tailed Fox',
... 'Ezreal': 'the Prodigal Explorer',
... 'Teemo': 'the Swift Scout',
... }
```

**형변환**

**dict** 함수를 사용, 두 값의 시퀀스(리스트 또는 튜플)을 딕셔너리로 변환 한다.

```python
>>> sample = [[1,2], [3,4], [5,6]]
>>> dict(sample)
{1: 2, 3: 4, 5: 6}
```

**항목 찾기/추가/변경 [key]**

```
>>> champion_dict['Lux']
'the Lady of Luminosity'
>>> champion_dict['Sona'] = 'Maven of the Strings'
>>> champion_dict['Lux'] = 'Demacia'
```

**결합 (update)**

```
>>> item_dict = {
... 'Doran\'s Ring': 400,
... 'Doran\'s Blade': 450,
... 'Doran\'s Shield': 450,
... }
>>> com_dict = {}
>>> com_dict.update(champion_dict)
>>> com_dict.update(item_dict)
>>> com_dict
```

서로 같은 키가 있을 경우, update에 주어진 딕셔너리의 값이 할당된다.

**삭제(del)**

```
>>> del com_dict['Doran\'s Blade']
>>> del com_dict['Doran\'s Ring']
>>> del com_dict['Doran\'s Shield']
```

#### 전체 삭제 (clear)

전체 항목을 삭제

#### in으로 키 검색

True/False를 반환한다.

#### 키 또는 값 얻기

**keys()**
모든 키 얻기

**values()**
모든 값 얻기

**items()**
모든 키-값 얻기 (튜플로 반환)

#### 복사

**copy()**



## 셋(Set)

셋은 키만 있는 딕셔너리와 같으며, 중복된 값이 존재할 수 없다.

**셋 생성**

```python
>>> empty_list = set()
>>> champions = {'lux', 'ahrl', 'ezreal'}
```

**형변환**

문자열, 리스트, 튜플, 딕셔너리를 셋으로 변환할 수 있으며, 중복된 값이 사라진다.

```
>>> set('ezreal')
{'e', 'z', 'a', 'l', 'r'}

>>> set(champion_dict)
{'Ahri', 'Lux', 'Ezreal', 'Sona', 'Teemo'}
```

딕셔너리는 키만 남는다.



#### 집합 연산

| 연산자 | 설명                        |
| ------ | --------------------------- |
| \|     | 합집합(Union)               |
| &      | 교집합(Intersection)        |
| \-     | 차집합(Difference)          |
| ^      | 대칭차집합(Exclusive)       |
| <=     | 부분집합(Subset)            |
| <      | 진부분집합(Proper subset)   |
| \>=    | 상위집합(Superset)          |
| \>     | 진상위집합(Proper superset) |

```
>>> A = {1,2,3,4,5}
>>> B = {4,5,6,7,8,9}
>>> C = {4,5,6}
>>> A|B
>>> A&B
>>> A-B
>>> B-A
>>> A^B
>>> A <= B
>>> C <= B
>>> C < B
>>> B <= B
>>> B < B
```



## 실습

- `apple`은 `사과`, `banana`는 `바나나`, `cherry`는 `체리`의 key-value를 갖는 `fruits`라는 이름의 사전을 만든다.

- `fruits`를 `Set`으로 만들어 `fruits_set`변수에 할당한다.

- `fruits_set`에 `durian`이 존재하는지 확인한다.

- `fruits`사전에서 `apple`키에 해당하는 값을 출력한다.
- `girlgroups`라는 이름의 2차원 사전을 만들고 출력해본다
  - 최상위 키는 `girlsday`와 `redvelvet`이 있으며, 각각 자식으로 사전을 갖는다.
  - `girlsday`키의 자식사전에는 `korean`과 `members`키가 있으며, 각각 `'걸스데이'`라는 문자열과 `['민아', '혜리', '소진', '유라']`라는 리스트를 갖는다.
  - `redvelvet`키의 자식사전에도 `korean`과 `members`키가 있으며, 각각 `'레드벨벳'`이라는 문자열과 `['아이린', '슬기', '웬디', '조이', '예리']`라는 리스트를 갖는다.

- `girlgroups`사전의 최상위 키 목록을 출력해본다.

- `girlgroups['girlsday']`의 모든 키를 출력해본다.

- `girlgroups['redvelvet']`의 모든 값을 출력해본다.

- ```x = {1,2,3,4,5,6,8}```, ```y={4,5,6,9,10,11}```, ```z={4,6,8,9,7,10,12}```일 때,

  - x,y,z의 교집합에 해당하는 숫자는?
  - y,z의 교집합이며 x에는 속하지 않는 숫자는?
  - x에만 속하고 y,z에는 속하지 않는 숫자는?

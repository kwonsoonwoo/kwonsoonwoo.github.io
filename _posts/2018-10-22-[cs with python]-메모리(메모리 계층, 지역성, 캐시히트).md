---
layout: post
title: (Cs with python)-메모리(메모리 계층, 지역성, 캐시히트)
category: 컴퓨터 공학
tags:
  - 컴퓨터 공학
  - 컴퓨터사이언스 부트캠프 with 파이썬
  - 메모리
  - 메모리 계층구조
  - memory hierarchy
  - 지역성
  - 캐시히트
  - locality
  - Cache hit
---



> [컴퓨터사이언스 부트캠프 with 파이썬](http://www.yes24.com/24/goods/58552941) 책을 공부하며 정리한 포스팅입니다.
>
> 개인 공부후 정리용으로 남기는 포스팅으로 내용상에 오류가 있을수 있습니다.
>
> 예제 코드는 [Computer-Science](https://github.com/KwonSoonWoo/Computer-Science) 를 통해 실습하고 있습니다.

---

### 핵심개념

- 메모리 계층구조(memory hierarchy)
- 지역성(locality)
- 캐시히트(cache hit)

---

### 메모리 계층

![메모리계층구조](/assets/memory/memory1.png)

- 메모리의 종류가 다양한 이유는 속도와 비용.
- 이러한 이유로 적정한 가격과 하드웨어 구현 등 여러가지 요소를 종합하여 위와 같은 **메모리 계층 구조(memory hierarchy)**가 완성됨.
  - 위로 올라갈수록 **속도는 빨라지지만 용량은 작아짐**
  - 반대로, 아래로 내려올수록 **속도는 느려지지만 용량은 커짐**
- 전달되는 데이터가 아래쪽에 있을 경우 CPU에 도달하려면 위에 있는 모든 계층을 거쳐야 한다는 특징이 있다.
- 위에 있는 계층을 모두 거칠 경우 속도가 느릴것 같지만 **지역성(locality)**때문에 실제로는 느려지지 않는다.
- 오늘날의 [캐시](https://kwonsoonwoo.github.io/%EC%BB%B4%ED%93%A8%ED%84%B0%20%EA%B3%B5%ED%95%99/2018/10/17/cs-with-python-%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5-%EB%B0%A9%EC%8B%9D-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D,-%EC%BA%90%EC%8B%9C(cache).html)는 CPU 안에 들어 있고 L1, L2, L3 캐시 등이 있다.
  - 숫자가 작을수록 속도는 빠르고 용량은 작음

---

### 지역성(Principal of locality)

- 데이터 접근이 같은 메모리 공간이나 인접한 메모리 공간에서 자주 일어난다는 의미
- **시간적 지역성(temporal locality)**
  - 특정 데이터에 한 번 접근했을 때 곧 다시 그 데이터에 접근할 가능성이 높다
- **공간적 지역성(spatial region)**
  - 이번에 접근할 데이터는 이전에 접근했던 데이터의 근처에 있을 확률이 높다

---

### 지역성 코드예시

```python
>>> li = [1, 2, 3, 4, 5]
>>> res = 0
	# e는 공간적 지역성
>>> for e in li:
    	# res는 시간적 지역성
        res += e
```

- res 변수는 리스트의 모든 요소를 가져와 더할 때마다 데이터에 접근한다
  - 시간적 지역성
- for 문의 e는 리스트를 순회하면서 매번 바로 옆의 데이터를 가져온다
  - 공간적 지역성

---

### 캐시 히트(Cache hit)

- CPU가 요청한 데이터를 메인 메모리에서 가져오지 않고 캐시에서 가져오는 것
  - 캐시에 없어서 메인 메모리에서 가져와야 하면 **캐시 미스(cache miss)**
- 캐시 히트나 캐시 미스가 가능한 이유
  - CPU가 데이터를 요청하면 그 데이터와 함께 인접 데이터로 이루어진 메모리 블록을 캐시로 가져옴
  - 요청 데이터 + 인접 데이터로 이루어진 메모리 블록 => **캐시 행(cache line)**
  - 그 다음, 캐시에서 해당 데이터만 레지스터로 전송
  - 그 다음 CPU가 데이터를 요청하면 우선적으로 캐시에 요청한 데이터가 있는지 확인

---

### Reference

> [위키백과-메모리 계층 구조](https://ko.wikipedia.org/wiki/%EB%A9%94%EB%AA%A8%EB%A6%AC_%EA%B3%84%EC%B8%B5_%EA%B5%AC%EC%A1%B0)


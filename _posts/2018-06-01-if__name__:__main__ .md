---
layout: post
title: if __name__=='__main__'
category: Python
---



해당 포스트는 아래 블로그를 참조했습니다.

> [땅뚱 창고](http://pinocc.tistory.com/175)


```python
# 만약 이 파일이 인터프리터에 의해서 실행되는 경우라면 이라는 의미.
if __name__=='__main__'
```

**본인이 구현한 코드는 다음과 같이 실행될수 있음.**

- 다른 파이썬 코드에 의해 모듈로 import 될 경우.
- 파이썬 인터프리터에 의해 직접 실행될 경우



**위 코드는 2번째 경우에만 실행하도록 하고 싶은 코드 블럭이 있는 경우에 사용한다.**



아래 예제 코드와 결과를 보면 이해하기 쉽다.

(참고: <http://ibiblio.org/g2swap/byteofpython/read/module-name.html>)



**CODE**

```python
#!/usr/bin/python
# Filename: using_name.py

if __name__ == '__main__':
	print 'This program is being run by itself'
else:
	print 'I am being imported from another module'
```



**OUTPUT**

```python
$ python using_name.py 
This program is being run by itself 
$ python >>> import using_name 
I am being imported from another module 
>>>
```


















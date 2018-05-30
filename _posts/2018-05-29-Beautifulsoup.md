---
layout: post
title: Beautifulsoup
category: Python
---



## Beautifulsoup

```
html_doc = """
<html><head><title>The Dormouse's story</title></head>
<body>
<p class="title"><b>The Dormouse's story</b></p>

<p class="story">Once upon a time there were three little sisters; and their names were
<a href="http://example.com/elsie" class="sister" id="link1">Elsie</a>,
<a href="http://example.com/lacie" class="sister" id="link2">Lacie</a> and
<a href="http://example.com/tillie" class="sister" id="link3">Tillie</a>;
and they lived at the bottom of a well.</p>

<p class="story">...</p>
"""
```



```
설치 과정
1. pip list 입력
2. pip install beautifulsoup4 lxml 입력
3. from bs4 import BeautifulSoup
   soup = BeautifulSoup(html_doc, 'lxml')
  
print(html_doc)			# 입력한 그대로 나옴.
print(soup.prettify())   # 자동으로 닫는 태그 생성
     					  태그들이 어떤 클래스의 인스턴스 형태. 
print(soup.title)
# <title>The Dormouse's story</title>

print(soup.title.name)
# u'title'

print(soup.title.string)
# u'The Dormouse's story'

print(soup.title.parent.name)
# u'head'

print(soup.p)
# <p class="title"><b>The Dormouse's story</b></p>

print(soup.p['class'])
# u'title'

print(soup.a)
# <a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>

print(soup.find_all('a'))
# [<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
#  <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>,
#  <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]

print(soup.find(id="link3"))
# <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>
```

> 참고사이트 : [Beautiful Soup Documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/#quick-start)
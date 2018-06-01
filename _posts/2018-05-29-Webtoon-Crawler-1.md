---
layout: post
title: Webtoon Crawler-1
category: Python
---





## Webtoon Crawler - 1

예제에 나와있는 표현을 이해하지 못해서 멘탈 바사삭.

해당 문장이 정확히 어떤 의미인지를 알아야 코드 적용이 가능하기 때문에

최대한 내가 이해할수 있는 정도로 풀어서 정리.

(내 생각은 ##으로 표시.)



- **예제**

```
# 1. HTML받아와서 html변수에 문자열을 할당
#   1-1. 만약 'data/episode_list.html'이 없다면
#   -> 내장모듈 os의 'exists'함수를 사용해본다
#   -> 파이썬 공식문서 확인
# http://comic.naver.com/webtoon/list.nhn?titleId=703845&weekday=wed
# 죽음에 관하여 (재) 페이지를
# requests를 사용해서 data/episode_list.html에 저장
#   list.nhn뒤 ?부터는 url에 넣지 말고 GET parameters로 처리
#   -> requests문서의 'Passing Parameters In URLs'
# 저장 후에는 파일을 불러와 html변수에 할당
# 1-2. 이미 'data/episode_list.html'이 있다면
#   html변수에 파일을 불러와 할당
```

```python
import os
import requests

# html을 받아온다는 의미인듯 함
file_path = 'data/episode_list.html'

# HTTP 요청을 보낼주소
## 아래 else문에 HTTP GET요청할때 .get()부분에 들어가는것
url_episode_list = 'http://comic.naver.com/webtoon/list.nhn'
params = {
    'titleId': 703845,
}

# HTML파일이 로컬에 저장되어 있는지 검사시작
# HTML파일이 저장되어 있다면
if os.path.exists(file_path):
    # 저장되어 있다면, 해당 파일을 읽어서 html변수에 할당
    ## 해당 파일을 읽어서 -> open(file_path, 'rt').read()
    ## html 변수에 할당 -> (html = ~~~)
	html = open(file_path, 'rt').read()
# HTML파일이 저장되어 있지 않다면
else:
    # requests를 사용해 HTTP GET요청
    ## 객체(코드 문맥에서 벗어나지 않게 마음대로 설정) = requests.get(url주소)
	response = requests.get(url_episode_list, params)
	# 요청 응답객체의 text속성값을 html변수에 할당
    ## 요청 응답객체 -> response(꼭 이 이름이 아니어도 됨)
    ## text속성값 -> 객체.text
    html = response.text
    # 받은 텍스트 데이터를 HTML 파일로 저장
	open(file_path, 'wt').write(html)
```

> [os.path.exists 함수 관련 참조](https://docs.python.org/3/library/os.path.html) ->  ctrl + f -> exists
>
> [params 참조](http://docs.python-requests.org/en/master/user/quickstart/#passing-parameters-in-urls) -> Passing Parameters In URLs





```
# 2. 제목, 저자, 웹툰정보 탐색하기
#  html변수를 사용해 soup변수에 BeautifulSoup객체를 생성
# soup객체에서
#   - 제목: 죽음에 관하여 (재)
#   - 작가: 시니/혀노
#   - 설명: 삶과 죽음의 경계선, 그 곳엔 누가 있을까.
# 의 내용을 가져와 title, author, description변수에 할당
```

```python
# BeautifulSoup클래스형 객체 생성 및 soup변수에 할당
## soup변수->soup
## 할당 -> "="
## BeautifulSoup(html, 'lxml') -> BeautifulSoup클래스형 객체 생성
soup = BeautifulSoup(html, 'lxml')

# div.detail > h2 (제목, 작가)의
#   0번째 자식: 제목 텍스트
#   1번째 자식: 작가정보 span Tag
#   Tag로 부터 문자열을 가져올때는 get_text()
## select_one은 해당 선택자에 대해서 한개만 가져온다.
h2_title = soup.select_one('div.detail > h2')

#   0번째 자식: 제목 텍스트
## 제목이니까 변수 이름을 title로
## .은 CSS에서 클래스 선택자를 의미함
## .contents는 해당 태그의 컨텐츠 목록을 출력한다.
## .strip()은 문자열의 처음과 끝에서 ()안에 있는 글자만 출력시킴.
##	이를테면 \n, \t와 같은 글자들은 없어진다고 생각하면 됨.(태그 없는 글자에 쓸것)
title = h2_title.contents[0].strip()
#   1번째 자식: 작가정보 span Tag
## strip=True 란 문자의 양쪽 공백을 다 없애주는거.
## .get_text() -> 문서나 태그의 텍스트 부분만 원할경우(태그 있는 글자에 쓸것)
author = h2_title.contents[1].get_text(strip=True)
# div.detail > p (설명)
#   Tag로 부터 문자열을 가져올때는 get_text()
## div.detail > p -> div클래스의 detail의 자식 요소인 p
description = soup.select_one('div.detail > p').get_text(strip=True)

print(title)
print(author)
print(description)
```

> CSS selector에 대해서 이해필수 -> 수업시간에 받은 pdf 파일 활용 or 구글링
>
> 크롤링하려는 페이지에서 개발자 도구를 켜서 해당 태그의 클래스 명 등을 확인해야 한다.




```
# 3. 에피소드 정보 목록을 가져오기
#   url_thumbnail:  썸네일 URL
#   title:          제목
#   rating:         별점
#   created_date:   등록일
#   no:             에피소드 상세페이지의 고유 번호
#    각 에피소드들은 하나의 dict데이터
#    모든 에피소드들을 list에 넣는다
```

```python
# 에피소드 목록을 담고 있는 table
## 크롤링 하려는게
table = soup.select_one('table.viewList')
print(table)
# table내의 모든 tr요소 목록
## table'.'(클래스)
## select('tr') -> <tr> 내용 </tr> 이런식으로 되어있는 내용 전체 출력. / 리스트 값으로 반환하기 때문에 list 변수 할당
tr_list = table.select('tr')

# 첫 번째 tr은 thead의 tr이므로 제외, tr_list의 [1:] 부터 순회
## enumerate -> 반복되는 구간에서 객체가 어느 위치에 있는지 알려주는 인덱스 값이 필요할때 사용
## 이번 경우 table.select('tr')로 잘 출력되는지 구분하기가 힘들어서 아래처럼 for 문을 돌림
for index, tr in enumerate(tr_list[1:]):
	# 에피소드에 해당하는 tr은 클래스가 없으므로,
	# 현재 순회중인 tr요소가 클래스 속성값을 가진다면 continue
    ## 만약 tr요소중에 class가 있다면 continue
    ## continue는 반복문의 나머지 부분을 안보고 반복문의 처음으로 돌아감
    ## 지금은 제외하는 경우를 첫번째에 처리함.
	if tr.get('class'):
		continue

	# 현재 tr의 첫 번째 td요소의 하위 img태그의 'src'속성값
    ## tr이 가지고 있는 td가 가지고 있는 nth-of-type의 첫번째거가 가지고 있는 img태그의 src속성
	url_thumbnail = tr.select_one('td:nth-of-type(1) img').get('src')
    # 현재 tr의 첫 번째 td요소의 자식 a 태그에 'href'속성값
    ### url을 주소와 + params 형태로 만드는것 -> 아래 사이트 참조
	url_detail = tr.select_one('td:nth-of-type(1) > a').get('href')
	# 현재 tr의 두 번째 td요소의 자식 a요소의 내용
	title = tr.select one('td:nth-of-type(2) > a').get_text(strip=True)
	# 현재 tr의 세 번째 td요소의 하위 strong태그의 내용
    ## 하위 선택자는 띄어쓰기로 함.
	rating = tr.select_one('td:nth-of-type(3) strong').get_text(strip=True)
	# 현재 tr의 네 번째 td요소의 내용
	created_date = tr.select_one('td:nth-of-type(4)').get_text(strip=True)
    ### url_detail을 먼저 할당
    ### parse.urlsplit(url_detail) -> SplitResult 목록 출력
    ### .query -> 그 중 query 속성출력
	query_string = parse.urlsplit(url_detail).query
    ### query_string을 파싱해줘 -> 딕셔너리 형태로 출력됨
	query_dict = parse.parse_qs(query_string)
    ### 단순 query_dict['no']로 하면 딕셔너리 형태로 출력됨
    ### 따라서 [0]을 통해 딕셔너리 형태를 없애주기 위해 0번째 값을 꺼내줌.
	no = query_dict['no'][0]

	print(url_thumbnail)
	print(title)
	print(rating)
	print(created_date)
	print(no)
```

> [url을 주소 + params 형태로 만드는법](https://stackoverflow.com/questions/21584545/url-query-parameters-to-dict-python)
>
>



**로드하지 않은 모듈을 임포트시**

- Pycharm에서 해당 명령어에 빨간줄 -> Alt + Enter -> 임포트할 모듈 선택



**타이핑을 입력하다가 오타가 날수 있으니 되도록 이면 자동완성 기능 사용할것.**

**한번에 코드를 짤순 없다! 그러니까 print를 자주 써서 제대로 내용을 작성하는지 수시로 확인할것.**

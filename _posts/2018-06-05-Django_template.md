---
layout: post
title: Django template 확장 및 CSRF
category: Django
---



**전반적인 흐름 리뷰**

---




```
Django
-> urls(root) -> view function -> HttpResponse
			   DB	(Model)
			   HTML	(Template)
				Static file link (STATICFILES_DIRS)

view function
	 요청을 DB, Template과 연동해서 처리



models.py
	DB구조 설계
	DB접근할 수 있도록 도와줌 (ORM)


templates/*.html
	특정 정보가 들어왔을 때, 사용자에게 보여줄 내용을 정의



MVC모델
	Model 		: 데이터
	View		: 사용자에게 표시되는 영역 	
	Controller	: 데이터를 사용해 사용자에게 돌려줄 내용을 처리


MTV모델
	Model
	Template
	View

MVC 와 MTV 모델은 정확히 일치하지만 View가 다른 역할을 한다는데 포커스
```

> [MVC모델](https://ko.wikipedia.org/wiki/%EB%AA%A8%EB%8D%B8-%EB%B7%B0-%EC%BB%A8%ED%8A%B8%EB%A1%A4%EB%9F%AC)



```linebreaksbr``` -> html쪽에서 알아서 엔터치는 효과.



- **template 확장기능**
  - **같이 사용하지 않는 부분만 block처럼 만드는것. **


```
1. html 들의 공통된 내용만 base.html 에 남겨놓음.

2. 각 html 파일에 공통된 내용은 다 제거 하고 내용을 입력해야 되는 부분은 아래와 같이 작성
{% block content %}
'html 내용'
{% endblock %}
```

추상화 : 내부적인 동작이 감춰진것.





**CSRF**

---

```
CSRF

은행
    송금하기 (bank.com/send/)
        form POST method
            금액
            상대계좌
            유저ID
            form에 비밀값 (매번 새로생성)

        -> 유저 상대에게 금액을 보냄


은행 피싱사이트 (bbank.com)
    송금하기
        form POST method -> (bank.com)
            금액    //999999999999
            상대계좌 //hacker
            유저ID






request -> (middleware) -> view -> response
```

> CSRF 관련문서
> https://ko.wikipedia.org/wiki/ 사이트 간 요청 위조
> https://namu.wiki/w/CSRF
> https://docs.djangoproject.com/en/2.0/ref/csrf/
>
> Django공식문서 - CSRF (How it works)
> https://docs.djangoproject.com/en/2.0/ref/csrf/#how-it-works

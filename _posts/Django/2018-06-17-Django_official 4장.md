---
layout: post
title: Django tutorial 4장
category: Django
tags:
  - Django
---



Django tutorial과 stop-out 과제를 하다보니 어떤 타이밍에 어떤 모듈에서 실행하는 순서인지를 파악하는게

중요하다고 느껴져서 Django tutorial강의를 들으며 전반적인 순서를 정리해보고자 한다.



#### 1. 간단한 폼 만들기

- polls/templates/polls/detail.html

  ```django
  {% raw %}
  <h1>{{ question.question_text }}</h1>
  
  {% if error_message %}
  <p><strong>{{ error_message }}</strong></p>
  {% endif %}
  
  <form action="" method="post">
      <!-- POST방식 요청이므로 csrf_token추가-->
      {% csrf_token %}
      
      <!--
      여기가 Question detail페이지이며, question키에 해당하는 Question인스턴스가 할당되어 있음
      현재 Question에 속하는 Choice목록은 question.choice_set.all로 QuerySet을 얻어낼 수 잇으며,
      for구문으로 QuerySet을 순회한다
      -->
      {% for choice in question.choice_set.all %}
      <!--
          각 Loop (매 Loop의 아이템: Choice인스턴스)
          마다 radio input과 label을 만들어줌
      -->
      <input type="radio" name="choice" id="choice{{ forloop.counter }}" value="{{ choice.id }}">
      <label for="choice{{ forloop.counter }}">{{ choice.choice_text }}</label><br>
      {% endfor %}
      
      <!-- 전송버튼 -->
      <button type="submit">Vote</button>
  </form>
  {% endif %}
  {% endraw %}
  ```

- admin페이지로 가서 choice를 더 만들기

  - POLLS의 choices 항목에 +Add를 선택하여 질문을 선택하고 choice목록을 추가

- polls페이지를 보면 선택한 항목들이 추가된걸 확인할수 있음

- 이 폼에서 key와 value => name , value

- html에서 폼으로 보낼 데이터를 담는 요소 = input



- detail.html 내용 추가

  ```django
  {% raw %}
  <form action="{% url 'polls:vote' question_id=question.id %}">
  {% endraw %}
  ```

- polls/views.py 수정

  ```python
  def vote(request, question_id):
      ## 터미널 상에서 프린트
      print('request.GET:', request.GET)
      print('request.POST:', request.POST)
  
      # 선택한 Choice의 choice_text와 id값을 갖는 문자열 생성
      # 해당 문자열을 HttpResponse로 전달
      # ex) question_text: 걸스데이 멤버중...., choice_text: 민아, id: 4
      
      ## request.POST dict의 choice키의 value를 뽑음
      choice_id = request.POST['choice']
      question = Question.objects.get(id=question_id)
      choice = Choice.objects.get(id=choice_id)
  
      question_text = question.question_text
      choice_text = choice.choice_text
  
      result = 'question_text: {}, choice_text: {}, choice.id: {}'.format(
          question_text,
          choice_text,
          choice_id,
      )
  
      return HttpResponse(result)
  ```

- 이렇게 되면 페이지에서 question_text와 choice_text, choice_id가 출력됨.



- polls/views.py 한번 더 수정

  ```python
  def vote(request, question_id):
      print('request.GET:', request.GET)
      print('request.POST:', request.POST)
  
      # 선택한 Choice의 choice_text와 id값을 갖는 문자열 생성
      # 해당 문자열을 HttpResponse로 전달
      # ex)
      # question_text: 걸스데이 멤버중....,
      # choice_text: 민아
      # choice.id: 4
      # 현재 Choice의 votes: 5
  
      choice_id = request.POST['choice']
      question = Question.objects.get(id=question_id)
      choice = Choice.objects.get(id=choice_id)
  
      # choice의 votes값을 증가시키고 DB에 저장하기
      choice.votes += 1
      choice.save()
  
      question_text = question.question_text
      choice_text = choice.choice_text
      choice_votes = choice.votes
  
      result = (
          'question_text: {}\n'
          'choice_text: {}\n'
          'choice.id: {}\n'
          'choice.votes: {}').format(
          question_text,
          choice_text,
          choice_id,
          choice_votes,
      )
  
      return HttpResponse(result)
  ```

- 이렇게 하면 DB browser로 확인했을때 선택한 값이 저장되어 1씩 올라가게 된다.

---



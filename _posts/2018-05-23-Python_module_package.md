---
layout: post
title: 모듈과 패키지
category: Python
---



# 모듈과 패키지

## 실습

1. 위 프로그램에 `friends`패키지를 만들고, `send_message`함수를 가진 `chat`모듈을 추가한다.
   `send_message`는 `input`을 이용해 2개의 인자를 받으며(친구명, 메세지), 실행 시 `print`함수를 통해 메세지를 보냈다는 문구를 출력한다.

2. 프로그램을 실행했을 때, `3`을 입력하면 `send_message`함수를 실행하도록 한다.

   ```python
   (fc-python) ➜  module git:(master) ✗ cd functions
   (fc-python) ➜  functions git:(master) ✗ vi chat.py

   def send_message():
   	a = input('친구명을 입력해주세요: ')
   	b = input('메세지를 입력해주세요: ')
   	print(f'{a}에게 {b}를 보냈습니다!')

   if __name__=='__main__':
   	send_message()

   (fc-python) ➜  functions git:(master) ✗ ..
   (fc-python) ➜  module git:(master) ✗ vi lol.py

   #import game
   from functions.game import *
   from functions.shop import show_info as shop_info
   from functions import shop
   from functions import chat

   shop_info()

   def turn_on():
       print('=Turn on game =')

       while True:
           choice = input('뭐할래?\n 1: 상점가기\n 2: 게임시작하기\n 3: 메시지보내기\n 0: 종료\n 입력:')
           if choice == '1':
               shop.buy_item()
           elif choice == '2':
               play_game()
           elif choice == '3':
               chat.send_message()

           elif choice == '0':
               break
           else:
               print('1, 2, 3, 0중 하나를 입력해주세요')

   if __name__ == '__main__':
       turn_on()


   ```

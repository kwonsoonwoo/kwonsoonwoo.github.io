---
layout: post
title: 클래스 실습
category: Python
tags:
  - Python
---



도서 관리 프로그램
    Library, Book, User클래스 구현
        프로그램 시작시 도서 5권 정도를 가진 상태로 시작

    Library
        attrs
            name: 도서관명
            book_list: 도서 목록 (Book인스턴스의 목록)
        methods
            add_book
            remove_book
        property
            info: 가지고 있는 도서 목록을 보기좋은 텍스트로 출력 (빌려간 도서는 출력 안해도 됨)
    
    Book
        attrs
            title: 제목
            location: 현재 자신이 어떤 Library 또는 User에게 있는지를 출력
        property
            is_borrowed: 대출되었는지 (location이 User인지 Library인지 확인)
    
    User
        attrs
            name: 이름
            book_list: 가지고 있는 도서 목록
        methods
            borrow_book(library, book_name): library로부터 book을 가져옴
            return_book(library, book_name): library에 book을 다시 건네줌


> [코드](https://github.com/KwonSoonWoo/python/blob/master/2018-05-26~27.%20%EC%88%99%EC%A0%9C.ipynb)

---
title: "[python] 파이썬 상속(inheritance) 개념" 
categories:
  - programming
tags:
  - programming
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 파이썬 상속(inheritance) 개념

본 포스팅은 [코딩도장](https://dojang.io/mod/page/view.php?id=2384)을 참고하였습니다. 

## 상속 정의 

* 부모클래스(parent class), 슈퍼클래스(super class)
* 자식클래스(child class), 서브클래스(subclass)

## 기본 문법

```python
class 기반클래스이름:
    코드
 
class 파생클래스이름(기반클래스이름):
    코드
```

## 예제

```python
class Person:
    def greeting(self):
        print('안녕하세요.')
 
class Student(Person):
    def study(self):
        print('공부하기')
```
```python
> james = Student()
> james.greeting()    # 안녕하세요.: 기반 클래스 Person의 메서드 호출
안녕하세요.
> james.study()       # 공부하기: 파생 클래스 Student에 추가한 study 메서드
공부하기 
```

## 상속관계확인 

```python
> issubclass(Student, Person)
True
```

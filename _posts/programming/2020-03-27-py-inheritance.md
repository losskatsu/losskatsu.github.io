---
title: "[python] 파이썬 상속(inheritance), 오버라이딩(overriding) 개념" 
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

# 파이썬 상속(inheritance)과 오버라이딩(overriding) 개념

본 포스팅은 [코딩도장](https://dojang.io/mod/page/view.php?id=2384)을 참고하였습니다. 

## 상속 정의 

* 부모클래스(parent class), 슈퍼클래스(super class), 기반클래스
* 자식클래스(child class), 서브클래스(subclass), 파생클래스 

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

## 초기화가 포함될 경우 슈퍼클래스의 변수 반환

```python
class Person:
    def __init__(self):
        print('Person __init__')
        self.hello = '안녕하세요.'
 
class Student(Person):
    def __init__(self):
        print('Student __init__')
        self.school = '파이썬 코딩 도장'
 
james = Student()
print(james.school)
print(james.hello)    # 기반 클래스의 속성을 출력하려고 하면 에러가 발생함
```

위 코드가 에러나는 이유는 기반클래스 Person의 __init__ 메소드가 호출되지 않았기 때문에 self.hello가 실행되지 않습니다. 

## super()로 기반클래스 초기화하기 

```python
class Person:
    def __init__(self):
        print('Person __init__')
        self.hello = '안녕하세요.'
 
class Student(Person):
    def __init__(self):
        print('Student __init__')
        super().__init__()                # super()로 기반 클래스의 __init__ 메서드 호출
        self.school = '파이썬 코딩 도장'
 
james = Student()
print(james.school)
print(james.hello)
```

## 기반 클래스를 초기화하지 않아도 되는 경우

```python
class Person:
    def __init__(self):
        print('Person __init__')
        self.hello = '안녕하세요.'
 
class Student(Person):
    pass
 
james = Student()
print(james.hello)
```

이처럼 파생 클래스에 __init__ 메서드가 없다면 기반 클래스의 
__init__ 이 자동으로 호출되므로 기반 클래스의 속성을 사용할 수 있습니다.


## 오버라이딩

오버라이딩은 기존의 함수를 덮어씌운다는 느낌입니다. 

```python
class Person:
    def greeting(self):
        print('안녕하세요.')
 
class Student(Person):
    def greeting(self):
        super().greeting()    # 기반 클래스의 메서드 호출하여 중복을 줄임
        print('저는 파이썬 코딩 도장 학생입니다.')
```

```python
> james = Student()
> james.greeting()
안녕하세요. 
저는 파이썬 코딩 도장 학생입니다.
```

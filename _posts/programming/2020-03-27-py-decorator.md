---
title: "[python] 파이썬 데코레이터 개념" 
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

# 파이썬 데코레이터 개념

본 포스팅은 [코딩도장](https://dojang.io/mod/page/view.php?id=2427)을 참고하였습니다.

```python
def decorator1(func):
    def wrapper():
        print('decorator1')
        func()
    return wrapper
 
def decorator2(func):
    def wrapper():
        print('decorator2')
        func()
    return wrapper
 
# 데코레이터를 여러 개 지정
@decorator1
@decorator2
def hello():
    print('hello')
```

```python
> hello()
decorator1
decorator2
hello
```

데코레이터를 사용하지 않았을 떄는 아래와 같음

```python
> decorated_hello = decorator1(decorator2(hello))
> decorated_hello()
```

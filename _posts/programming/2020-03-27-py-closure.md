---
title: "[python] 파이썬 클로저 기초 개념" 
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

# 파이썬 클로저 기초 개념

본 포스팅은 [코딩도장](https://dojang.io/mod/page/view.php?id=2366)을 참고하였습니다.

* [파이썬 클로저 복습하기](https://losskatsu.github.io/programming/py-closure/)
* [파이썬 데코레이터 복습하기](https://losskatsu.github.io/programming/py-decorator/)
* [파이썬 상속, 오버라이딩 복습하기](https://losskatsu.github.io/programming/py-inheritance/)

## 클로저 

아래와 같은 함수가 있다고 합시다.

```python
def calc():
    a = 3
    b = 5
    def mul_add(x):
        return a * x + b    # 함수 바깥쪽에 있는 지역 변수 a, b를 사용하여 계산
    return mul_add          # mul_add 함수를 반환
```
잘보시면 calc()함수 속에는 또다른 함수 mul_add(x)가 있는데,
mul_add(x)에 쓰이는 a, b값은 mul_add 밖에 있는 변수 a, b 입니다.
또한 calc()의 리턴값을 보면 특정 값이 아니라 또다른 함수입니다. 

```python
> c = calc()
> print(c)
<function __main__.calc.<locals>.mul_add(x)>
```

따라서 calc()를 변수 c에 집어넣고 c를 출력해보면 함수 주소가 찍히는 것을 보실 수 있습니다. 
프로그램의흐름을보면 

* 1단계: calc() 호출
* 2단계: 함수 mul_add(x) 호출 -> 이 시점에서 calc()는 종료
* 3단계: mul_add(x) 결과로 a*x+b 출력
* 4단계: mul_add(x) 종료

위를 보시면 calc()가 이미 종료되었는데, 
뒤이어 mul_add(x)가 혼자 동작됩니다. 
이상하죠, 함수 calc()가 종료되면 calc내부의 지역변수인 a, b도 사라져야하는데 그렇지않고 
mul_add에 들어갑니다!
즉, 2단계에서 calc()는 이미 종료되었지만 함수주소 및 지역변수 a, b 주소를 계속 물고 있다가 
mul_add(x)가 호출되었을때 calc()가 물고있던 자신의 주소(함수주소)와 지역변수 주소를 mul_add(x)에게 주는 것입니다. 
함수를 둘러싼 환경(지역변수, 코드 등)을 계속 물고있다가, 함수를 호출할때 다시 꺼내서 사용하는 함수를 클로저 라고 합니다. 
여기서는 c에 저장된 함수(calc)가 클로저입니다. 
이를 정리하면 프로그램 흐름은 아래와 같습니다.

* 1단계: calc() 호출
* 2단계: calc()의 리턴값으로 함수 mul_add(x) 주소 호출
* 3단계: calc() 종료, 그러나 자신의 함수 주소와 지역변수 정보를 아직 메모리 상에 물고 있음.
* 4단계: mul_add(x) 작동 시작
* 5단계: a * x + b 계산해야하는데 a, b값이 필요하므로 calc()에게 값 요청
* 6단계: mul_add(x)에게 calc()가 자신이 물고 있던 a, b값 전달
* 7단계: a * x + b 계산결과 리턴
* 8단계: mul_add(x) 종료 

 ## 클로저를 쓰는 이유

* 클로저는지역변수와 코드를 묶어서 사용하고 싶을 때 활용. 
* 클로저에 속한 지역변수는 바깥에서 직접 접근할 수 없으므로 데이터를 숨기고 싶을 때 활용

## 람다식을 이용한 클로저 표현

```python
def calc():
    a = 3
    b = 5
    return lambda x: a * x + b    # 람다 표현식을 반환 
```

```python
> c = calc()
> c(1)
8
```


---
title: "[python] 파이썬 언더바, 언더스코어, 밑줄 개념" 
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


# 파이썬 언더바, 언더스코어, 밑줄 개념


* [파이썬 클로저 복습하기](https://losskatsu.github.io/programming/py-closure/)
* [파이썬 데코레이터 복습하기](https://losskatsu.github.io/programming/py-decorator/)
* [파이썬 상속, 오버라이딩 복습하기](https://losskatsu.github.io/programming/py-inheritance/)
* [파이썬 언더스코어](https://losskatsu.github.io/programming/py-underscore/)


## 1. 언더바

파이썬에서는 언더바(언더스코어, 밑줄)를 사용합니다. 
지금부터는 언더바라는 용어를 사용하겠습니다. 
파이썬에서는 언더바를 사용하는데 어떤 상황에서 언더바를 사용하는지 알아보겠습니다. 

* 인터프리터에서의 마지막 값
* 무시하는 값
* 숫자 자릿수 구분
* 모듈내에서만 변수/함수를 사용할때(앞 언더바)
* 파이썬 변수/함수명 충돌을 피하기 위해(뒤 언더바)
* 맹글링
* 매직 메소드

파이썬의 언더바는 위와 같은 상황일 때 사용하는데 지금부터 하나씩 알아보겠습니다. 

## 2. 인터프리터에서의 마지막 값

파이썬을 실행하고 다음과 같이 입력해보겠습니다.

```python
>>> 3+4
7
>>> _+3
10
```

위 코드 첫줄에서 3 더하기 4의 결과는 7입니다. 
그리고 두번째 코드는 언더바 더하기 3인데, 
이때 언더바는 앞선 3 더하기 4의 결과인 7이라는 것을 알 수 있습니다. 
즉, 이 상황에서 언더바는 앞선 코드 실행의 결과가 들어가는 것을 알 수 있습니다.

## 3. 무시하는 값

```python
>> list01 = [1,2,3,4,5]
>> a, b, _, d, e = list01
>> print(a)
1
>> print(b)
2
>> print(_)
3
>> print(d)
4
>> print(e)
5
```

위와 같이 리스트 내의 원소를 각각 네이밍 할때 언더바를 사용하면 해당 위치의 원소는 무시하겠다는 의미인데, 
사실 언더바를 변수로 생각하고 print해보면 결과가 나오긴 합니다. 

```python
>> list01 = [1,2,3,4,5]
>> a, *_, e = list01
>> print(a)
1
>> print(*_)
2 3 4
>> print(e)
5
```

위 코드와 같이 애스터리스크(별표)를 사용하면 여러개를 무시할 수도 있습니다. 
별표언더바를 print해보면 생략된 리스트 원소를 확인할 수 있습니다.

```python
list01 = [[1,2],[3,4],[5,6]]

for _, b in list01:
    print(b)
```
```python
2
4
6
```

언더바는 반복문에서도 사용할 수 있습니다. 
위 코드는 리스트원소의 두번째 값만 print하겠다는 의미입니다. 

```python
list01 = [[1,2],[3,4],[5,6]]

for _, b in list01:
    print(_, b)
```
```python
1 2
3 4
5 6
```

물론 언더바를 print하면 결과가 나오긴 합니다.

## 4. 숫자 자릿수 

```python
num1 = 100000
num2 = 100_000
num3 = 10_0_00_0
print(num1)
print(num2)
print(num3)
```
```python
100000
100000
100000
```

위 코드와 같이 언더바는 숫자형 변수를 사용할 때 자리수 구분을 위해 사용하기도 합니다. 
실 생활에서는 자리수 구분을 천(1000) 단위로 구분하는데 
파이썬에서는 딱히 자리수 구분을 해야만 하는 위치는 없습니다. 
다만 실생활에서와 같이 천단위로 구분을 해주면 보기 편하겠죠. 
위 코드는 어느 자리에 구분을 주던 상관 없다는 것을 알 수 있습니다. 

## 5. 앞 언더바, 변수/함수를 모듈 내에서만 사용하고 싶을때

다음과 같이 greeting.py 라는 모듈을 만든다고 해보겠습니다.

```python
# greeting.py
def hi():
    print('hi')

def _hello():
    print('hello')
```

위 모듈을 불러와서 hi함수와 ```_hello``` 함수를 사용해보겠습니다.

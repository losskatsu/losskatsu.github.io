---
title: "[python] 파이썬 클래스, 객체 개념" 
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

# 파이썬 클래스, 객체 개념

**참고링크**

* [윈도우에 아나콘다를 사용해 파이썬 가상환경 설치하기](https://losskatsu.github.io/programming/py-conda/)
* [맥북에 파이썬 가상환경(pyenv) 설치하기](https://losskatsu.github.io/it-infra/pyenv-osx/)
* [우분투에 파이썬 가상환경(pyenv) 설치하기](https://losskatsu.github.io/programming/pyenv/)
* [CentOS에 파이썬 가상환경(pyenv) 설치하기](https://losskatsu.github.io/it-infra/pyenv-centos6/)
* [함수, 모듈, 패키지의 차이점](https://losskatsu.github.io/programming/function-module-package/)
* [클래스, 객체 개념](https://losskatsu.github.io/programming/class-object/)


## 1. 클래스

클래스는 추상화 할 대상의 틀이라고 생각할 수 있습니다. 
클래스는 추상화할 대상과 관련된 변수 및 함수를 포함합니다. 
예를 들어 '인간'이라는 추상적인 개념을 클래스 형태로 표현하면 다음과 같습니다.

```python
class Human:
    blood,
    hobby,
    def running:
        print(“달린다.”);
```

위 코드는 인간을 나타내는 Human이라는 클래스를 만든 것입니다. 
개념을 설명하기 위한 코드이므로 아직 파이썬으로 실행은 시킬 수 없습니다. 
Human이라는 클래스에는 blood, hobby라는 변수와 running이라는 함수로 구성되어 있습니다. 
Human 이라는 추상적인 개념을 변수 blood, hobby와 함수 running의 조합으로 정의한 것입니다. 
그렇다면 Human의 실체는 존재할까요? 그렇지 않습니다. 
클래스 Human은 추상적인 개념으로 실체화 되지 않았습니다. 
추상적인 클래스의 실체화는 객체(object)를 통해 구현가능합니다. 
마치 우리 눈으로 ‘인간’이라는 추상적인 개념은 볼 수 없지만 ‘철수’라는 실제 인물은 볼 수 있는 것과 같습니다. 
객체는 인스턴스(instance)라는 단어와 혼용됩니다. 


```python
class Human:	
    def __init__(self, blood, hobby): 
        self.blood = blood
        self.hobby = hobby
        
    def run(self, time): 
        print(time, "초 동안 달린다.") 
```

위 코드는 Human 클래스를 나타내는 코드입니다. 
먼저 class문으로 클래스를 생성할 수 있습니다. 
클래스 이름은 Human으로 정했습니다. 
다음으로 __init__ 함수가 사용되는데, 
이 함수는 초기값을 정할 때 사용합니다. 
초기값이란 객체를 생성할 때 지정해줘야하는 값을 의미합니다. 
Human 클래스의 초기값으로는 blood와 hobby를 설정해주어야합니다. 
그리고 __init__ 함수의 첫 번째 입력 변수가 self인데 이는 객체 자기 자신을 나타내는 것으로 초기값을 설정해야하는 변수 이름이 아닙니다. 
그리고 Human 클래스를 구성하는 함수로 run이라는 함수가 존재합니다. 
run함수는 time을 매개 변수로 받아 time초 만큼 달린다는 메시지를 출력하는 함수입니다. 


# 2. 객체(object)

앞서 만든 클래스를 기반으로 객체를 생성해보겠습니다. 

```python
cheolsoo = Human('A','soccer')
younghee = Human('B','music')
```
먼저 cheolsoo라는 객체를 만듭니다. 
객체 cheolsoo는 blood='A'이고 hobby='soccer'라는 초기값으로 생성합니다. 
그리고 younghee라는 객체도 만들어보겠습니다. younghee는 blood='B', hobby='music'의 초기값으로 생성됩니다.


```python
>>> print(cheolsoo.blood)
A
```
앞서 생성된 객체의 데이터를 확인해보겠습니다. 먼저 cheolsoo의 blood를 확인해보면 A라는 것을 알 수있습니다.  

```python
>>> print(cheolsoo.hobby)
soccer
```
객체 cheolsoo의 hobby는 soccer라는 것을 알 수 있습니다.  

```python
>>> cheolsoo.run(10)
10 초 동안 달린다.
```

이번에는 객체 내 run 함수를 실행해보겠습니다. 
입력 변수로 10을 입력하면 ’10 초 동안 달린다’라는 메시지가 출력되는 것을 볼 수 있습니다.

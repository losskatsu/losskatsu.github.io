---
title: "확률적 사고 방식" 
categories:
  - statistics
tags:
  - statistics
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 확률적 사고 방식(stochastic thinking)

본 포스팅은 [MIT 강의](https://www.youtube.com/watch?v=-1BnXEwHUok&t=505s&ab_channel=MITOpenCourseWare)를 참고로 작성했습니다. 

## 1. 역사

동일한 인풋을 넣었을 때 동일한 아웃풋이 나오는 경우, 이 경우를 예측가능(predictable)하다라고 말합니다. 
하지만 실제 우리가 살고 있는 세계는 불확실한 상황이 많기 때문에 예측가능한 프로그래밍은 도움이 안될때가 많습니다. 
예전에 뉴턴역학이 처음 등장했을 때, "사과가 나무에서 떨어지는 것은 중력 때문이다"라는 문장처럼 
이 세계를 명확히 설명할수 있는 것 처럼 보였습니다. 
하지만 시간이 흘러 20세기초, 하이젠베르크는 causal nondeterminism이라는 것을 발표하게 됩니다. 
이는 아주 밑바닥, 근본적인 레벨에서 실제 물리 세계는 예측할 수 없다는 의미입니다. 
즉, 사건이 발생할 것이다라고 예측할순 있어도, 100% 확신할 수는 없다는 의미입니다. 확률이 1이 될 순 없다는 뜻이죠. 
그리고 아인슈타인은 하이젠베르크의 주장을 반대하면서 "신은 주사위 놀이를 하지 않는다"라는 명언을 남겼습니다. 

## 2. 서론

이제 본격적으로 예를 들면서 시작해봅시다. 
두개의 동전을 섞은 후 바닥에 뒤집어 놓는다고 가정해봅시다. 
결과는 (앞, 앞), (뒤, 뒤), (앞, 뒤), (뒤, 앞) 중 하나일 것입니다. 무엇이 정답일까요? 
여러분은 답을 몰라서 확률적 결정을 하지만, 저는 답을 알고 있기 때문에 저한테는 확률적 상황이 아닙니다. 
따라서 세계가 예측가능하든, 그렇지 않든 우리는 전체 세계에 대해 완벽한 정보를 가질 수 없기 때문에 예측가능하지 않다고 생각하는 것입니다. 
이를 predictive nondeterminism 이라고 합니다. 

## 3. 확률과정(stochastic process)

그렇다면 불확실성을 계산하는 방법에 대해 이야기 해봅시다. 이를 확률과정론(stochastic process)이라고 합니다. 
어떤 진행중인 프로세스의 다음 상태(state)는 이전 상태에 달려있습니다. 어떤 확률적 요소를 포함해서 말이죠. 
주사위를 굴리는 프로그램을 작성한다고 해봅시다.

```python
def rollDie():
    return an int between 1 and 6
```

위와 같은 상황을 "underdetermined"라고 부릅니다. 
즉, 어떤 값이 리턴값으로 나올지 모르는 것이죠. 
하지만 일단 한번 호출하면 매번 호출할 때마다 같은 값이 나올 거라는 것은 알 수 있습니다. 
즉, 랜덤성을 요구하지 않는다는 것이죠.

```python
def rollDie():
    return a randomly chosen int between 1 and 6
```

반대로 위와 같은 상황은 랜덤성을 요구합니다. 
리턴값을 랜덤으로 결정하죠. 이를 stochastic implementation 이라고 부릅니다. 

## 4. 파이썬으로 랜덤프로세스 실행하기 

```python
import random

def rollDie():
    return random.choich([1,2,3,4,5,6])

def testRoll(n=10):
    result = ''
    for i in range(n):
        result = result + str(rollDie())
    print(result)
```

위 코드에서 1부터 6까지 숫자가 뽑힐 확률은 동일합니다. 균일분포를 따르죠. 
자, 그럼 이제 testRoll을 실행해봅시다. 결과는 어떨까요>? 
11111이라는 결과가 나올 확률은 1/(6^5)입니다. 약 0.0001286 정도 되네요. 

## 5. 확률의 기본적인 성질

확률은 0부터 1까지의 범위를 가집니다. 0은 불가능하다는 뜻이고, 1은 보장할 수 있다는 뜻이죠. 
그리고 사건이 발생할 확률이 p라고 하면 발생하지 않을 확률은 1-p 입니다. 
그리고 사건이 모두 독립일 때 사건이 모두 일어날 확률은 각 사건이 발생할 확률의 곱과 같습니다. 
두사건의 결과가 서로에게 영향을 미치지 않을 때 두 사건은 독립이라고 합니다. 
사람들이 하는 흔한 실수는 사건이 독립적이지 않은데 독립적이라고 가정하고 계산하는 것입니다. 


2135

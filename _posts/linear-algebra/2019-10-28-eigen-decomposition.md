---
title: "[선형대수] 대각화(Diagonalization)와 고유값분해(eigenvalue decomposition)의 의미" 
categories:
  - linear-algebra
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


# 대각화(Diagonalization)와 고유값분해(eigenvalue decomposition)의 의미

* [고유값, 고유벡터 복습하기](https://losskatsu.github.io/linear-algebra/eigen/)
* [행렬식 복습하기](https://losskatsu.github.io/linear-algebra/determinant/)
* [내적 복습하기](https://losskatsu.github.io/linear-algebra/innerproduct/)
* [기저 복습하기](https://losskatsu.github.io/linear-algebra/basis/)
* [랭크, 차원 복습하기](https://losskatsu.github.io/linear-algebra/rank-dim/)
* [선형변환 복습하기](https://losskatsu.github.io/linear-algebra/linear-trans/)
* [직교행렬 복습하기](https://losskatsu.github.io/linear-algebra/orthogonal/)
* [대각화, 고유값분해 복습하기](https://losskatsu.github.io/linear-algebra/eigen-decomposition/)
* [특이값 분해 복습하기](https://losskatsu.github.io/linear-algebra/svd/)


## 1.고유값 분해의 정의

안녕하세요, 오늘은 고유값분해(eigenvalue decomposition)에 대해 알아보겠습니다. 언제나 그랬듯 위키백과 정의부터 보시겠습니다.

> 선형대수학에서, 고유값 분해 또는 스펙트럼 분해는 행렬을 정형화된 형태로 분해함으로써 행렬이 고유값 및 고유벡터로 표현된다. 
대각화 가능 행렬만이 인수분해 될 수 있다. 

위 정의를 읽어보면 고유값 분해는 어떤 행렬을 고유값과 고유벡터를 이용해 다른 형태로 표현하는 것이네요. 
그리고 분해되기 위한 조건은 초기 행렬이 대각화 가능해야한다는 것을 알 수 있습니다. 
고유값과 고유벡터에 대해선 이전시간에 다루었으므로 해당 포스팅을 참고해주시구요[링크: 고유값, 고유벡터](https://losskatsu.github.io/linear-algebra/eigen/), 
오늘은 '대각화가능'이라는 말부터 살펴보겠습니다.

## 2.닮음(Similar)

대각화를 이야기하기전에 '닮음'이라는 성질에 대해 먼저 알아야하는데요, 
우리가 일상생활에서 쓰는 '닮았다'라는 말은 두 대상이 동일하진 않지만 '비슷하다'라는 느낌이 들 때 쓰는데요.
행렬에서 닮음(similar)라고 함은, $P^{-1}AP = B$를 만족하는 가역행렬 P가 존재할 때, 
정사각행렬 A와 B는 서로 닮음 이라고 합니다. 
행렬 A와 B는 동일한 행렬은 아니지만 서로 비슷하다는 의미죠. 
이 때 '가역행렬 P'란 P의 역행렬이 존재한다는 뜻입니다. 
역행렬이 존재하기 위해서는 [행렬식](https://losskatsu.github.io/linear-algebra/determinant/)이 0이 되면 안되겠죠?
그리고 한걸음 더 나아가서 $ B = P^{T}AP$를 만족하면 [직교행렬](https://losskatsu.github.io/linear-algebra/orthogonal/) P가 존재할때, 
B는 A에 직교닮음(orthogonally similar)라고 합니다.

## 3.직교 대각화(Orthogonal Diagonalization)

방금 다루었던, 직교 닮음에서 정사각행렬 B가 대각행렬 D라면 어떨까요? 
즉, $P^{T}AP = D$를 만족하는 직교행렬 P가 존재하는 경우죠. 
이런 경우 직교행렬 P는 A를 '직교 대각화' 한다고 말하며, 
A는 '직교 대각화 가능(orthogonally diagonalizable)'하다고 말합니다. 
$P^{T}AP = D$ 이 식을 잘 보시면 행렬 A에 어떤 [선형변환](https://losskatsu.github.io/linear-algebra/linear-trans/)을 취했을 때, 
대각 원소만 남는 대각행렬이 된다고 생각하시면 편하실 것 같아요. 
그리고 A가 만약 직교 대각화 가능하다면 A는 반드시 대칭행렬이어야합니다. 
대칭행렬은 $A^{T}=A$, 즉, 자기 자신과 전치행렬이 같아지는 특징이 있는데요. 
행렬 A가 대칭행렬이어야하는 이유는 아래와 같습니다. 

$ A^{T} = (PDP^{T})^{T} = (P^{T})^{T}D^{T}P^{T} = PDP^{T} = A $

우리가 아는 대칭행렬 중 아주 유명한 대칭행렬이 있습니다. 
그것은 바로 공분산 행렬인데요, 대칭행렬에 관해 적용할 수 있는 여러가지 방법들은 공분산 행렬을 다룰 때 큰 도움이 됩니다. 

![figure01](/assets/images/eigen_decomposition/covariance_matrix.jpg){: width="500"}

## 4.고유값분해(eigen decomposition)

자, 이제 오늘의 주인공인 고유값 분해(또는 스펙트럴 분해)까지 왔습니다. 
고유값 분해는 직교대각화의 한 종류라고 생각하시면 됩니다. 
사실 직교대각화를 이해하셨다면 고유값 분해도 쉽게 이해하실 수 있습니다. 
제가 선형대수 포스팅 중 가장 먼저했던 포스팅이 [고유값, 고유벡터](https://losskatsu.github.io/linear-algebra/eigen/) 였는데요, 
그만큼 중요하다는 뜻이겠죠. 
이번에도 고유값, 고유벡터가 쓰입니다. 
즉 직교대각화에서 쓰이는 '직교'벡터 $P$가 고유값 분해에서는 고유벡터를 이용해 만들고, 
대각행렬의 원소에 해당하는 것이 고유값이라고 생각하시면 됩니다. 
즉 쉽게 말해 어떤 대칭행렬 A의 고유값과 고유벡터가 존재할때 A의 스펙트럴 분해는 아래와 같습니다.

![figure02](/assets/images/eigen_decomposition/covariance_matrix2.jpg){: width="500"}

위 그림을 설명하자면 고유값분해의 정의대로 어떤 대칭행렬 A를 고유값과 고유분해를 이용해 분해한 것이네요.

![figure03](/assets/images/eigen_decomposition/covariance_matrix3.jpg){: width="500"}

마지막으로 고유값 분해의 위키백과 정의를 보시면서 오늘 포스팅을 마치겠습니다.

> 선형대수학에서, 고유값 분해 또는 스펙트럼 분해는 행렬을 정형화된 형태로 분해함으로써 행렬이 고유값 및 고유벡터로 표현된다. 
대각화 가능 행렬만이 인수분해 될 수 있다.

## 5.마무리

오늘 배운 고유값 분해는 머신러닝에서 많이 쓰이는데요. 
특히 유명한 것은 고유값분해를 $m \times n$ 행렬로 일반화 시킨 특이값 분해(singular value decomposition, SVD) 입니다. 
다음 시간에는 특이값 분해에 대해 알아보겠습니다. 감사합니다. 


### 잠깐! 선형대수, 머신러닝에 대해 좀 더 자세히 알고 싶다면?

<a href="http://www.yes24.com/Product/Goods/97032765?OzSrank=1"><img src="/assets/images/mybook/book_cover01.JPG" width="100" align="middle"> [선형대수와 통계학으로 배우는 머신러닝 with 파이썬](http://www.yes24.com/Product/Goods/97032765?OzSrank=1)

<br/>

<a href="http://www.yes24.com/Product/Goods/105772247"><img src="/assets/images/mybook/linear_algebra.PNG" width="100" align="middle"> [알고리즘 구현으로 배우는 선형대수 with 파이썬](http://www.yes24.com/Product/Goods/105772247)
  
<br/>

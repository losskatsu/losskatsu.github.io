---
title: "[선형대수] 직교행렬(Orthogonal Matrix)의 의미" 
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

# 직교행렬(Orthogonal Matrix)의 의미, 개념

* [고유값, 고유벡터 복습하기](https://losskatsu.github.io/linear-algebra/eigen/)
* [행렬식 복습하기](https://losskatsu.github.io/linear-algebra/determinant/)
* [내적 복습하기](https://losskatsu.github.io/linear-algebra/innerproduct/)
* [기저 복습하기](https://losskatsu.github.io/linear-algebra/basis/)
* [랭크, 차원 복습하기](https://losskatsu.github.io/linear-algebra/rank-dim/)
* [선형변환 복습하기](https://losskatsu.github.io/linear-algebra/linear-trans/)
* [직교행렬 복습하기](https://losskatsu.github.io/linear-algebra/orthogonal/)
* [대각화, 고유값분해 복습하기](https://losskatsu.github.io/linear-algebra/eigen-decomposition/)
* [특이값 분해 복습하기](https://losskatsu.github.io/linear-algebra/svd/)



## 1.직교행렬(Orthogonal Matrix)의 정의

안녕하세요, 오늘 알아볼 내용은 직교행렬(Orthogonal Matrix)입니다. 먼저 위키백과 정의 보시겠습니다. 

> 선형대수학에서 직교행렬(Orthogonal Matrix)은 행벡터와 열벡터가 유클리드 공간의 정규 직교 기저를 이루는 실수 행렬이다.

라고 합니다. 
주요 키워드는 행벡터, 열벡터, 유클리드 공간, 정규 직교 기저, 실수 행렬 이네요. 
먼저 행벡터와 열벡터에 대해선 지난 시간에 [링크: 랭크, 차원](https://losskatsu.github.io/linear-algebra/rank-dim/)에서 다루었으니 해당 링크를 참고해주세요. 
다음으로 유클리드 공간이라는 단어가 나오는데요, 유클리드 공간은 일반적인 평면과 공간을 일반화 한 것입니다. 
쉽게 좌표공간계라고 생각하셔도 무방할 것 같아요. 
또한 정규직교기저라는 단어는 다음 단락에서 알아보도록 하구요, 
마지막으로 실수 행렬은 말 그대로 실수로 구성된 행렬을 의미합니다. 
이렇게 보니 오늘 알아볼 부분이 명확해지네요. 정규 직교 기저에 대해 알아봅시다.

## 2.정규 직교 기저

### 2.1. 기저?

정규 직교 기저에서 우리는 이미 '기저'라는 단어를 접했습니다. 
기저는 어떤 벡터 공간을 생성하는 벡터들이죠. 
기저에 대해서 복습하고 싶으신 분은 [링크: 기저](https://losskatsu.github.io/linear-algebra/basis/)를 참고해주세요. 
그럼 이제 '정규 직교'라는 말만 남네요. 먼저 직교라는 말에 대해 알아보겠습니다.

### 2.2. 정규?

정규 직교 기저에서 쓰이는 '정규'라는 단어는 벡터의 크기가 1임을 의미합니다. 
벡터의 크기는 이전 시간에 내적을 공부하면서 배웠는데요. 
벡터의 크기에 대해 복습하고 싶으신 분은 [링크: 내적](https://losskatsu.github.io/linear-algebra/innerproduct/)을 참고해 주세요. 

### 2.3. 직교?

직교란 두 직선 또는 두 평면이 직각을 이루며 만나는 것입니다. 
제가 이전에 [기저](https://losskatsu.github.io/linear-algebra/basis/)에 대해 설명할 때 
그린 예시들 중 기저 벡터들이 서로 직각을 이루는 경우가 있었는데요, 해당 경우가 직교라고 생각하시면 될 것 같아요. 


### 2.4. 그렇다면 정규 직교 기저란?

위 내용을 종합해보면 정규 직교 기저란 '벡터의 크기가 1이고 서로 수직은 기저 벡터'라는 것을 아실 수 있습니다. 
정규 직교 직교라는 성질은 선형대수학에서 굉장히 중요합니다. 
이 조건이 붙으면 여러가지 복잡한 상황을 단순화 시키기 편해지거든요. 
이 글을 보시는 여러분들도 정규 직교 직교와 친해지면 좋을 것 같아요.


## 3. 직교 행렬의 수학적 정의


위에서 직교 행렬의 정의를 살펴보았는데요, 이번에는 직교 행렬의 수학적 정의를 보시겠습니다.


> 아래의 성질을 만족하는 정사각행렬 A를 직교 행렬이라고 합니다. $A^{-1} = A^{T}$, 또는 $AA^{T} = A^{T}A = I$


위 정의에 따르면 직교행렬의 역행렬은 직교행렬 자신의 전치행렬(transpose matrix)와 같다는 사실을 알 수 있습니다. 
이전 문단에서 정규 직교 기저라는 성질을 이용하면 상황을 단순화 시키기 좋다고 했었는데요. 
직교행렬의 수학적 정의를 이용하면 역행렬을 구하는게 상당히 쉬워집니다. 
학교 시험 보시면서 역행렬을 손으로 구해본 적이 있으실 텐데요, 사실 실제로 이 역행렬을 구하는건 쉽지 않습니다. 
하지만 직교행렬이라는 조건이 붙으면 행렬의 행과 열을 바꾸는, 즉 전치 시키는 것만으로도 역행렬을 아주 쉽게 구할 수 있습니다. 


## 4. 직교 행렬의 성질


다음으로 직교 행렬의 성질에 대해 알아보겠습니다.


(1) 직교 행렬의 전치 행렬은 직교 행렬입니다. <br />
(2) 직교 행렬의 역행렬은 직교 행렬입니다. <br />
(3) 직교 행렬의 곱은 직교 행렬입니다. <br />
(4) 만약 A가 직교 행렬이라면 A의 행렬식은 1 또는 -1입니다.([링크: 행렬식 참고](https://losskatsu.github.io/linear-algebra/determinant/))


마지막으로 직교 행렬(Orthogonal Matrix)의 정의를 다시 한번 보면서 포스팅을 마치겠습니다. 감사합니다.


> 선형대수학에서 직교행렬(Orthogonal Matrix)은 행벡터와 열벡터가 유클리드 공간의 정규 직교 기저를 이루는 실수 행렬이다.


### 잠깐! 선형대수, 머신러닝에 대해 좀 더 자세히 알고 싶다면?

<a href="http://www.yes24.com/Product/Goods/97032765?OzSrank=1"><img src="/assets/images/mybook/book_cover01.JPG" width="100" align="middle"> [선형대수와 통계학으로 배우는 머신러닝 with 파이썬](http://www.yes24.com/Product/Goods/97032765?OzSrank=1)

<br/>


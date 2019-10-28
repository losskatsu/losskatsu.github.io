---
title: "[선형대수] 대각화(Diagonalization)와 고유값분해(eigen decomposition)의 의미" 
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


# 대각화(Diagonalization)와 고유값분해(eigen decomposition)의 의미

안녕하세요, 오늘은 고유값분해에 대해 알아보겠습니다. 언제나 그랬듯 위키백과 정의부터 보시겠습니다.

> 선형대수학에서, 고유값 분해 또는 스펙트럼 분해는 행렬을 정형화된 형태로 분해함으로써 행렬이 고유값 및 고유벡터로 표현된다. 
대각화 가능 행렬만이 인수분해 될 수 있다. 

위 정의를 읽어보면 고유값 분해는 어떤 행렬을 고유값과 고유벡터를 이용해 다른 형태로 표현하는 것이네요. 
그리고 그렇게 분해되기 위한 조건은 분해 이전 행렬이 대각화 가능해야한다는 것을 알 수 있습니다. 
고유값과 고유벡터에 대해선 이전시간에 다루었으므로 해당 포스팅을 참고해주시구요[링크: 고유값, 고유벡터](https://losskatsu.github.io/linear-algebra/eigen/), 
오늘은 '대각화가능'이라는 말부터 살펴보겠습니다.

## 1.닮음(Similar)

대각화를 이야기하기전에 '닮음'이라는 성질에 대해 먼저 알아야하는데요, 
행렬에서 닮음(similar)라고 함은, $$P^{-1}AP = B$$를 만족하는 가역행렬 P가 존재할 때, 
정사각행렬 A와 B는 서로 닮음 이라고 합니다. 
이 때 가역행렬 P란 P의 역행렬이 존재한다는 뜻입니다. 
그리고 한걸음 더 나아가서 $$ B = P^{T}AP$$를 만족하면 직교행렬 P가 존재할때, 
B는 A에 직교닮음(orthogonally similar)라고 합니다.

## 2.직교 대각화(Orthogonal Diagonalization)

방금 다루었던, 직교 닮음에서 정사각행렬 B가 대각행렬 D라면 어떨까요? 
즉, $$P^{T}AP = D$$를 만족하는 직교행렬 P가 존재하는 경우죠. 
이런 경우 직교행렬 P는 A를 '직교 대각화' 한다고 말하며, 
A는 '직교 대각화 가능(orthogonally diagonalizable)'하다고 말합니다. 
그리고 A가 만약 직교 대각화 가능하다면 A는 대칭행렬이어야합니다. 
행렬 A가 대칭행렬이어야하는 이유는 아래와 같습니다.

$ A^{T} = (PDP^{T})^{T} = (P^{T}^{T}D^{T}P^{T} = PDP^{T} = A $

우리가 아는 대칭행렬 중 아주 유명한 대칭행렬이 있습니다. 
그건 바로 공분산 행렬인데요, 
따라서 대칭행렬에 관해 적용할 수 있는 여러가지 방법들은 공분산 행렬을 다룰 때 유용한 도움이 됩니다. 

![figure01](/assets/images/eigen_decomposition/covariance_matrix.jpg){: width="500"}

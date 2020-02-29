---
title: "[머신러닝] K-means 클러스터링 개념 정리" 
categories:
  - machine-learning
tags:
  - machine-learning
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# K-means 클러스터링 개념 정리

## K-Means 클러스터링 간단 개념

K-Means 클러스터링은 N개의 데이터를 K개의 클러스터로 나누는 클러스터링 기법입니다. 
각 클러스터는 자신의 평균값을 가지고 있습니다. 
k번째 클러스터의 평균을 $m^{k}$라고 하겠습니다. 
각각의 데이터는 I차원에 있다고 하겠습니다. 
즉, $x=(x_1, \dots , x_i, \dots , x_I)$ 꼴입니다. 
쉬운 예로 2차원 데이터면 $x=(1,2)$ 꼴로 표현 되겠지요. 
k-means 클러스터링에서는 거리 개념이 사용되는데요. 
여기서는 유클리드거리를 사용하며 아래 식을 사용합니다. 

$$ d(x,y) = \sqrt(\sum(x_i - y_i)^2) $$


## 클러스터링 단계 

### 1. 그룹 평균 초기화
각 그룹의 평균 $m^{k}$를 초기화 합니다. 참고로 초기화 하는 방법에도 여러가지가 있습니다. 
가장 기본적인 방법은 랜덤값을 평균으로 취하는 것입니다. 

### 2. 그룹할당
모든 데이터 $x^{n}$ 대해 가장 가까운 평균에 속하게 합니다. 
즉, 각 데이터 포인트에 대해 각 그룹의 평균까지의 거리를 계산하고, 가장 가까운 그룹으로 속하게 하는 것입니다. 
이를 수식으로 적으면 아래와 같은데요. 

$$ \hat{k^(n)} = \argmin_{k}[d(m^{k}, x^{n})] $$

### 3. 평균 업데이트
각 그룹에 대한 새로운 평균값을 업데이트 합니다.

$$ 
r_{k}^(n) = 
\begin{cases}
1 & \text{if} \, \hat{k}^{(n)}=k \\
0 & \text{if} \, \hat{k}^{(n)} \neq k \\
\end{cases}
$$

### 4. 반복
2번으로 돌아갑니다.


## k-means 클러스터링의 한계


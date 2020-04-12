---
title: "Robust LogitBoost and Adaptive Base Class(ABC) LogitBoost" 
categories:
  - paper-translation
tags:
  - reinforcement-learning
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# Robust LogitBoost and Adaptive Base Class(ABC) LogitBoost

[원문링크](https://arxiv.org/ftp/arxiv/papers/1203/1203.3491.pdf)

## Introduction

우선 $\{ y_i, x_i \}_{i=1}^{N}$ 을 트레이닝 셋이라고 합시다. 이때 $N$을 피쳐벡터(feature vector)라고하고, 
$x_i$를 $i$번째 피쳐벡터, $y_i \in \{ 0,1,2,\dots, K-1\}$을 $i$번째 클래스라벨(class label)이라 하고 $K \geq 3$인 멀티 클래스 분류문제라고 합시다.

그러면 모델 분류기 $p_{i,k}$는 

$$ p_{i,k} = P(y_i = k | x_i) = \frac{e^{F_{i,k}(x_i)}}{\sum_{s=0}^{K-1}e^{F_{i,k}(x_i)}}$$

로 정의 됩니다. 이때 $F_{i,k}(x_i) = \beta_{k}^{T}x_{i}$이고 Logitboost는 유연한 "additive model"을 채택하는데, 이는 아래와 같다.

$$ F^{(M)}(x) = \sum_{m=1}^{M}\rho_{m}h(x;a_m) $$

이때 $h(x;a_m)$는 약한 분류기이다. 여기서 파라미터는 $\rho_m, a_m$인데 이들은 데이터로 부터 학습된다. 
학습 방법은 아래와 같은 log-likelihood 함수를 최소화시킴으로써 학습된다. 

## 알고리즘




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

우선 ${y_i, x_i}_{i=1}^{N}$ 을 트레이닝 셋이라고 합시다. 이때 $N$을 피쳐벡터(feature vector)라고하고, 
$x_i$를 $i$번째 피쳐벡터, $y_i \in {0,1,2,\dots, K-1}$을 $i$번째 클래스라벨(class label)이라 하고 $K \geq 3$인 멀티 클래스 분류문제라고 합시다.



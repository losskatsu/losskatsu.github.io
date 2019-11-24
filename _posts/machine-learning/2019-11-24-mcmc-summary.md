---
title: "[머신러닝] 몬테카를로 시뮬레이션(MCMC) 요약" 
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


# 몬테카를로 시뮬레이션(Markov Chain Monte Carlo Method) 요약

## 2. Simple Monte Carlo

### 2.1 Accuracy of simple Monte Carlo

몬테카를로의 목적은 표본평균을 이용해 모평균을 추정하는 것이다. 
우리는 우리가 알기 원하는 확률변수 $$Y$$의 평균을 $$\mu = E(Y)$$로 표현한다. 
그리고나서 $$Y$$의 분포에서 iid(Independent and Identically Distributed)를 만족하는 $$Y_1, \dots , Y_n$$을 생성한다. 


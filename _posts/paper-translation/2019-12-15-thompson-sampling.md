---
title: "Analysis of Thompson Sampling for the Multi-armed Bandit Problem" 
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

# Analysis of Thompson Sampling for the Multi-armed Bandit Problem

## Abstract

Multi-armed bandit problem은 순차적 결정 문제에서 exploration/exploitation 균형을 연구하는데 있어 유명한 모델이다. 
이런 잘 연구된 문제에 대해 많은 알고리즘이 존재한다. 
1933년, 초기 알고리즘은 W.R 톰슨에 의해 고안되었다. 
이 알고리즘은 톰슨 샘플링(Thompson Sampling)이라고 불려지는데, 이 톰슨 샘플링은 순수 베이지안 알고리즘(natural Bayesian algorithm)이다. 
기본적인 아이디어는 여러개의 arm중에서 베스트 arm을 선택하는 확률을 따르도록 arm 하나를 선택하는 것이다. 
톰슨 샘플링 알고리즘은 실험적으로 최적화에 가까워지는 것을 보여주었다. 
게다가, 실행하는데 있어 효율적이며, 지연되는 피드백에 대해 작은 후회(regret)와 같은 바람직한 특성을 보여준다. 
그러나, 이론적으로 이 알고리즘을 이해하는 것은 꽤 제한적이다. 
이 논문은 처음에는 톰슨 샘플링이 확률적 Multi-armed bandit problem에 대해 logarithmic expected regret을 달성하는 것을 보여줄 것이다. 


## 1. Introduction

Multi-armed bandit problem은 순차적인 결정 문제에서 exploration/exploitation 균형을 모델링한다. 
Multi-armed bandit problem을 일반화 시킨 버전은 다수 존재한다. 
초기 연구중 톰슨이 제안한 순수 베이지안 알고리즘으 regret을 최소화 시킨다. 
기본적인 아이디어는 모든 arm에 대해 보상분포(reward distribution)의 모수의 단순 사전분포를 가정한다. 
또한 어떤 타임 스텝에서든지 best arm의 사후분포를 따르도록 플레이한다. 
이러한 알고리즘을 톰슨 샘플링(Thompson Sampling)이라고 하고, 
톰슨 샘플링은 randomized probability matching algorithms 족에 속한다. 
우리는 톰슨샘플링 알고리즘이 베이지안 접근법이라고 강조했지만, 
실제로 사전분포에 상관없는 stochastic Multi-armed bandit model을 적용한다. 
여기서 stochastic Multi-armed bandit model이란 모든 arm에 대해 보상함수의 모수는 알수는 없지만 고정되어 있다.

### 1.1 The multi-armed bandit problem

stochastic multi-armed bandit(MAB) problem을 생각해보자. 
우리에게 N개의 arm을 가지고 있는 슬롯 머신이 주어져 있다. 
각 타임스텝 $$t = 1,2,3, \dots $$에서 N개의 arm중 하나를 선택해서 플레이한다. 


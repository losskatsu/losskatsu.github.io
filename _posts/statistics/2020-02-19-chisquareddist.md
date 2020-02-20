---
title: "[기초통계] 카이제곱분포 의미 및 개념 정리" 
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

# 카이제곱분포 의미 및 개념 정리

## 참고링크 
* [확률변수 복습하기](https://losskatsu.github.io/statistics/random-variable/)
* [확률분포 복습하기](https://losskatsu.github.io/statistics/prob-distribution/)
* [모집단과 표본 복습하기](https://losskatsu.github.io/statistics/population-sample/)
* [평균과 분산 복습하기](https://losskatsu.github.io/statistics/mean-vairance/) 
### 이산확률분포
* [베르누이분포, 이항분포](https://losskatsu.github.io/statistics/binomial/) 
* [기하분포, 음이항분포](https://losskatsu.github.io/statistics/geometric-negative/)
* [초기하분포](https://losskatsu.github.io/statistics/hypergeometric/)
* [포아송분포](https://losskatsu.github.io/statistics/poisson/)
### 연속확률분포
* [정규분포](https://losskatsu.github.io/statistics/normaldist/)
* [감마분포](https://losskatsu.github.io/statistics/gammadist/)
* [지수분포](https://losskatsu.github.io/statistics/exponentialdist/)
* [카이제곱분포](https://losskatsu.github.io/statistics/chisquareddist/)
* [베타분포](https://losskatsu.github.io/statistics/betadist/)
* [균일분포](https://losskatsu.github.io/statistics/uniformdist/)

## 1. 카이제곱분포의 정의

> 카이제곱분포(chi-squared distribution)은 p개의 서로 독립적인 표준정규 확률변수를 각각 제곱한 다음 합해서 얻어지는 분포이다. 이 때 p를 자유도라고 하며, 카이제곱분포의 매개변수가 된다. 카이제곱 분포는 신뢰구간이나 가설검정 등의 모델에서 자주 등장한다. 


## 2. 카이제곱분포의 확률밀도함수, 평균, 분산

![figure01](/assets/images/statistics/chisquared/chisquared01.jpg){: width="500"}


## 2. 감마분포와의 관계 
 
사실 카이제곱분포는 [감마분포](https://losskatsu.github.io/statistics/gammadist/)의 특수한 경우라고 생각하실수 있습니다. 
카이제곱분포는 감마분포에서 $\alpha = p/2$, $\beta = 2$인 경우를 나타냅니다. 
따라서 [감마분포](https://losskatsu.github.io/statistics/gammadist/)를 이해하고 계신다면 카이제곱분포도 쉽게 이해하실수 있습니다. 

## 3. 표준정규분포와의 관계

카이제곱분포의 정의에서 알 수 있듯, 카이제곱분포는 [표준정규확률변수](https://losskatsu.github.io/statistics/normaldist/)를 각각 제곱한 다음 합새서 얻어지는 분포인데요. 
쉽게 말해 [표준정규확률변수](https://losskatsu.github.io/statistics/normaldist/)를 제곱해서 더하면 카이제곱분포가 되는 것인데요. 
이를 수식으로 정리하면 아래와 같습니다. 

표준정규 확률변수 $X_{1}, \dots , X_{p}$가 있다고 가정하면 

$$ Q = \sum_{i=1}^{p} X_{i}^{2} $$

는 자유도 p의 카이제곱분포입니다. 이를 $ Q \sim \chi_{p}^{2}$ 으로 표현합니다. 

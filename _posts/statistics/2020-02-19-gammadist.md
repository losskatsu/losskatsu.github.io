---
title: "[기초통계] 감마분포 의미 및 개념 정리" 
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

# 감마분포 의미 및 개념 정리

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

## 1. 감마분포의 정의

> 감마분포는 연속확률분포로, 두개의 매개변수를 받으며 양의 실수를 가질 수 있다. 

위 정의는 위키백과에서 가지고 온 것인데요. 자세하게 나와있지는 않아서 보충설명해 드리면, 
감마분포는 $\alpha$번째 사건이 발생할때까지의 대기시간의 분포라고 생각하시면 될 것 같습니다. 

## 2. 감마함수의 정의 

감마분포를 이야기하기 전에 감마함수를 먼저 아셔야하는데요. 
감마함수를 알아보도록 하겠습니다. 
감마합수는 아래와 같은데요. 
뭔가 복잡해보이지만 하나의 표현식이라고 생각하시면 편하실 것 같습니다. 

![figure01](/assets/images/statistics/gamma/gamma01.jpg){: width="500"}


## 3. 감마분포의 확률밀도함수, 평균, 분산

감마분포의 [확률밀도함수](https://losskatsu.github.io/statistics/prob-distribution/#), [평균, 분산](https://losskatsu.github.io/statistics/mean-vairance/#)은 다음과 같습니다.

![figure02](/assets/images/statistics/gamma/gamma02.jpg){: width="500"}

## 4. 감마분포 vs 지수분포

감마분포는 [지수분포](https://losskatsu.github.io/statistics/exponentialdist/)와 관련이 있는데요. 
[지수분포](https://losskatsu.github.io/statistics/exponentialdist/)는 첫번째 사건이 발생할 때 까지의 대기시간의 분포인 반면, 
감마분포는 $\alpha$번째 사건이 발생할 때 까지의 대기사간의 분포라고 보시면 됩니다. 
즉, 지수분포는 감마분포의 특수한 경우라고 생각하시면 되겠습니다. 

## 참고. 확률분포간 관계도

![figure100](/assets/images/statistics/dist_rel.jpg){: width="700"}



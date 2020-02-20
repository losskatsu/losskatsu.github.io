---
title: "[기초통계] 지수분포 의미 및 개념 정리" 
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

# 지수분포 의미 및 개념 정리

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


## 1. 지수분포의 정의

> 지수분포(exponential distribution)은 연속확률분포의 일정이다. 사건이 서로 독립적일 때, 일정 시간 동안 발생하는 사건의 횟수가 포아송분포를 따른다면, 다음 사건이 일어날 때까지의 대기 시간은 지수분포를 따른다. 이는 기하분포와 유사한 측면이 있다. 

## 2. 지수분포의 확률밀도함수, 평균, 분산

지수분포의 [확률밀도함수](https://losskatsu.github.io/statistics/prob-distribution/), [평균, 분산](https://losskatsu.github.io/statistics/mean-vairance/#)은 아래와 같습니다. 

![figure01](/assets/images/statistics/exponential/exponential01.jpg){: width="500"}

## 3. 지수분포 vs 포아송분포

지수분포의 정의에서도 언급되었듯이 지수분포는 여러가지 분포와 연관지어 생각할 수 있습니다. 
먼저 알아볼 것은 [포아송분포](https://losskatsu.github.io/statistics/poisson/#)와의 관계인데요. 
포아송분포와 지수분포는 사건을 바라보는 관점이 다릅니다. 
어떤 단위 시간 동안 발생하는 사건을 관찰한다고 했을때, 포아송분포는 단위 시간 당 발생하는 사건의 **횟수**를 관측합니다. 
반면 지수분포는 사건이 일어날때까지의 **대기 시간**을 관측합니다. 
즉, 지수분포는 **대기시간**, 포아송분포는 **횟수** 입니다. 

## 4. 지수분포 vs 기하분포 

지수분포는 또한 기하분포와도 관련이 있는데요. 지수분포는 사건이 발생할때가지의 **대기시간** 인 반면, 
기하분포는 사건이 발생할때까지의 **시도횟수** 입니다. 
이러한 차이는 결국 지수분포는 [연속형 확률분포](https://losskatsu.github.io/statistics/prob-distribution/#)이고 기하분포는 [이산형 확률분포](https://losskatsu.github.io/statistics/prob-distribution/#)라는 것을 알 수 있습니다. 

## 5. 지수분포 vs 감마분포

지수분포는 감마분포의 특별한 형태입니다. 2.에서 지수분포의 확률밀도함수를 보시면 지수분포는 감마분포에서 $\alpha$가 1인 경우라는 것을 알 수 있습니다. 

## 참고. 확률분포간 관계도

![figure100](/assets/images/statistics/dist_rel.jpg){: width="700"}




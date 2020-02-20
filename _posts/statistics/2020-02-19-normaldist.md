---
title: "[기초통계] 정규분포 의미 및 개념 정리" 
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

# 정규분포 의미 및 개념 정리

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

## 1. 정규분포의 정의

> 정규분포(normal distribution) 혹은 가우시안 분포(Gaussian distribution)은 연속확률분포의 하나이다. 정규분포는 수집된 자료의 분포를 근사하는데에 가주 사용되며, 이것은 중심극한정리에 의하여 독립적인 확률변수들의 평균은 정규분포에 가까워지는 성질이 있기 때문이다. 특히 평균이 0이고 표준편차가 1인 정규분포는 표준정규분포(standard normal distribution)이라고 한다. 

정규분포는 여러가지 확률분포 중 가장 기초가 되는 분포입니다. 
확률분포를 잘 모르시는 분리더라도 정규분포 혹은 종모양분포라는 말은 한번쯤은 들어보셨을 텐데요. 
그만큼 중요한 분포입니다. 

## 2. 정규분포의 확률밀도함수, 평균, 분산

정규분포의 [확률밀도함수](https://losskatsu.github.io/statistics/prob-distribution/#), [평균, 분산](https://losskatsu.github.io/statistics/mean-vairance/#)은 다음과 같습니다.

![figure01](/assets/images/statistics/normal/normaldist01.jpg){: width="500"}


## 3. 중심극한정리

정규분포의 정의에서 중심극한정리(central limit theorem) 라는 말이 나오는데, 이름만 봐서는 중심으로 간다는 느낌이네요. 
중심극한정리의 정의는 다음과 같습니다. 

> 중심극한정리(central limit theorm, CLT)는 동일한 확률분포를 가진 독립확률변수 n개의 평균의 분포는 n이 적당히 크다면 정규분포에 가까워진다는 정리이다. 

정의를 보면 이해하기 다소 어려우실수 있는데요. 우선 [확률분포](https://losskatsu.github.io/statistics/prob-distribution/#)를 가진 [독립확률변수](https://losskatsu.github.io/statistics/random-variable/)라고 했으니 해당 [확률변수](https://losskatsu.github.io/statistics/random-variable/)는 [평균과 분산](https://losskatsu.github.io/statistics/mean-vairance/#)을 가질 수 있겠죠. 이 때, 이 [평균과 분산](https://losskatsu.github.io/statistics/mean-vairance/#)도 [확률분포](https://losskatsu.github.io/statistics/prob-distribution/#)를 가지게 되는데요. 중심극한 정리는 n이 커진다면 그 확률분포가 정규분포에 가까워 진다는 뜻입니다. 

## 4. 표준정규분포

표준정규분포(standard normal distribution)은 정규분포에서 평균이 0, 분산이 1인 경우를 의미합니다. 
표준정규분포는 가설검정에서 많이 쓰이는데요. 흔히 z-검정, 표준정규분포표 라는 말을 들어보셨을 겁니다. 
정규분포를 따르는 데이터셋에서 $ Z = frac{X - \mu}{\sigma}$를 통해 $X$를 $Z$로 정규화시켜서 기존에 평균 $\mu$, ,분산 $\sigma^2$ 인 분포를 평균 0, 분산 1로 정규화시킵니다. 


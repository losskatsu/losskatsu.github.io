---
title: "[기초통계] 기하분포 및 음이항분포 정리" 
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

# 기하분포 및 음이항분포 정리

## 참고링크 
* [확률변수 복습하기](https://losskatsu.github.io/statistics/random-variable/)
* [확률분포 복습하기](https://losskatsu.github.io/statistics/prob-distribution/)
* [모집단과 표본 복습하기](https://losskatsu.github.io/statistics/population-sample/)
* [평균과 분산 복습하기](https://losskatsu.github.io/statistics/mean-vairance/) 
* [공분산, 상관계수 복습하기](https://losskatsu.github.io/statistics/cov-corr/) 
* [최대가능도추정 복습하기](https://losskatsu.github.io/statistics/mle/)
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

## 1. 기하분포

기하분포(geometric distribution)는 [이산확률분포](https://losskatsu.github.io/statistics/prob-distribution/#) 중 하나로 특이하게 두 가지 관점으로 볼 수 있습니다. 

* [베르누이시행](https://losskatsu.github.io/statistics/binomial/)에서 **처음 성공**까지 **시도한 횟수** X의 분포
* [베르누이시행](https://losskatsu.github.io/statistics/binomial/)에서 **처음 성공**까지 **실패한 횟수** Y=X-1의 분포

즉, 기하분포는 어떤 행위를 성공할때까지 시도하는데, 성공할때까지의 시도횟수 또는 실패한 횟수의 분포라고 볼 수 있습니다. 
[이산확률분포](https://losskatsu.github.io/statistics/prob-distribution/#)는 많은 경우 베르누이시행을 기반으로 이루어져있습니다.  
아래에 기하분포를 간략히 정리해보았습니다. 

<center><img src="/assets/images/statistics/geometric/geometric02.jpg" width="500"></center>

기하분포는 두가지 관점으로 정의될 수 있으므로 기하분포를 사용할때는 기준을 **시도한 횟수**로 볼 것인지, **실패한 횟수**로 볼것인지를 명확히 해야합니다. 

기하분포는 **처음 성공**까지를 보는데요. 그럼 **r번째 성공** 까지 보면 어떻게 될까요? 
기하분포를 일반화한 버전이 음이항분포 입니다. 

## 2. 음이항분포

음이항분포는 기하분포를 일반화시킨 것이므로, 아래와 같이 정의 할 수 잇습니다. 

* [베르누이시행](https://losskatsu.github.io/statistics/binomial/)에서 **r번째 성공**까지 **시도한 횟수** X의 분포
* [베르누이시행](https://losskatsu.github.io/statistics/binomial/)에서 **r번쨰 성공**까지 **실패한 횟수** Y=X-r의 분포

<center><img src="/assets/images/statistics/geometric/geometric01.jpg" width="500"></center>

추가적으로 r=3일 경우의, 음이항 분포의 mgf를 구해보았습니다.

<center><img src="/assets/images/statistics/geometric/geometric03.jpg" width="500"></center>


## 참고. 확률분포간 관계도

<center><img src="/assets/images/statistics/dist_rel.jpg" width="700"></center>



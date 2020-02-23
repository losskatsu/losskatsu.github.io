---
title: "[기초통계] 두 집단 간 평균, 분산 비교, T-test, F-test" 
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

# 두 집단 간 평균, 분산 비교, T-test, F-test

참고링크
* []()


## 1. 모분산이 알려진 경우(known population variacne)

두 집단이 [iid](https://losskatsu.github.io/statistics/prob-distribution/)를 따른다고 가정합시다. 

$$ x_{1}, x_{2}, \dot ,x_{n1} \sim N(\mu_{1}, \sigma_{1}^{2}) $$, <br />
$$ y_{1}, y_{2}, \dot ,y_{n2} \sim N(\mu_{2}, \sigma_{2}^{2}) $$

위 식은 $x_{1}, x_{2}, \dot ,x_{n1}$은 평균 $\mu_{1}$이고, 분산이 $\sigma_{1}^{2}$인 정규분포에서 나온 표본이라는 뜻이고,  
$y_{1}, y_{2}, \dot ,y_{n2}$는 평균 $\mu_{2}$이고, 분산이 $\sigma_{2}^{2}$인 정규분포에서 나온 표본이라는 뜻입니다. 



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

$$ x_{1}, x_{2}, \dots ,x_{n1} \sim N(\mu_{1}, \sigma_{1}^{2}) $$, <br />
$$ y_{1}, y_{2}, \dots ,y_{n2} \sim N(\mu_{2}, \sigma_{2}^{2}) $$

위 식은 $x_{1}, x_{2}, \dots ,x_{n1}$은 평균 $\mu_{1}$이고, 분산이 $\sigma_{1}^{2}$인 정규분포에서 나온 표본이라는 뜻이고,  
$y_{1}, y_{2}, \dots ,y_{n2}$는 평균 $\mu_{2}$이고, 분산이 $\sigma_{2}^{2}$인 정규분포에서 나온 표본이라는 뜻입니다. 

저희가 알고 싶은 것은 두 집단의 평균이 같냐 다르냐입니다. 
여기서 평균이 다를 경우 평균이 큰지, 작은지, 아니면 그저 다른지에 따라 아래처럼 세 가지 형태로 가설을 세울 수 있습니다. 

$$ H0: \mu_{1} - \mu_{2} = 0, H1: \mu_{1} - \mu_{2} > 0 $$, <br />
$$ H0: \mu_{1} - \mu_{2} = 0, H1: \mu_{1} - \mu_{2} < 0 $$, <br />
$$ H0: \mu_{1} - \mu_{2} = 0, H1: \mu_{1} - \mu_{2} \neq 0 $$


---
title: "[기초통계] 회귀분석 정리" 
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


# 회귀분석 정리

## 회귀분석 정의

> 회귀분석(regression analysis)는 [변수](https://losskatsu.github.io/statistics/random-variable/)들간의 함수관계를 추구하는 통계적 방법이다. 

회귀분석은 독립변수와 종속변수 간의 함수관계를 규명하는 통계적 방법입니다. 
그렇다면 독립변수와 종속변수는 무엇일까요?

> 독립변수(independent variable)는 입력값이나 원인을 나타내며, 종속변수(dependent variable)은 결과물이나 효과를 나타낸다. 

독립변수는 설명변수(explanatory variable)이라고도 하며, 종속변수는 반응변수(response variable)이라고도 합니다. 
독립변수와 종속변수는 $(x_i, y_i)$ 쌍으로 표현하고 독립변수의 집합을 대문자 $X$, 종속변수의 집합을 대문자 $Y$로 표현합니다. 
결국 회귀분석이란 독립변수 $X$의 분포를 분석한 후, 종속변수 $Y$의 값을 예측하는 것입니다. 
다른 말로하면 다양하게 분포된 $X$가 존재할 때, $Y$의 분포를 알아내는 것입니다. 

## MEAN FUNCTION

우리가 $Y$의 분포에 대해 관심있을 때 중요한 것이 mean function 입니다. 

$$ E(Y|X=x) = \text{a function that depends on the value of } x $$

데이터에 대해서 생각해보면 데이터는 이미 '주어졌다'는 것을 알 수 있습니다. 
'주어졌다'를 다른 말로 바꾸면 '정해졌다'라고 할 수 있는데요. 
위 식에서 기대값은 $x$값이 '이미 정해을때'라는 조건부 기대값으로 볼 수 있습니다.
이를 수식으로 나타내면,

$$ E(Y|X=x) = \beta_{0} + \beta_{1}x $$

위 mean function을 자세히 살펴보면, 직선이라는 것을 알 수 있는데요. 
$\beta_{0}$가 절편(intercept)이 되고, $\beta_{1}$은 기울기(slope)입니다. 

## VARIANCE FUNCTION

회귀분석에서 종종 적합 모델에 사용되는 가정은 모든 $x$값에 대해 분산이 동일하다는 것입니다. 
즉, 

$$ Var(Y|X=x) = \sigma^{2} $$

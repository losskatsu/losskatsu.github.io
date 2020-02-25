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

$$ E(Y|X=x) = $$

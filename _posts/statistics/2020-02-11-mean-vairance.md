---
title: "[기초통계] 평균과 분산" 
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

# 평균(mean)과 분산(variance)

## 0. 대표값

우리는 앞서 [확률변수](https://losskatsu.github.io/statistics/random-variable/), 
[표본](https://losskatsu.github.io/statistics/population-sample/)에 대해 알아보았습니다. 
우리가 구한 표본데이터는 분포를 따르게 되는데요. 
분포의 특성을 나타내는데에는 대표값이라는 개념을 사용합니다. 
대표값은 이름 그대로 여러가지 값들을 대표하는 값을 의미합니다. 
그리고 가장 흔히 쓰이는 대표값이 평균, 분산, 표준편차와 같은 대표값입니다.

## 1. 평균(mean)과 기대값(expected value)

### 1-1. 평균(mean)

평균에는 산술평균, 기하평균, 조화평균과 같이 여러 종류가 있는데요. 오늘 알아볼 평균은 산술평균을 의미합니다.

> 평균은 단순히 모든 관측값을 더해서 관측값 개수로 나눈 것이다. 


### 1-2. 기대값(expected value) 

> 기대값은 각 사건이 벌어졌을 때의 이득과 그 사건이 벌어질 확률을 곱한 것을 전체 사건에 대해 합한 값이다. 이것은 어떤 확률적 사건에 대한 평균의 의미로 생각할 수 있다.

### 1-3 평균과 기대값의 차이

사실 평균과 기대값은 동일하다고 생각해도 크게 문제 되지는 않을 것 같아요. 
실제로 두 용어를 섞어서 사용하기도 하는데요. 
저는 평균과 기대값에는 관점의 차이가 있다고 생각합니다. 
즉, 표본으로부터 얻어진 표본데이터값 자체에 중점을 두고 보면 평균이고, 
확률변수에 중점을 두고 보면 기대값이라고 생각합니다. 
다른 말로하면 표본은 이미 구해진(정해진) 데이터의 평균, 
기대값은 아직 구해지지않은 값(미래에 기대되는)에 대한 평균이라고도 볼 수 있을 것 같아요. 

## 2. 분산(variance)와 표준편차(standard deviation)

### 2-1. 분산(variance)

> 분산은 평균에 대한 편차 제곱의 평균을 구한 값이다.

### 2-2. 표준편차(standard deviation)

> 표준편차는 분산의 양의 제곱근으로 정의 된다.

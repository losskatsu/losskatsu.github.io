---
title: "[기초통계] 범주형 자료 분석" 
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

# 범주형 자료 분석

## 상대위험률과 오즈비

구분 | 결과 1 | 결과 2 | 합
----|--------|--------|---
그룹 1 | n11 | n12 | n1+
그룹 2 | n21 | n22 | n2+
합 | n+1 | n+2 | n

> 오즈비(odds ratio)란 해당 시간이 발생하지 않은 확률에 대해 그 사건이 발생한 확률의 비율로 정의된다.

상대위험률(relative risk) RR = $ \frac{n11/n1+}{n21/n2+} $

오즈비(odds ratio) OR = $ \frac{(n11/n+1)/(n21/n+1)}{(n12/n+2)/(n22/n+2)} = \frac{n11n22}{n12n21}$

## 카이제곱 검정

### 동질성검정(homogeneity test)

H0 : 실제약을 복용할 때와 위약을 복용했을 때의 발병 비율은 같다.

### 독립성검정(independence test)

H0 : 실제약 복용여부와 발병 여부는 서로 독립이다. 

그룹 수 = I, 결과 수 = J 일 때,  

$$H0: p_{1j} = p_{2j} = \dots = p_{Ij} \, (j=1,2, ..., J)$$

$$ \hat{p_{j}} = \frac{n_{+j}}{n}$$

$$ E_{ij} = n_{i+}\hat{p_{j}} = \frac{n_{i+}{n}  $$

$$ \chi^{2} = \sum_{i=1}^{I}\sum_{j=1}^{J}\frac{(n_{ij} - E_{ij})^{2}}{E_{ij}} $$

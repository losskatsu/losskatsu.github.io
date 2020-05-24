---
title: "[최적화]컨벡스 셋(Convex set)의 개념" 
categories:
  - mathematics
tags:
  - mathematics
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# [최적화] Convex set의 개념

## 1. line segment

$\mathbb{R}^n$ 공간에서의 두 점 $x_1, x_2$가 있다고 합시다. 
이 때 두 점 $x_1, x_2$을 잇는 선(line) 사이에 있는 점 $y$를 아래와 같이 표현합니다. 

$$ y = \theta x_1 + (1-\theta)x_2 $$

만약 $\theta = 0$이면 $y=x_2$가 되고, $\theta = 1$이면 $y=x_1$이 됩니다. 
이때, $ 0 \leq \theta \leq 1$이면 $x_1, x_2$간의 line segment라고 합니다. 

## 2. 아핀 셋(affine set)

특정 집합(set) $C\subseteq \mathbb{R}^n$이 아핀(affine)이라는 말은 아래와 같습니다. 
$C$ 속의 두 점을 잇는 직선이 있다고했을 때, 즉, $x_1, x_2 \in C$이고 $\theta \in \mathbb{R}^n$ 일 때, 
$ \theta x_1 + (1-\theta) x_2 \in C $s이면 $C$는 아핀 셋(affine set) 입니다. 
즉, 집합 $C$는 집합 $C$에 속하는 두 점의 선형 결합(linear combination)입니다. 
이 때, 선형 결합 계수 $\theta$들의 합은 1입니다. 

이를 2차원 이상으로 확장시키면 $\theta_1 x_1 + \cdots + \theta_k x_k$, $\theta_1+\cdots+\theta_k = 1$으로 쓸 수 있는데 
이를 포인트 $x_1, \dots, x_k$에 대한 아핀 결합(affine bombination)이라고 합니다. 
즉, 아핀 셋(affine set)은 해당 아핀 셋의 포인트에 대한 모든 아핀 결합을 포함합니다. 

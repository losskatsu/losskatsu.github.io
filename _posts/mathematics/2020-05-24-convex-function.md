---
title: "[최적화]컨벡스 함수(Convex function)의 개념" 
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

# [최적화] 컨벡스 함수(Convex function)의 개념

참고링크

* [내적 ](https://losskatsu.github.io/linear-algebra/innerproduct/)
* [컨벡스 셋(convex set)](https://losskatsu.github.io/mathematics/convex-set/)
* [라그랑주 듀얼 함수](https://losskatsu.github.io/mathematics/dual-function/)
* [Karush-Kuhn-Tucker](https://losskatsu.github.io/mathematics/kkt/)

## 1. 정의역(domain, 도메인)

함수 $f$가 다음과 같다고 합시다.

$$ f: \mathbb{R}^{p} \rightarrow \mathbb{R}^{q} $$ 

이 때, 함수 $f$의 정의역(domain)을 $\mathbf{bol} f$라고 쓰겠습니다. 
위 함수의 의미는 함수 $f$는 $\mathbb{R}^{p}$ 공간에 속하는 벡터 $p-vector$를 취한 후,
$\mathbb{R}^{q}$ 공간에 속하는 벡터 $q-vector$를 반환합니다. 

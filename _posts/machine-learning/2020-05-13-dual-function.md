---
title: "[최적화] 라그랑주 듀얼 함수(Lagrange dual function)의 개념" 
categories:
  - machine-learning
tags:
  - machine-learning
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 라그랑주 듀얼 함수(Lagrange dual function)의 개념

참고링크

* [컨벡스 셋(convex set)](https://losskatsu.github.io/mathematics/convex-set/)
* [컨벡스 함수(convex function)](https://losskatsu.github.io/mathematics/convex-function/)
* [라그랑주 듀얼 함수](https://losskatsu.github.io/mathematics/dual-function/)
* [Karush-Kuhn-Tucker](https://losskatsu.github.io/mathematics/kkt/)
* [단순 회귀분석](https://losskatsu.github.io/statistics/simple-regression/)
* [로지스틱 회귀분석](https://losskatsu.github.io/statistics/logistic-regression/)
* [릿지(ridge), 라쏘(lasso) 회귀분석](https://losskatsu.github.io/machine-learning/l1l2/)

## 최적화 문제의 표준 형식

최적화 문제의 표준적인 형식은 아래와 같습니다. 

<center><img src="/assets/images/math/dualfunction/01.jpg" width="800"></center> 

위 형식에서 $f_0(x)$를 우리가 최적화된 값을 구하고자 하는 목적함수(objective function)라고 하구요. 
subject to 다음 부터 나오는 부분, $f_i(x) \leq 0$, $h_i(x) = 0$을 제약식(constraint)라고 합니다. 
위 최적화 문제는 목적함수와 제약식이 따로 분리되어 있는데요. 
이를 하나의 식으로 정리한 것은 아래와 같으며, 
아래와 같은 식을 라그랑주 프리멀 함수(Lagrange primal function)이라고 합니다. 

## 라그랑주 프리멀 함수

<center><img src="/assets/images/math/dualfunction/02.jpg" width="800"></center> 

위 식에서 사용된 $\lambda_i$, $v_i$를 라그랑주 승수(Lagrange multiplier)라고 합니다. 

## 라그랑주 승수 벡터

<center><img src="/assets/images/math/dualfunction/03.jpg" width="800"></center> 

그리고 위와 같이 $\lambda_i$, $v_i$를 모아놓은 벡터를 라그랑주 승수 벡터(Lagrange multiplier vector)라고 합니다. 

## 라그랑주 듀얼 함수

<center><img src="/assets/images/math/dualfunction/04.jpg" width="800"></center> 

위와 같은 형태를 라그랑주 듀얼 함수(Lagrange dual function)이라고 하며, 
라그랑주 프리멀 함수의 하한(infimum)을 나타냅니다. 
만약 라그랑주 듀얼 함수의 최적값을 $d^{\ast}$라고 하고, 
우리가 구하고자 하는 최적값을 $p^{\ast}$라고 하면 아래와 같은 부등식이 성립합니다. 

$$d^{\ast} \leq p^{\ast} $$ 

위와 같은 성질을 weak duality라고 합니다. 또한 $p^{\ast} -d^{\ast}$를 optimal duality gap이라고 부릅니다. 
이는 프리말 문제의 최적값인 $p^{\ast}$와 라그랑지 유얼 함수로부터 얻어진 lower bound $d^{\ast}$의 차이를 의미합니다. 
optimal duality gap은 nonnegative 합니다. 

만약 아래와 같은 식을 만족한다면 strong duality라고 부릅니다. 

$$ d^{\ast} = p^{\ast} $$


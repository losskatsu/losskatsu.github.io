---
title: "라그랑주 듀얼 함수(Lagrange dual function)의 개념" 
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

# [최적화] 라그랑주 듀얼 함수(Lagrange dual function)의 개념

최적화 문제의 표준적인 형식은 아래와 같습니다. 

<center><img src="/assets/images/math/dualfunction/01.jpg" width="800"><center>

위 최적화 문제를 하나의 식으로 정리한 것은 아래와 같으며, 
아래와 같은 식을 라그랑주 프리멀 함수(Lagrange primal function)이라고 합니다.

<center><img src="/assets/images/math/dualfunction/02.jpg" width="800"><center>

위 식에서 사용된 $\lambda_i$, $v_i$를 라그랑주 승수(Lagrange multiplier)라고 합니다.

<center><img src="/assets/images/math/dualfunction/03.jpg" width="800"><center>

그리고 위와 같이 $\lambda_i$, $v_i$를 모아놓은 벡터를 라그랑주 승수 벡터(Lagrange multiplier vector)라고 합니다.

<center><img src="/assets/images/math/dualfunction/04.jpg" width="800"><center>

위와 같은 형태를 라그랑주 듀얼 함수(Lagrange dual function)이라고 하며, 
라그랑주 프리멀 함수의 최소값을 나타냅니다. 

<center><img src="/assets/images/math/dualfunction/05.jpg" width="800"><center>

결국 라그랑주 듀얼 함수를 최대화 시키면 우리가 구하고자 하는 최적값(optimal value)를 구할 수 있습니다.


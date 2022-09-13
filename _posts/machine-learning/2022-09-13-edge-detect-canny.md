---
title: "[머신러닝] 이미지에서 엣지 검출하기" 
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


# [머신러닝] 이미지에서 엣지 검출하기

**참고 링크**

* [Determining if a point lies on the interior of a polygon](http://web.archive.org/web/20080812141848/http://local.wasp.uwa.edu.au/~pbourke/geometry/insidepoly/)
* [한 점이 다각형 내부에 위치하는지 판별하기](https://losskatsu.github.io/machine-learning/py-polygon01/)
* [이미지에서 엣지 검출하기](https://losskatsu.github.io/machine-learning/edge-detect-canny/)

## 1. 서론 

이미지 밝기가 급격하게 변하는 이벤트가 발생할 때 이미지에서 엣지를 검출 할 수 있습니다. 
엣지를 검출하는 방법에는 여러가지가 존재하는데 크게 search-based 방법과 zero-crossing based 방법으로 나눠집니다. 
search-based 방법은 그레디언트의 1차 미분을 통해 엣지의 선명함을 측정하고, 
local directional 최댓값으로 엣지를 추정하는데 이를 gradient direction이라고 합니다. 
반면 zero-crossing based 방법은 2차 미분을 통해 엣지를 검출하는 방법입니다. 


## 2. Canny edge detector

canny edge detectgor는 이미지에서 엣지를 검출하기 위해 여러 단계를 거치는 알고리즘 입니다. 
이 알고리즘은 John F.Canny가 1986년에 개발한 알고리즘입니다. 
canny edge detector는 가우시안의 1차 미분을 이용합니다. 


## 3. canny edge detector 과정  

canny edge detector는 다음과 같은 과정을 거칩니다. 

(1) 가우시안 필터(Gaussian filter)를 이용해 이미지의 노이즈를 없애줍니다. 
(2) 이미지의 그래디언트를 구합니다. 
(3) 앞서 구한 그래디언트로 엣지 검출을 위해 필요 없는 부분을 cut-off 시킵니다. 
(4) 잠재적인 엣지(potential edge)를 결정하기 위해 threshold를 두번 적용시킵니다. 
(5) 엣지를 결정합니다.

### 3-1. Gaussian filter란?

이미지에서 엣지 검출할 때, 이미지는 노이즈에 영향을 쉽게 받습니다. 
따라서 에러를 줄이기 위해 노이즈를 필터링하는 것이 중요한데, 
이를 위해 가우시안 필터 커널을 이미지에 두릅니다. 



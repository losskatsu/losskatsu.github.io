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

### 참고링크  

|머신러닝|딥러닝|선형대수|기초통계|최적화|
|:------:|:------:|:------:|:------:|:------:|
|[k-means](https://losskatsu.github.io/machine-learning/kmeans-clustering/)|[신경망이란](https://losskatsu.github.io/machine-learning/dl-basic01/)|[고유값,고유벡터](https://losskatsu.github.io/linear-algebra/eigen/)| [확률변수](https://losskatsu.github.io/statistics/random-variable/) |[컨벡스 셋](https://losskatsu.github.io/machine-learning/convex-set/)|
|[k-최근접이웃](https://losskatsu.github.io/machine-learning/knn/)|[성능함수](https://losskatsu.github.io/machine-learning/dl-basic02/)|[행렬식](https://losskatsu.github.io/linear-algebra/determinant/)| [확률분포](https://losskatsu.github.io/statistics/prob-distribution/) | [컨벡스 함수](https://losskatsu.github.io/machine-learning/convex-function/)|
|[선형회귀](https://losskatsu.github.io/statistics/simple-regression/)|[신경망 학습](https://losskatsu.github.io/machine-learning/dl-basic03/)|[내적](https://losskatsu.github.io/linear-algebra/innerproduct/)| [모집단과 표본](https://losskatsu.github.io/statistics/population-sample/) |[라그랑주 듀얼](https://losskatsu.github.io/machine-learning/dual-function/)|
|[로지스틱회귀](https://losskatsu.github.io/statistics/logistic-regression/) |[교차연결](https://losskatsu.github.io/machine-learning/dl-basic04/) |[기저](https://losskatsu.github.io/linear-algebra/basis/)| [평균과 분산](https://losskatsu.github.io/statistics/mean-vairance/)   | [KKT 조건](https://losskatsu.github.io/machine-learning/kkt/) |
|[릿지,라쏘회귀](https://losskatsu.github.io/machine-learning/l1l2/) |[합성곱 신경망](https://losskatsu.github.io/machine-learning/dl-basic05/) |[랭크, 차원](https://losskatsu.github.io/linear-algebra/rank-dim/)| [공분산, 상관계수](https://losskatsu.github.io/statistics/cov-corr/)  | [ROC 커브](https://losskatsu.github.io/machine-learning/stat-roc-curve/) |
|[의사결정나무](https://losskatsu.github.io/machine-learning/decision-tree/) |[배치, 에포크 차이](https://losskatsu.github.io/machine-learning/epoch-batch/) | [선형변환](https://losskatsu.github.io/linear-algebra/linear-trans/)| [최대가능도추정](https://losskatsu.github.io/statistics/mle/) | [크로스 밸리데이션](https://losskatsu.github.io/machine-learning/cross-validation/) |
|[서포트벡터머신](https://losskatsu.github.io/machine-learning/svm/) | [텐서플로기초(1)](https://losskatsu.github.io/machine-learning/tensorflow-basic01/) |[직교행렬](https://losskatsu.github.io/linear-algebra/orthogonal/) | [베르누이,이항분포](https://losskatsu.github.io/statistics/binomial/)  | [실루엣 스코어](https://losskatsu.github.io/machine-learning/silhouette-score) |
|[원클래스 SVM](https://losskatsu.github.io/machine-learning/oneclass-svm/)  | [텐서플로기초(2)](https://losskatsu.github.io/machine-learning/tensorflow-basic02/)  | [고유값분해](https://losskatsu.github.io/linear-algebra/eigen-decomposition/)| [기하,음이항분포](https://losskatsu.github.io/statistics/geometric-negative/) | |
|[LDA ](https://losskatsu.github.io/machine-learning/lda/) | [seq2seq](https://losskatsu.github.io/machine-learning/seq2seq-keras/) | [특이값분해](https://losskatsu.github.io/linear-algebra/svd/) | [초기하분포](https://losskatsu.github.io/statistics/hypergeometric/) | |
|[GMM](https://losskatsu.github.io/machine-learning/gmm/) | [opencv기초](https://losskatsu.github.io/machine-learning/opencv01) | |[포아송분포](https://losskatsu.github.io/statistics/poisson/) | |
|[부스팅](https://losskatsu.github.io/machine-learning/boosting/) | [resnet](https://losskatsu.github.io/machine-learning/resnet) | | [정규분포](https://losskatsu.github.io/statistics/normaldist/) | |
|[사이킷런 실습](https://losskatsu.github.io/machine-learning/sklearn/) |[다각형내부판별](https://losskatsu.github.io/machine-learning/py-polygon01) | |[감마분포](https://losskatsu.github.io/statistics/gammadist/) | |
| | [엣지판별](https://losskatsu.github.io/machine-learning/edge-detect-canny) | | [지수분포](https://losskatsu.github.io/statistics/exponentialdist/) | |
| | | | [카이제곱분포](https://losskatsu.github.io/statistics/chisquareddist/) | |
| | | | [베타분포](https://losskatsu.github.io/statistics/betadist/) | |
| | | | [균일분포](https://losskatsu.github.io/statistics/uniformdist/) | |


<br/>

<a href="http://www.yes24.com/Product/Goods/97032765" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00001_ml.png" width="800" align="middle">

<br/>



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

<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>

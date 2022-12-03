---
title: "[머신러닝] K-means 클러스터링 개념 정리" 
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

# K-means 클러스터링 개념 정리

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




## K-Means 클러스터링 간단 개념

K-Means 클러스터링은 N개의 데이터를 K개의 클러스터로 나누는 클러스터링 기법입니다. 
각 클러스터는 자신의 평균값을 가지고 있습니다. 
k번째 클러스터의 평균을 $m^{k}$라고 하겠습니다. 
각각의 데이터는 I차원에 있다고 하겠습니다. 
즉, $x=(x_1, \dots , x_i, \dots , x_I)$ 꼴입니다. 
쉬운 예로 2차원 데이터면 $x=(1,2)$ 꼴로 표현 되겠지요. 
k-means 클러스터링에서는 거리 개념이 사용되는데요. 
여기서는 유클리드거리를 사용하며 아래 식을 사용합니다. 

$$ d(x,y) = \sqrt{\sum(x_i - y_i)^2} $$


## 클러스터링 단계 

### 1. 그룹 평균 초기화
각 그룹의 평균 $m^{k}$를 초기화 합니다. 참고로 초기화 하는 방법에도 여러가지가 있습니다. 
가장 기본적인 방법은 랜덤값을 평균으로 취하는 것입니다. 

### 2. 그룹할당
모든 데이터 $x^{n}$ 대해 가장 가까운 평균에 속하게 합니다. 
즉, 각 데이터 포인트에 대해 각 그룹의 평균까지의 거리를 계산하고, 가장 가까운 그룹으로 속하게 하는 것입니다. 
이를 수식으로 적으면 아래와 같은데요. 

$$ \hat{k^{(n)}} = argmin_{k}[d(m^{(k)}, x^{(n)})] $$

### 3. 평균 업데이트
각 그룹에 대한 새로운 평균값을 업데이트 합니다.

$$ 
r_{k}^{(n)} = 
\begin{cases}
1 & \text{if} \, \hat{k}^{(n)}=k \\
0 & \text{if} \, \hat{k}^{(n)} \neq k \\
\end{cases}
$$

위 식의 $r_{k}$는 지시함수(indicator function)로서 해당 클러스터인 경우 1, 아니면 0입니다. 
아래식에서 사용법을 보시면 이해가 되실 겁니다. 

$$ m^{(k)} = \frac{\sum_{n}r_{k}^{(n)}x^{(n)}}{\sum_{n}r_{k}^{(n)}} $$

### 4. 반복
2, 3단계를 반복합니다. 언제까지 반복하냐면 2단계에서 바뀌는게 없을 때 까지 반복합니다. 


## k-means 클러스터링의 한계

사실 k-menas 클러스터링에서는 가중치를 주거나하지 않기 때문에 클러스터간 데이터의 밀도의 차이가 있을 경우 클러스터링이 잘 되지 않는 경향이 있습니다. 
또한 이 방법은 클러스터의 모양을 고려하지 않습니다. 


<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>


---
title: "[기초통계] 지수분포 의미 및 개념 정리" 
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

# 지수분포 의미 및 개념 정리


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



## 1. 지수분포의 정의

> 지수분포(exponential distribution)은 연속확률분포의 일정이다. 사건이 서로 독립적일 때, 일정 시간 동안 발생하는 사건의 횟수가 포아송분포를 따른다면, 다음 사건이 일어날 때까지의 대기 시간은 지수분포를 따른다. 이는 기하분포와 유사한 측면이 있다. 

## 2. 지수분포의 확률밀도함수, 평균, 분산

지수분포의 [확률밀도함수](https://losskatsu.github.io/statistics/prob-distribution/), [평균, 분산](https://losskatsu.github.io/statistics/mean-vairance/#)은 아래와 같습니다. 


<center><img src="/assets/images/statistics/exponential/exponential01.jpg" width="800"></center>

## 3. 지수분포 vs 포아송분포

지수분포의 정의에서도 언급되었듯이 지수분포는 여러가지 분포와 연관지어 생각할 수 있습니다. 
먼저 알아볼 것은 [포아송분포](https://losskatsu.github.io/statistics/poisson/#)와의 관계인데요. 
포아송분포와 지수분포는 사건을 바라보는 관점이 다릅니다. 
어떤 단위 시간 동안 발생하는 사건을 관찰한다고 했을때, 포아송분포는 단위 시간 당 발생하는 사건의 **횟수**를 관측합니다. 
반면 지수분포는 사건이 일어날때까지의 **대기 시간**을 관측합니다. 
즉, 지수분포는 **대기시간**, 포아송분포는 **횟수** 입니다. 

## 4. 지수분포 vs 기하분포 

지수분포는 또한 기하분포와도 관련이 있는데요. 지수분포는 사건이 발생할때가지의 **대기시간** 인 반면, 
기하분포는 사건이 발생할때까지의 **시도횟수** 입니다. 
이러한 차이는 결국 지수분포는 [연속형 확률분포](https://losskatsu.github.io/statistics/prob-distribution/#)이고 기하분포는 [이산형 확률분포](https://losskatsu.github.io/statistics/prob-distribution/#)라는 것을 알 수 있습니다. 

## 5. 지수분포 vs 감마분포

지수분포는 감마분포의 특별한 형태입니다. 2.에서 지수분포의 확률밀도함수를 보시면 지수분포는 감마분포에서 $\alpha$가 1인 경우라는 것을 알 수 있습니다. 

## 참고. 확률분포간 관계도

<center><img src="/assets/images/statistics/dist_rel.jpg" width="800"></center>


<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>


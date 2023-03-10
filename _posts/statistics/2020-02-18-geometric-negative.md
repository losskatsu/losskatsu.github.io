---
title: "[기초통계] 기하분포 및 음이항분포 정리" 
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

# 기하분포 및 음이항분포 정리

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
## 1. 기하분포

기하분포(geometric distribution)는 [이산확률분포](https://losskatsu.github.io/statistics/prob-distribution/#) 중 하나로 특이하게 두 가지 관점으로 볼 수 있습니다. 

* [베르누이시행](https://losskatsu.github.io/statistics/binomial/)에서 **처음 성공**까지 **시도한 횟수** X의 분포
* [베르누이시행](https://losskatsu.github.io/statistics/binomial/)에서 **처음 성공**까지 **실패한 횟수** Y=X-1의 분포

즉, 기하분포는 어떤 행위를 성공할때까지 시도하는데, 성공할때까지의 시도횟수 또는 실패한 횟수의 분포라고 볼 수 있습니다. 
[이산확률분포](https://losskatsu.github.io/statistics/prob-distribution/#)는 많은 경우 베르누이시행을 기반으로 이루어져있습니다.  
아래에 기하분포를 간략히 정리해보았습니다. 

<center><img src="/assets/images/statistics/geometric/geometric02.jpg" width="500"></center>

기하분포는 두가지 관점으로 정의될 수 있으므로 기하분포를 사용할때는 기준을 **시도한 횟수**로 볼 것인지, **실패한 횟수**로 볼것인지를 명확히 해야합니다. 

기하분포는 **처음 성공**까지를 보는데요. 그럼 **r번째 성공** 까지 보면 어떻게 될까요? 
기하분포를 일반화한 버전이 음이항분포 입니다. 

<br/>

<a href="http://www.yes24.com/Product/Goods/117709828" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00004_probability.png" width="800" align="middle">

<br/>  
  
## 2. 음이항분포

음이항분포는 기하분포를 일반화시킨 것이므로, 아래와 같이 정의 할 수 잇습니다. 

* [베르누이시행](https://losskatsu.github.io/statistics/binomial/)에서 **r번째 성공**까지 **시도한 횟수** X의 분포
* [베르누이시행](https://losskatsu.github.io/statistics/binomial/)에서 **r번쨰 성공**까지 **실패한 횟수** Y=X-r의 분포

<center><img src="/assets/images/statistics/geometric/geometric01.jpg" width="500"></center>

추가적으로 r=3일 경우의, 음이항 분포의 mgf를 구해보았습니다.

<center><img src="/assets/images/statistics/geometric/geometric03.jpg" width="500"></center>


## 참고. 확률분포간 관계도

<center><img src="/assets/images/statistics/dist_rel.jpg" width="700"></center>


<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>

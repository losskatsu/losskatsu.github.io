---
title: "[기초통계] 정규분포 의미 및 개념 정리" 
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

# 정규분포 의미 및 개념 정리

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


## 1. 정규분포의 정의

> 정규분포(normal distribution) 혹은 가우시안 분포(Gaussian distribution)은 연속확률분포의 하나이다. 정규분포는 수집된 자료의 분포를 근사하는데에 가주 사용되며, 이것은 중심극한정리에 의하여 독립적인 확률변수들의 평균은 정규분포에 가까워지는 성질이 있기 때문이다. 특히 평균이 0이고 표준편차가 1인 정규분포는 표준정규분포(standard normal distribution)이라고 한다. 

정규분포는 여러가지 확률분포 중 가장 기초가 되는 분포입니다. 
확률분포를 잘 모르시는 분리더라도 정규분포 혹은 종모양분포라는 말은 한번쯤은 들어보셨을 텐데요. 
그만큼 중요한 분포입니다. 

## 2. 정규분포의 확률밀도함수, 평균, 분산

정규분포의 [확률밀도함수](https://losskatsu.github.io/statistics/prob-distribution/#), [평균, 분산](https://losskatsu.github.io/statistics/mean-vairance/#)은 다음과 같습니다.

<center><img src="/assets/images/statistics/normal/normaldist01.jpg" width="800"></center>


## 3. 중심극한정리

정규분포의 정의에서 중심극한정리(central limit theorem) 라는 말이 나오는데, 이름만 봐서는 중심으로 간다는 느낌이네요. 
중심극한정리의 정의는 다음과 같습니다. 

> 중심극한정리(central limit theorm, CLT)는 동일한 확률분포를 가진 독립확률변수 n개의 평균의 분포는 n이 적당히 크다면 정규분포에 가까워진다는 정리이다. 

정의를 보면 이해하기 다소 어려우실수 있는데요. 우선 [확률분포](https://losskatsu.github.io/statistics/prob-distribution/#)를 가진 [독립확률변수](https://losskatsu.github.io/statistics/random-variable/)라고 했으니 해당 [확률변수](https://losskatsu.github.io/statistics/random-variable/)는 [평균과 분산](https://losskatsu.github.io/statistics/mean-vairance/#)을 가질 수 있겠죠. 이 때, 이 [평균과 분산](https://losskatsu.github.io/statistics/mean-vairance/#)도 [확률분포](https://losskatsu.github.io/statistics/prob-distribution/#)를 가지게 되는데요. 중심극한 정리는 n이 커진다면 그 확률분포가 정규분포에 가까워 진다는 뜻입니다. 

## 4. 표준정규분포

표준정규분포(standard normal distribution)은 정규분포에서 평균이 0, 분산이 1인 경우를 의미합니다. 
표준정규분포는 가설검정에서 많이 쓰이는데요. 흔히 z-검정, 표준정규분포표 라는 말을 들어보셨을 겁니다. 
정규분포를 따르는 데이터셋에서 $ Z = \frac{X - \mu}{\sigma}$를 통해 $X$를 $Z$로 정규화시켜서 기존에 평균 $\mu$, ,분산 $\sigma^2$ 인 분포를 평균 0, 분산 1로 정규화시킵니다. 

## 참고. 확률분포간 관계도

<center><img src="/assets/images/statistics/dist_rel.jpg" width="800"></center>


<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>

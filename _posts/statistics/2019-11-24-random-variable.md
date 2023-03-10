---
title: "[기초통계] 확률변수(random variable)의 개념, 의미" 
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

# 확률변수(random variable)의 개념, 의미

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


머신러닝, 딥러닝, 통계학 등 확률을 다루는 분야를 공부함에 있어 확률변수(random variable)의 개념은 필수적입니다. 
다양한 분야에서 확률변수를 대상으로 여러가지 연산을 하게 되는데요, 
확률변수의 개념을 제대로 이해하지 못하고 학습시킬 경우 엉뚱한 결과가 나올 수도 있습니다. 
미분, 적분과 같은 테크닉을 아는 것도 중요하지만 그 전에 연산의 대상이되는 확률변수의 이해가 선행되어야겠죠. 
오늘은 저와 함께 확률변수에 대해 알아보겠습니다. 

## 확률변수의 정의

확률변수(random variable)란, 확률현상에 기인해 결과값이 확률적으로 정해지는 변수를 의미한다.  

## 확률현상이란

확률현상이란 어떤 결과들이 나올지는 알지만 가능한 결과들 중 어떤 결과가 나올지는 모르는 현상입니다. 
예를들어 동전을 던지는 현상에서 우리는 앞이나 뒤가 나올 것이라는 것은 알고 있습니다. 가능한 결과는 앞, 뒤 뿐이죠. 
하지만 앞, 뒤 중 어떤 결과가 나올지는 모르죠. 이것이 확률현상입니다. 

<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>  
  
## 확률변수의 개념

확률변수에는 '변수'라는 단어가 들어가네요. 
여기서 확률변수는 상수가 아닌 '변수'임을 알 수 있습니다. 
변수와 상수는 어떻게 다를까요? 
상수는 pi = 3.141592...처럼 정해져있는 수이지만, 
변수는 이름그대로 변할수있는 수입니다. 
마찬가지로 확률변수는 '변수'이므로 '변할수 있는 수'인데요. 
그럼 어떻게 변하는 것이냐, 
바로 확률적으로 변하는 것입니다. 
즉, 우리 주변에 확률적인 현상이 존재할때, 
확률변수는 확률적으로 정해지는 것이죠. 

## 확률변수의 간단한 예제

100원짜리 동전을 던지는 상황을 가정해봅시다. 
동전을 던지는 상황은 확률현상이죠. 앞이 나올지 뒤가 나올지 알 수 없으니까요. 
그리고 $X$를 **100원짜리 동전을 한 번 던졌을 때 이순신 장군이 나오는 횟수**라고 하면, 
$X$는 확률현상에 기인해 결과값이 확률적으로 정해지므로 확률변수라는 것을 알 수 있습니다.
동전을 한번 던졌을 때 나올수있는 결과는 이순신 또는 숫자 100이므로 
확률변수 $X$는 0 또는 1을 가집니다. 
$X$는 확률변수이므로 0 또는 1이 될 수 있다는 뜻입니다.
즉, 동전을 던졌을때 숫자 100이 나오면 이순신 장군이 나온 횟수는 0이므로 확률변수 $X = 0$이고, 
이순신 장군이 나오면 이순신 장군이 나온 횟수는 1이므로 확률변수 $X = 1$이 되는 것입니다. 
여기서 확률의 개념 까지 보면, 
확률변수 $X$가 0일 확률, 즉, $X=0$일 확률 = $P(X=0)$은 1/2입니다. 
동전을 던져서 숫자가 나올 확률은 50%라는 뜻이죠. 
마찬가지로 $X=1$일 확률, 즉 $P(X=1)$도 1/2입니다. 
동전을 던저셔 이순신이 나올 확률도 50%니까요. 
이를 정리하면 아래 표와 같습니다. 

확률현상| 확률 현상의 결과 | 확률변수 X | P(X)
--------|-----------|-----------|------
동전을 던짐 | 뒤 | 0 | 1/2
| 앞 | 1 | 1/2

## 정리 

확률변수의 개념은 매우 중요합니다. 
실제로 복잡한 상황을 다루다보면 변수를 상수처럼 생각하고 계산에만 치중하는 경향이 있는데요, 
확률변수의 개념을 정확히 이해함으로써 혼동하는 일이 없었으면 좋겠습니다. 

  
<br/>

<a href="http://www.yes24.com/Product/Goods/117709828" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00004_probability.png" width="800" align="middle">

<br/>  
  




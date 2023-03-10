---
title: "[기초통계] 모집단과 표본의 의미" 
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

# 모집단과 표본의 의미


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

실무에서 "모수가 작다/크다." 라는 표현을 사용하는 것을 종종 보곤 하는데요, 이는 대부분 틀린 표현인 경우가 많습니다. 
오늘은 저와 함께 모집단, 모수, 표본, 표본통계량의 개념에 대해 알아보도록 하겠습니다. 

## 1. 모집단(population)과 모수(population parameter)

### 1-1. 모집단(population)

> 모집단(population)이란 정보를 얻고자 하는 관심 대상의 전체집합을 말한다. 

쉽게 말해, 모집단은 집단 전체를 말한다고 할 수 있습니다. 
예를 들어, 어떤 게임 유저들의 하루 평균 플레이 타임을 분석하고 싶을 경우, 
모집단은 해당 게임을 플레이하는 유저 전체의 플레이 타임이 됩니다. 

### 1-2. 모수(population parameter)

> 모수(population parameter)란 모집단 분포 특성을 규정 짓는 척도. 관심의 대상이 되는 모집단의 대표값을 말한다.

위의 예에서 전체 유저의 하루 평균 플레이 타임이 60분 일 경우 모수는 60분이 됩니다.

## 2. 표본(sample)과 표본통계량(sample statistic)

### 2-1. 표본(sample)

> 표본(sample)은 모집단(population)의 부분집합이다.

즉, 표본은 모집단의 일부분이라고 할 수 있습니다. 
위의 예에서 해당 게임의 유저수가 너무 많아 100명만 뽑아서 평균 플레이타임을 본다고했을 때, 
표본은 뽑힌 100명의 플레이 타임이 될 것입니다.

### 2-2. 표본통계량(sample statistic)

> 표본통계량(sample statistic)이란 표본의 몇몇 특징을 수치화한 값이다.

표본통계량은 뽑힌 표본으로부터 대표값을 계산하는 것인데요, 
위의 예에서 100명의 하루 평균 플레이타임이 65분이라고 하면 표본통계량은 65분입니다.

<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>  
  
## 3. 모집단과 표본의 관계

### 3-1. 모수를 구하는게 불가능한 이유 

표본추출은 왜 하는 것 일까요? 
내가 관심 있는 대상이 있다면 그 대상 전체를 계산하지, 굳이 n명을 추출해서 계산할 필요가 있을까요? 
표본을 사용하는 이유는, 모집단, 모수를 알기 어려운 경우가 많기 때문입니다. 
IT기술이 발전하기전에는 데이터를 수집하는 것 자체가 어려운 경우가 많았습니다. 데이터가 귀했었죠. 
반면 요즘같은 빅데이터 시대에는 데이터를 구하는게 예전보다는 쉬워졌는데요, 
그렇다고 할지라도 모집단 전체를 관측하는 것은 불가능에 가깝습니다. 
위의 예에서 2020년 2월 10일에 X라는 게임을 플레이한 유저의 평균 플레이타임을 구하고 싶다고 가정합시다. 
쿼리를 날리면 해당 날짜에 접속한 모든 유저의 평균 플레이타임을 구할 수 있습니다. 
이는 모수처럼 보이는 데요, 과연 그럴까요? 
모집단의 모수를 구한 것 처럼 보이지만 실제로는 그렇지 않습니다. 모수에 가깝지만 모수는 아닙니다. 
왜냐하면, 데이터베이스에 존재하는 기록은 100% 정확한 경우가 아닌 경우가 많습니다. 
여기서 정확이라는 개념은 한치의 오차도 없는 측정을 의미합니다. 애초에 완벽한 측정은 불가능하죠. 
예를 들어, 무언가 기술적인 이유로 어떤 유저의 기록이 남지 않았을 경우에 계산에 포함 되지 않습니다. 
만약 10명의 기록이 남지 않았다면 실제로 하루에 10,000명이 접속했어도 데이터베이스에 존재하는 기록은 9,990명 입니다. 
이는 모집단이 아닌 표본이죠. 물론 실제로 하루에 정확히 몇 명이 접속했는지는 아무도 모릅니다. 근사치를 알 수 있을 뿐이죠. 
따라서 이 예에서 모집단이 아닌 표본을 대상으로 분석한 것입니다. 
즉, 모집단과 모수는 개념적으로는 존재하지만 실제로 구하는 것은 불가능한 경우가 많다는 것을 알 수 있습니다. 

### 3-2. 통계학이란?

통계학은 영어로 statistics인데요, 이는 표본통계량(statistic)을 이용하는 학문이라고 생각할 수 있습니다. 
즉, 통계학은 표본을 가지고 연구하는 학문입니다. 
표본통계량을 이용하여 모수를 추정하는 학문이라고 할 수 있습니다. 

## 4. 모수가 작다? 용어의 잘못된 사용

흔히 실무에서 '모수'라는 용어를 잘못 사용하는 경우가 있는데요. 
모수를 샘플 수라는 뜻으로 사용하는 경우를 종종 봅니다. 
예를 들어 쿼리를 날려 데이터베이스에 존재하는 데이터를 조회했을 때 1,000 건이 조회되었다고 합시다. 
이 경우, "모수가 1,000 이다."라는 표현을 사용하곤 하는데요. 
이는 틀린 표현입니다. 위에서 설명드렸듯, 모수는 모집단의 대표값을 의미하는 것이지 샘플 수를 의미하는 것이 아닙니다. 
또 다른 틀린 표현으로는 "모수가 작다", "모수가 크다" 등이 있습니다. 


<br/>

<a href="http://www.yes24.com/Product/Goods/117709828" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00004_probability.png" width="800" align="middle">

<br/>


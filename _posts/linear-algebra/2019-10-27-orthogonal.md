---
title: "[선형대수] 직교행렬(Orthogonal Matrix)의 의미" 
categories:
  - linear-algebra
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

# 직교행렬(Orthogonal Matrix)의 의미, 개념

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


## 1.직교행렬(Orthogonal Matrix)의 정의

안녕하세요, 오늘 알아볼 내용은 직교행렬(Orthogonal Matrix)입니다. 먼저 위키백과 정의 보시겠습니다. 

> 선형대수학에서 직교행렬(Orthogonal Matrix)은 행벡터와 열벡터가 유클리드 공간의 정규 직교 기저를 이루는 실수 행렬이다.

라고 합니다. 
주요 키워드는 행벡터, 열벡터, 유클리드 공간, 정규 직교 기저, 실수 행렬 이네요. 
먼저 행벡터와 열벡터에 대해선 지난 시간에 [링크: 랭크, 차원](https://losskatsu.github.io/linear-algebra/rank-dim/)에서 다루었으니 해당 링크를 참고해주세요. 
다음으로 유클리드 공간이라는 단어가 나오는데요, 유클리드 공간은 일반적인 평면과 공간을 일반화 한 것입니다. 
쉽게 좌표공간계라고 생각하셔도 무방할 것 같아요. 
또한 정규직교기저라는 단어는 다음 단락에서 알아보도록 하구요, 
마지막으로 실수 행렬은 말 그대로 실수로 구성된 행렬을 의미합니다. 
이렇게 보니 오늘 알아볼 부분이 명확해지네요. 정규 직교 기저에 대해 알아봅시다.

## 2.정규 직교 기저

### 2.1. 기저?

정규 직교 기저에서 우리는 이미 '기저'라는 단어를 접했습니다. 
기저는 어떤 벡터 공간을 생성하는 벡터들이죠. 
기저에 대해서 복습하고 싶으신 분은 [링크: 기저](https://losskatsu.github.io/linear-algebra/basis/)를 참고해주세요. 
그럼 이제 '정규 직교'라는 말만 남네요. 먼저 직교라는 말에 대해 알아보겠습니다.

### 2.2. 정규?

정규 직교 기저에서 쓰이는 '정규'라는 단어는 벡터의 크기가 1임을 의미합니다. 
벡터의 크기는 이전 시간에 내적을 공부하면서 배웠는데요. 
벡터의 크기에 대해 복습하고 싶으신 분은 [링크: 내적](https://losskatsu.github.io/linear-algebra/innerproduct/)을 참고해 주세요. 

### 2.3. 직교?

직교란 두 직선 또는 두 평면이 직각을 이루며 만나는 것입니다. 
제가 이전에 [기저](https://losskatsu.github.io/linear-algebra/basis/)에 대해 설명할 때 
그린 예시들 중 기저 벡터들이 서로 직각을 이루는 경우가 있었는데요, 해당 경우가 직교라고 생각하시면 될 것 같아요. 


### 2.4. 그렇다면 정규 직교 기저란?

위 내용을 종합해보면 정규 직교 기저란 '벡터의 크기가 1이고 서로 수직은 기저 벡터'라는 것을 아실 수 있습니다. 
정규 직교 직교라는 성질은 선형대수학에서 굉장히 중요합니다. 
이 조건이 붙으면 여러가지 복잡한 상황을 단순화 시키기 편해지거든요. 
이 글을 보시는 여러분들도 정규 직교 직교와 친해지면 좋을 것 같아요.


## 3. 직교 행렬의 수학적 정의


위에서 직교 행렬의 정의를 살펴보았는데요, 이번에는 직교 행렬의 수학적 정의를 보시겠습니다.


> 아래의 성질을 만족하는 정사각행렬 A를 직교 행렬이라고 합니다. $A^{-1} = A^{T}$, 또는 $AA^{T} = A^{T}A = I$


위 정의에 따르면 직교행렬의 역행렬은 직교행렬 자신의 전치행렬(transpose matrix)와 같다는 사실을 알 수 있습니다. 
이전 문단에서 정규 직교 기저라는 성질을 이용하면 상황을 단순화 시키기 좋다고 했었는데요. 
직교행렬의 수학적 정의를 이용하면 역행렬을 구하는게 상당히 쉬워집니다. 
학교 시험 보시면서 역행렬을 손으로 구해본 적이 있으실 텐데요, 사실 실제로 이 역행렬을 구하는건 쉽지 않습니다. 
하지만 직교행렬이라는 조건이 붙으면 행렬의 행과 열을 바꾸는, 즉 전치 시키는 것만으로도 역행렬을 아주 쉽게 구할 수 있습니다. 


## 4. 직교 행렬의 성질


다음으로 직교 행렬의 성질에 대해 알아보겠습니다.


(1) 직교 행렬의 전치 행렬은 직교 행렬입니다. <br />
(2) 직교 행렬의 역행렬은 직교 행렬입니다. <br />
(3) 직교 행렬의 곱은 직교 행렬입니다. <br />
(4) 만약 A가 직교 행렬이라면 A의 행렬식은 1 또는 -1입니다.([링크: 행렬식 참고](https://losskatsu.github.io/linear-algebra/determinant/))


마지막으로 직교 행렬(Orthogonal Matrix)의 정의를 다시 한번 보면서 포스팅을 마치겠습니다. 감사합니다.


> 선형대수학에서 직교행렬(Orthogonal Matrix)은 행벡터와 열벡터가 유클리드 공간의 정규 직교 기저를 이루는 실수 행렬이다.



<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>

---
title: "[선형대수] 대각화(Diagonalization)와 고유값분해(eigenvalue decomposition)의 의미" 
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


# 대각화(Diagonalization)와 고유값분해(eigenvalue decomposition)의 의미

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


## 1.고유값 분해의 정의

안녕하세요, 오늘은 고유값분해(eigenvalue decomposition)에 대해 알아보겠습니다. 언제나 그랬듯 위키백과 정의부터 보시겠습니다.

> 선형대수학에서, 고유값 분해 또는 스펙트럼 분해는 행렬을 정형화된 형태로 분해함으로써 행렬이 고유값 및 고유벡터로 표현된다. 
대각화 가능 행렬만이 인수분해 될 수 있다. 

위 정의를 읽어보면 고유값 분해는 어떤 행렬을 고유값과 고유벡터를 이용해 다른 형태로 표현하는 것이네요. 
그리고 분해되기 위한 조건은 초기 행렬이 대각화 가능해야한다는 것을 알 수 있습니다. 
고유값과 고유벡터에 대해선 이전시간에 다루었으므로 해당 포스팅을 참고해주시구요[링크: 고유값, 고유벡터](https://losskatsu.github.io/linear-algebra/eigen/), 
오늘은 '대각화가능'이라는 말부터 살펴보겠습니다.

## 2.닮음(Similar)

대각화를 이야기하기전에 '닮음'이라는 성질에 대해 먼저 알아야하는데요, 
우리가 일상생활에서 쓰는 '닮았다'라는 말은 두 대상이 동일하진 않지만 '비슷하다'라는 느낌이 들 때 쓰는데요.
행렬에서 닮음(similar)라고 함은, $P^{-1}AP = B$를 만족하는 가역행렬 P가 존재할 때, 
정사각행렬 A와 B는 서로 닮음 이라고 합니다. 
행렬 A와 B는 동일한 행렬은 아니지만 서로 비슷하다는 의미죠. 
이 때 '가역행렬 P'란 P의 역행렬이 존재한다는 뜻입니다. 
역행렬이 존재하기 위해서는 [행렬식](https://losskatsu.github.io/linear-algebra/determinant/)이 0이 되면 안되겠죠?
그리고 한걸음 더 나아가서 $ B = P^{T}AP$를 만족하면 [직교행렬](https://losskatsu.github.io/linear-algebra/orthogonal/) P가 존재할때, 
B는 A에 직교닮음(orthogonally similar)라고 합니다.

## 3.직교 대각화(Orthogonal Diagonalization)

방금 다루었던, 직교 닮음에서 정사각행렬 B가 대각행렬 D라면 어떨까요? 
즉, $P^{T}AP = D$를 만족하는 직교행렬 P가 존재하는 경우죠. 
이런 경우 직교행렬 P는 A를 '직교 대각화' 한다고 말하며, 
A는 '직교 대각화 가능(orthogonally diagonalizable)'하다고 말합니다. 
$P^{T}AP = D$ 이 식을 잘 보시면 행렬 A에 어떤 [선형변환](https://losskatsu.github.io/linear-algebra/linear-trans/)을 취했을 때, 
대각 원소만 남는 대각행렬이 된다고 생각하시면 편하실 것 같아요. 
그리고 A가 만약 직교 대각화 가능하다면 A는 반드시 대칭행렬이어야합니다. 
대칭행렬은 $A^{T}=A$, 즉, 자기 자신과 전치행렬이 같아지는 특징이 있는데요. 
행렬 A가 대칭행렬이어야하는 이유는 아래와 같습니다. 

$ A^{T} = (PDP^{T})^{T} = (P^{T})^{T}D^{T}P^{T} = PDP^{T} = A $

우리가 아는 대칭행렬 중 아주 유명한 대칭행렬이 있습니다. 
그것은 바로 공분산 행렬인데요, 대칭행렬에 관해 적용할 수 있는 여러가지 방법들은 공분산 행렬을 다룰 때 큰 도움이 됩니다. 

<center><img src="(/assets/images/eigen_decomposition/covariance_matrix.jpg" width="800"></center>

## 4.고유값분해(eigen decomposition)

자, 이제 오늘의 주인공인 고유값 분해(또는 스펙트럴 분해)까지 왔습니다. 
고유값 분해는 직교대각화의 한 종류라고 생각하시면 됩니다. 
사실 직교대각화를 이해하셨다면 고유값 분해도 쉽게 이해하실 수 있습니다. 
제가 선형대수 포스팅 중 가장 먼저했던 포스팅이 [고유값, 고유벡터](https://losskatsu.github.io/linear-algebra/eigen/) 였는데요, 
그만큼 중요하다는 뜻이겠죠. 
이번에도 고유값, 고유벡터가 쓰입니다. 
즉 직교대각화에서 쓰이는 '직교'벡터 $P$가 고유값 분해에서는 고유벡터를 이용해 만들고, 
대각행렬의 원소에 해당하는 것이 고유값이라고 생각하시면 됩니다. 
즉 쉽게 말해 어떤 대칭행렬 A의 고유값과 고유벡터가 존재할때 A의 스펙트럴 분해는 아래와 같습니다.

<center><img src="(/assets/images/eigen_decomposition/covariance_matrix2.jpg" width="800"></center>

위 그림을 설명하자면 고유값분해의 정의대로 어떤 대칭행렬 A를 고유값과 고유분해를 이용해 분해한 것이네요.

<center><img src="(/assets/images/eigen_decomposition/covariance_matrix3.jpg" width="800"></center>

마지막으로 고유값 분해의 위키백과 정의를 보시면서 오늘 포스팅을 마치겠습니다.

> 선형대수학에서, 고유값 분해 또는 스펙트럼 분해는 행렬을 정형화된 형태로 분해함으로써 행렬이 고유값 및 고유벡터로 표현된다. 
대각화 가능 행렬만이 인수분해 될 수 있다.

## 5.마무리

오늘 배운 고유값 분해는 머신러닝에서 많이 쓰이는데요. 
특히 유명한 것은 고유값분해를 $m \times n$ 행렬로 일반화 시킨 특이값 분해(singular value decomposition, SVD) 입니다. 
다음 시간에는 특이값 분해에 대해 알아보겠습니다. 감사합니다. 


<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>

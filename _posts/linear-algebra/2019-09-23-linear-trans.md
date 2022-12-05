---
title: "[선형대수] 선형변환(linear transformation)의 의미" 
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

# 선형변환(linear transformation)의 의미

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


같은 사물도 어느 각도에서 보느냐에 따라 다르게 보일 수 있습니다. 
마찬가지로 행렬이 주어졌을 때 어떤 각도로 보느냐에 따라 다르게 보일 수 있는데요. 
기존 행렬을 데이터의 집합이나 나열이라는 느낌으로 바라보신 분이 계시다면, 
오늘 다룰 선형변환은 형렬을 바라보는 새로운 각도일 수 있습니다. 
우선 위키백과 정의 부터 보고 가시겠습니다. 

> 선형변환은 선형 결합을 보존하는, 두 벡터 공간 사이의 함수이다.

심플한 정의네요. 위 정의에서 우리가 알아야 할 대목은, 
1) 선형결합을 보존하는, 2) 두 벡터공간 사이의 함수 입니다. 
지금부터 저와 하나씩 알아보도록 하겠습니다. 

## 1. 선형결합을 보존한다의 의미

선형결합을 보존한다는 게 무슨 뜻일까요? 
우선 선형결합의 뜻을 알아봅시다. 
선형 결합이란 $T(u+v) = T(u)+T(v)$, $T(ku) = kT(u)$을 의미합니다.  
그리고 선형결합을 보존한다는 뜻은 이러한 성질이 보존된다는 뜻입니다. 
쉽게말해 덧셈과 곱셈에 닫혀있다라고 보시면 됩니다. 
닫혀있다라는 말은 덧셈과 곱셈을 쓸 수 있다라는 뜻으로 생각하시면 편하실 것 같아요
(덧셈과 곱셈을 쓸 수 있는 판이 마련되어 있으니 마음껏 써라라는 뜻이기도 합니다, 
실제로 우리가 일상생활에서 더하기 곱하기를 마음껏 쓰는 이유는 판이 마련되어 있기 때문이죠).

선형결합에 대해 좀 더 말씀드리면 어떤 벡터나 행렬을 나타낼 때 우리는 무의식적으로 기저를 정하고 그 기저를 근간으로 좌표를 생각합니다. 
([기저에 대해 복습하시려면 클릭](https://losskatsu.github.io/linear-algebra/basis/))
예를 들면 (2,1)이라는 좌표는 무의식적으로 (1,0), (0,1)을 기저로 생성된 좌표라는 것이지요. 
즉, (2,1)은 아래와 같은 표현식으로 이해할 수 있습니다.

<center><img src="/assets/images/lineartrans/linear03.JPG" width="800"></center>

즉, 단순히 (2,1)이라는 벡터도 기저들의 선형결합이라는 뜻입니다. 
그럼 기저가 달라지면 좌표도 달라질까요? 

<center><img src="/assets/images/lineartrans/linear01.JPG" width="800"></center>

위 그림을 봅시다. 
위 두개의 건물은 (1,0), (0,1)을 기저로 삼았을땐 꼭대기 층의 좌표가 다를 수 있습니다. 
하지만 기울어진 건물의 경우, (1,0), (0,1)을 기저로 두었을땐 앞선 건물과 좌표가 달라지지만, 
기저 또한 기울이게 되면 앞선 건물과 같은 좌표를 가질 수 있습니다. 
즉, 서로 기저가 다른 경우, 같은 좌표를 가지더라도 같은 곳을 가리키는 것이 아니라는 뜻입니다.

## 2. 두 벡터 공간 사이의 함수

선형변환이란, 두 벡터 공간 사이의 함수라고 합니다. 
만약 벡터 공간에 대해 잘 모르시는 분은 이전 포스팅을 참고해주세요. 
두 벡터 공간 사이의 함수...선형변환은 결국 '함수'인데요. 
위키백과에서 함수를 검색하면 아래와 같은 결과가 나옵니다.

> 첫 번째 집합의 임의의 한 원소를 두 번째 집합의 오직 한 원소에 대응시키는 이항 관계이다.

쉽게 말해, 한 점을 한 벡터공간에서 다른 벡터공간으로 이동시키는데 그 이동 규칙을 선형변환이라고 합니다. 
예를 들어, 서울에 살고 있는 사람을 부산으로 이동시킨다는 규칙이 존재할 때, 
그 규칙은 함수가 되고 해당 함수가 선형변환이라고 생각하시면 됩니다. 
서울과 부산을 각기 서로다른 벡터 공간이라고 생각하시면 편할 것 같아요. 

좀 더 수학적으로 표현하자면, 아래와 같은 행렬 $A$가 있다고 가정합시다.

<center><img src="/assets/images/lineartrans/linear02.JPG" width="800"></center>

선형변환의 정의에 따르면 위와 같은 2X3 행렬은 3차원에서 2차원으로 선형변환 이라고 생각하시면 됩니다. 
즉, 행렬 $A$에 임의의 행렬 $x$를 곱하는 $Ax$의 의미는 $x$라는 벡터를 3차원에서 2차원으로 변환 시키는 것이지요. 
해당 선형변환의 결과 3차원 벡터 $x$는 2차원 벡터가 됩니다. 
위에서 예로 들었던 서울에서 부산으로 이동시키는 예는 어떨까요, 실제로 서울과 부산은 같은 차원입니다. 
그래서 서울에서 부산으로 변환 시키는 행렬이 있다면 그 행렬은 정방행렬이겠죠. 

끝으로 선형변환의 위키백과 정의와 수학적 정의를 보고 마치겠습니다.

> 선형변환은 선형 결합을 보존하는, 두 벡터 공간 사이의 함수이다.

Definition 1. If T: V -> W is a mapping from a vector space V to a vector space W, 
then T is called a linear transformation from V  to W if the following two properties hold for all vectors u and v in V 
and for all scalars k: <br />
(1) T(ku) = kT(u) <br />
(2) T(u + v) = T(u) + T(v) <br />
In the special case where V=W, the linear transformation T is called a linear operator on the vector space V.




<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>

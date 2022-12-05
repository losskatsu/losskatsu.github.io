---
title: "[선형대수] 행렬식(determinant)의 의미" 
categories:
  - linear-algebra
tags:
  - statistics
  - machine-learning
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

## 행렬식(determinant)의 의미


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




위키백과에서 행렬식을 검색하면 아래와 같은 결과가 나옵니다.
<br />

> 선형대수학에서, 행렬식(determinant)은 정사각행렬에 수를 대응시키는 함수의 하나이다. 
대략, 정사각행렬이 나타내는 선형변환이 부피를 확대시키는 정도를 나타낸다. 
<br />

### 1. determinant

행렬식은 영어로 determinant라고 합니다. 
영어사전에서 determinant를 찾아보면, '결정요인' 이라는 뜻이 나옵니다. 
잘은 모르겠지만 뭔가 '결정적인 역할을 하는' 느낌이 듭니다. 
행렬식은 과연 무엇을 결정할까요? 

### 2. 2 by 2 행렬

먼저 간단하게 $2 \times 2$ 행렬을 살펴봅시다. 

$$
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$

첫 행렬로 (1, 0), (0, 1) 두 벡터로 구성된 행렬을 봅시다. 
이 두 벡터를 좌표공간에 표현하면 아래 그림의 좌측과 같은 형태로 그릴 수 있습니다. 
그리고 두 벡터를 이용해 만들 수 있는 우측 도형의 면적이 해당 행렬의 행렬식의 절대값 입니다. 
<br />

<center><img src="/assets/images/determinant/determinant01.JPG" width="800"></center>
<br />

예를 하나만 더 들어볼께요. (2, 1), (1, 2) 두 벡터로 구성된 행렬을 봅시다. 

$$
\begin{bmatrix}
2 & 1 \\
1 & 2
\end{bmatrix}
$$

이 벡터로 구성된 도형은 평행사변형이네요. 
마찬가지로 행렬식의 절대값은 이 도형의 면적을 의미합니다. 
<br />

<center><img src="/assets/images/determinant/determinant02.JPG" width="800"></center>

### 3. 3 by 3 행렬
위 섹션의 개념을 한 차원 확장시키면 바로 $3 \times 3$ 행렬식의 의미를 파악하실 수 있습니다. 
네, $3 \times 3$ 행렬식의 의미는 3차원 공간에서 해당 행렬 속 벡터들로 구성된 3차원 도형의 부피를 의미합니다. 

### 4. n by n 행렬  
따라서 $n \times n$ 행렬의 행렬식은 n차원 공간의 벡터들로 구성된 도형의 부피라는 것을 알 수 있습니다. 

### 5. 행렬식(determinant)의 의미
앞서 말한 내용을 정리하면 행렬식의 절대값은 '부피'라고 생각할 수 있습니다. 
이 사실로부터 개념을 조금 확장시켜보면, 행렬식이 0이라는 것은 어떤 의미일까요?
행렬을 구성하는 벡터가 영벡터가 아닌데 각 벡터로 구성된 도형의 부피가 0이라는 사실은 
행렬을 구성하는 벡터가 서로 동일선상(colinear)에 있다는 것을 의미합니다. 
이는 행렬의 구성하는 벡터가 해당 공간의 기저가 아님을 의미하는데 
이는 나중에 기저와 차원을 다룰 때 자세히 설명하도록 하겠습니다.
이 개념을 생각하면 행렬식의 여러가지 특징을 이해할 수 있습니다. 
<br />

예를 들어 행렬을 구성하는 행이나 열의 순서를 바꾸어도 행렬식의 절대값은 바뀌지 않습니다.
이는 벡터의 순서를 바꾸어도 공간을 구성하는 벡터의 순서만 바뀔뿐 벡터가 구성하는 도형의 부피는 바뀌지 않기 때문입니다. 
<br />

또한 $det(AB) = det(A)det(B)$ 라는 성질의 의미는 다음과 같습니다. 
행렬 $A$를 선형변환이라고 생각하고 행렬 $B$를 기존의 도형이라고 생각하면 
행렬 $B$를 선형변환했을때의 부피를 $det(AB)$라고 생각할 수 있다고 생각합니다(좌변). 
그럼 우변은 어떨까요? $det(A)$는 선형변환 기저의 부피라고 생각할 수 있고 $det(B)$를 곱함으로써
선형변환 이후의 부피, 즉 좌변과 같아진다고 볼 수도 있을 것 같습니다. 
<br />

마지막으로 위키백과 정의를 다시 보면서 이 글을 마치도록 하겠습니다. 
<br /> 

> 선형대수학에서, 행렬식(determinant)은 정사각행렬에 수를 대응시키는 함수의 하나이다. 
대략, 정사각행렬이 나타내는 선형변환이 부피를 확대시키는 정도를 나타낸다. 

<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>


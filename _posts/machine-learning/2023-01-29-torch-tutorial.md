---
title: "[딥러닝] 파이토치 자세한 튜토리얼" 
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


# 파이토치 튜토리얼



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


## 1. 서론

이번 포스팅에서는 파이토치를 처음 사용하시는 분들을 위한 튜토리얼을 작성해보겠습니다. 
참고로 이번 포스트팅은 [파이토치 공식 튜토리얼](https://tutorials.pytorch.kr/beginner/pytorch_with_examples.html)의 내용을 참고했으며, 해당 내용을 좀더 자세히 풀어썼다고 생각하시면 되겠습니다.   

이번 튜토리얼은 3차 다항식을 이용해 사인(sin) 함수를 추정하는 문제를 다뤄보겠습니다. 
  
  
## 2. 넘파이

먼저 넘파이 라이브러리를 활용해 문제를 풀어보겠습니다. 

### 2.1. 라이브러리 불러오기 및 실제값 생성

```py
import numpy as np
import math
import matplotlib.pyplot as plt

# 추정하고자 하는 실제 곡선
x = np.linspace(-math.pi, math.pi, 2000)
y = np.sin(x)  
```

위와 같은 코드를 작성해줍니다. 위 코드는 라이브러리를 불러오고 우리가 추정하고자 하는 실제 곡선인 sin 함수값을 생성하는 코드입니다. 위 코드로부터 생성된 ```y```값이 실제값이라고 생각하면 되겠습니다.  
  
```py
plt.plot(x, y)
plt.show()
```
<center><img src="/assets/images/dl/torch_tutorial/torch_tutorial01.png" width="800"></center>

앞서 구한 ```y```값을 시각화하면 위 그림과 같이 사인곡선이 나타나는 것을 볼 수 있습니다. 즉, 우리는 3차 다항식을 이용해 위 곡선을 추정하는 것이 목표입니다. 
즉, 위 3차 다항식의 a, b, c, d를 딥러닝을 이용해 추정하는 것입니다.  

### 2.2. 가중치 초기값 생성

```py
# 가중치 초기
a = np.random.randn()
b = np.random.randn()
c = np.random.randn()
d = np.random.randn()
```

다음으로 가중치의 초기값을 정해줍니다. 초기값은 위 코드처럼 랜덤으로 정해줍니다. 
  
```py
>>> print(a, b, c, d)
0.1629 -0.563484 2.5714189 -0.062937
```

앞서만든 초기값을 확인해봅니다.

### 2.3. 학습

```py
# 학습
learning_rate = 1e-6
for t in range(0, 1000):
    y_pred = a + b*x + c*x**2 + d*x**3
    
    ss = np.square(y_pred - y)**0.5
    loss = ss.sum()
    if t%100 == 99:
        print(t, loss)
    
    grad_y_pred = 2.0 * (y_pred - y)
    grad_a = grad_y_pred.sum()
    grad_b = (grad_y_pred*x).sum()
    grad_c = (grad_y_pred*x**2).sum()
    grad_d = (grad_y_pred*x**3).sum()
    
    a -= learning_rate * grad_a
    b -= learning_rate * grad_b
    c -= learning_rate * grad_c
    d -= learning_rate * grad_d
```

위 코드는 학습하는 코드인데, 코드가 길기 때문에 나눠서 보겠습니다. 
  
```py
# 학습
learning_rate = 1e-6
for t in range(0, 1000):
    y_pred = a + b*x + c*x**2 + d*x**3  
```

위 코드에서 ```learning_rate```는 이름 그대로 학습율을 의미합니다. 그리고 반복문을 수행하는데 학습은 1000번 수행하며, 우리가 만든 추정식을 통해 구한 ```y```의 추정값(예측값)을 y_pred라고 이름지어 줍니다. 
  
```py
    ss = np.square(y_pred - y)**0.5
    loss = ss.sum()
    if t%100 == 99:
        print(t, loss)
```

그리고 다음 단계로 비용함수를 정의해주는데, 이번 실습에서 비용함수는 오차제곱합으로 하겠습니다. 따라서 오차제곱합 ss를 통해 구한 손실의 총합이 위 식에서 loss가 되는 것입니다. 
  
```py
    grad_y_pred = 2.0 * (y_pred - y)
    grad_a = grad_y_pred.sum()
    grad_b = (grad_y_pred*x).sum()
    grad_c = (grad_y_pred*x**2).sum()
    grad_d = (grad_y_pred*x**3).sum()
```

그리고 다음으로 그래디언트를 계산해줍니다. 위와 같은 방법으로 코딩하는 이유는 다음과 같습니다. 
  
<center><img src="/assets/images/dl/torch_tutorial/torch_tutorial02.png" width="800"></center>

위 식에서 오차제곱합을 이용해 비용함수를 ```L```로 정의하고 ```a```에 대해 편미분한 값을 이용해 그래디언트를 구할 수 있습니다.  

<center><img src="/assets/images/dl/torch_tutorial/torch_tutorial03.png" width="800"></center>

그리고 나머지 친구들에 대해서도 위와 같이 구할 수 있습니다. 

```py
    a -= learning_rate * grad_a
    b -= learning_rate * grad_b
    c -= learning_rate * grad_c
    d -= learning_rate * grad_d
```

마지막 단계로 가중치를 업데이트 시킵니다. 위 코드는 다음 식을 이용해 작성한 것입니다. 

<center><img src="/assets/images/dl/torch_tutorial/torch_tutorial04.png" width="800"></center>

### 2.4. 학습 결과

학습이 끝나고 최종 학습 결과인 a, b, c, d를 출력하면 다음과 같습니다. 
  
```py
# 학습 결과
>>> print(f"Result: y = {a} + {b} x + {c} x^2 + {d} x^3")
Result: y = -0.04471609 + 0.87041 x + 0.0077142708 x^2 + -0.095275 x^3
```

그리고 실제로 학습이 얼마나 잘 되었는지, 실제 곡선과 추정 곡선을 비교하면 다음과 같습니다. 

```py
plt.plot(x, y, color='blue')
plt.plot(x, y_pred, color='red')
plt.show()
```
<center><img src="/assets/images/dl/torch_tutorial/torch_tutorial05.png" width="800"></center>

### 2.5. 전체 코드
  
```py
# 전체 코드
import numpy as np
import math
import matplotlib.pyplot as plt

# 추정하고자 하는 실제 곡선
x = np.linspace(-math.pi, math.pi, 2000)
y = np.sin(x)

# 가중치 초기
a = np.random.randn()
b = np.random.randn()
c = np.random.randn()
d = np.random.randn()

# 학습
learning_rate = 1e-6
for t in range(0, 1000):
    y_pred = a + b*x + c*x**2 + d*x**3
    
    ss = np.square(y_pred - y)**0.5
    loss = ss.sum()
    if t%100 == 99:
        print(t, loss)
    
    grad_y_pred = 2.0 * (y_pred - y)
    grad_a = grad_y_pred.sum()
    grad_b = (grad_y_pred*x).sum()
    grad_c = (grad_y_pred*x**2).sum()
    grad_d = (grad_y_pred*x**3).sum()
    
    a -= learning_rate * grad_a
    b -= learning_rate * grad_b
    c -= learning_rate * grad_c
    d -= learning_rate * grad_d

# 학습 결과
print(f"Result: y = {a} + {b} x + {c} x^2 + {d} x^3")
```
  

## 3. 파이토치   

위 코드를 파이토치를 이용해 작성하면 다음과 같습니다. 

```py
import torch
import math

dtype = torch.float
device = torch.device('cpu')

x = torch.linspace(-math.pi, math.pi, 2000, device=device, dtype=dtype)
y = torch.sin(x)

a = torch.randn((), device=device, dtype=dtype)
b = torch.randn((), device=device, dtype=dtype)
c = torch.randn((), device=device, dtype=dtype)
d = torch.randn((), device=device, dtype=dtype)

learning_rate = 1e-6
for t in range(2000):
    y_pred = a + b * x + c * x ** 2 + d * x ** 3

    ss = (y_pred - y).pow(2)
    loss = ss.sum().item()
    if t % 100 == 99:
        print(t, loss)

    grad_y_pred = 2.0 * (y_pred - y)
    grad_a = grad_y_pred.sum()
    grad_b = (grad_y_pred * x).sum()
    grad_c = (grad_y_pred * x ** 2).sum()
    grad_d = (grad_y_pred * x ** 3).sum()

    a -= learning_rate * grad_a
    b -= learning_rate * grad_b
    c -= learning_rate * grad_c
    d -= learning_rate * grad_d

print(f'Result: y = {a.item()} + {b.item()} x + {c.item()} x^2 + {d.item()} x^3')
```



<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>

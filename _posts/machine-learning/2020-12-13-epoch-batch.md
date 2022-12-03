---
title: "[딥러닝] 배치 사이즈(batch size) vs 에포크(epoch) vs 반복(iteration)의 차이" 
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

# 배치 사이즈(batch size) vs 에포크(epoch) vs 반복(iteration)의 차이

### 참고링크  

**머신러닝**
* ### [k-means클러스터링 복습하기](https://losskatsu.github.io/machine-learning/kmeans-clustering/)
* #### [k-최근접 이웃 알고리즘 복습하기](https://losskatsu.github.io/machine-learning/knn/)
* [선형회귀분석 복습하기](https://losskatsu.github.io/statistics/simple-regression/)
* [로지스틱 회귀분석 복습하기](https://losskatsu.github.io/statistics/logistic-regression/)
* [릿지, 라쏘 회귀분석 북습하기](https://losskatsu.github.io/machine-learning/l1l2/)
* [의사결정나무 복습하기](https://losskatsu.github.io/machine-learning/decision-tree/)
* [서포트벡터머신 복습하기](https://losskatsu.github.io/machine-learning/svm/)
* [원클래스 SVM 복습하기](https://losskatsu.github.io/machine-learning/oneclass-svm/) 
* [LDA 복습하기](https://losskatsu.github.io/machine-learning/lda/)
* [가우시안 혼합 모형(GMM) 복습하기](https://losskatsu.github.io/machine-learning/gmm/)
* [딥러닝 기초 복습하기](https://losskatsu.github.io/machine-learning/dl-basic01/)
* [부스팅(boosting) 복습하기](https://losskatsu.github.io/machine-learning/boosting/)
* [사이킷런 실습하기](https://losskatsu.github.io/machine-learning/sklearn/)

**딥러닝**
* [딥러닝 기초(1) 신경망이란](https://losskatsu.github.io/machine-learning/dl-basic01/)
* [딥러닝 기초(2) 성능함수란](https://losskatsu.github.io/machine-learning/dl-basic02/)
* [딥러닝 기초(3) 편미분을 이용한 신경망 학습](https://losskatsu.github.io/machine-learning/dl-basic03/)
* [딥러닝 기초(4) 교차연결](https://losskatsu.github.io/machine-learning/dl-basic04/)
* [딥러닝 기초(5) 합성곱 신경망](https://losskatsu.github.io/machine-learning/dl-basic05/)

**모형평가**
* [ROC 커브 복습하기](https://losskatsu.github.io/machine-learning/stat-roc-curve/)
* [교차검증(cross validataion)](https://losskatsu.github.io/machine-learning/cross-validation/)
* [실루엣 스코어](https://losskatsu.github.io/machine-learning/silhouette-score)

**최적화**
* [컨벡스 셋(convex set)](https://losskatsu.github.io/machine-learning/convex-set/)
* [컨벡스 함수(convex function)](https://losskatsu.github.io/machine-learning/convex-function/)
* [라그랑주 듀얼 함수](https://losskatsu.github.io/machine-learning/dual-function/)
* [Karush-Kuhn-Tucker](https://losskatsu.github.io/machine-learning/kkt/)


<br/>

<a href="http://www.yes24.com/Product/Goods/97032765" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00001_ml.png" width="800" align="middle">

<br/>


딥러닝을 하다보며 에포크(epoch), 배치(batch), 반복(iteration)이라는 단어를 많이 접하게 됩니다. 
그런데 이 단어들이 다 비슷비슷한 느낌이라 처음에는 헷갈릴 수 있는데요. 
이번 포스팅에서는 epoch, batch, iteration의 차이에 대해 알아보겠습니다.

## 1. 사전적 의미

먼저 batch 의 사전적 의미를 보겠습니다. 
batch를 영어사전에 검색하면 아래와 같은 뜻이 나옵니다.
batch 는 일괄적이라는 뜻이 포함되네요. 

> batch
>> (일괄적으로 처리되는) 집단, 무리  
>> 한 회분(한 번에 만들어 내는 음식기계 등의 양)   
>> (일괄 처리를 위해) 함께 묶다  

다음은 epoch의 사전적 의미를 보겠습니다. 
epoch는 시대라는 뜻으로 batch와는 조금 다른 느낌이 듭니다. 

> epoch
>> (중요한 사건·변화들이 일어난) 시대 (=era)

마지막으로 iteration을 검색해보겠습니다. 
iteration은 '반복'이라는 뜻으로 흔히 반복문할 때 그 반복이라고 생각하시면 이해가 쉬울 것 같습니다.

> iteration
>> (계산·컴퓨터 처리 절차의) 반복


## 2. batch size의 의미

batch size란 정확히 무엇을 의미할까요? 
전체 트레이닝 데이터 셋을 여러 작은 그룹을 나누었을 때 batch size는 하나의 소그룹에 속하는 데이터 수를 의미합니다. 
전체 트레이닝 셋을 작게 나누는 이유는 트레이닝 데이터를 통째로 신경망에 넣으면 비효율적이 리소스 사용으로 학습 시간이 오래 걸리기 때문입니다. 

<center><img src="/assets/images/dl/epoch/epoch01.jpg" width="800"></center>


## 3. epoch의 의미 

딥러닝에서 epoch는 전체 트레이닝 셋이 신경망을 통과한 횟수 의미합니다. 
예를 들어, 1-epoch는 전체 트레이닝 셋이 하나의 신경망에 적용되어 순전파와 역전파를 통해 신경망을 한 번 통과했다는 것을 의미합니다. 

<center><img src="/assets/images/dl/epoch/epoch02.jpg" width="800"></center>


## 4. iteration의 의미

마지막으로 iteration은 1-epoch를 마치는데 필요한 미니배치 갯수를 의미합니다. 
다른 말로, 1-epoch를 마치는데 필요한 파라미터 업데이트 횟수 이기도 합니다. 
각 미니 배치 마다 파라미터 업데이터가 한번씩 진행되므로 iteration은 파라미터 업데이트 횟수이자 미니배치 갯수입니다. 
예를 들어, 700개의 데이터를 100개씩 7개의 미니배치로 나누었을때, 
1-epoch를 위해서는 7-iteration이 필요하며 7번의 파라미터 업데이트가 진행됩니다. 


<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>

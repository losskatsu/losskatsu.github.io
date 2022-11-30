---
title: "[머신러닝] 비지도학습 - One Class SVM" 
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


# 비지도학습 - One Class SVM(One Class Support Vector Machine)


### 참고링크  

**머신러닝**
* [k-means클러스터링 복습하기](https://losskatsu.github.io/machine-learning/kmeans-clustering/)
* [k-최근접 이웃 알고리즘 복습하기](https://losskatsu.github.io/machine-learning/knn/)
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


## 1. SVM 복습

우리는 지도학습 알고리즘 중 서포트 벡터 머신(support vector machine, 이하 SVM)이라는 
알고리즘을 배웠습니다. 서포트 벡터 머신은 지도학습 알고리즘이므로 라벨링이 되어 있는 데이터를 
대상으로 학습하는 알고리즘 입니다. 
그리고 [SVM 포스팅](https://losskatsu.github.io/machine-learning/svm/)에서도 알 수 있듯, 
SVM의 핵심 개념은 서포트 벡터를 이용해 분류하는 것이었습니다. 

## 2. One Class SVM

반면 이번 포스팅에서 알아볼 One Class SVM(one class support vector machine)은 
비지도학습 알고리즘 중 하나입니다. 즉, one class svm은 서포트 벡터 개념을 이용해 
라벨링되어 있지 않은 데이터를 클러스터링 하는 방법입니다.  

이번 포스팅에서는 비지도학습에 사용되는 One Class SVM에 대해 알아보겠습니다. 

<center><img src="/assets/images/ml/oneclass-svm/ocsvm01.png" width="500"></center>

기본적인 서포트 벡터 머신과 마찬가지로 one class svm 또한 위와 같은 식을 최적화 하는 방식입니다. 
위 식에서 $\phi (x)$는 새로운 피처 공간에서의 데이터를 의미합니다. 

<center><img src="/assets/images/ml/oneclass-svm/ocsvm02.png" width="800"></center>

그리고 라그랑주 프리멀 함수를 구하면 위와 같이 구할 수 있고, 
각각의 파라미터로 편미분하면 다음과 같은 결과를 구할 수 있습니다. 

<center><img src="/assets/images/ml/oneclass-svm/ocsvm03.png" width="800"></center>


위에서 구한 최적해를 다음 그림과 같이 원래 라그랑주 프리멀 함수에 넣습니다. 

<center><img src="/assets/images/ml/oneclass-svm/ocsvm04.png" width="800"></center>

앞서 구한 최적해 $w$를 라그랑주 프리멀 함수에 넣고 풀면 다음과 같이 라그랑주 듀얼 함수를 구할 수 있습니다. 

<center><img src="/assets/images/ml/oneclass-svm/ocsvm05.png" width="800"></center>

위 식에서 마지막 줄이 정리된 라그랑주 듀얼 함수인데, 
이 식의 코어 함수만 남기면 다음과 같은 식을 최소화하는 것이 목적이라고 할 수 있습니다. 

<center><img src="/assets/images/ml/oneclass-svm/ocsvm06.png" width="800"></center>

즉, one class svm의 최종 목적은 위 식을 조건을 만족하는 최적해를 찾는 것입니다. 



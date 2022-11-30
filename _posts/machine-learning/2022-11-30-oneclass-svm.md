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


## 1. 서론

이번 포스팅에서는 비지도학습에 사용되는 One Class SVM에 대해 알아보겠습니다. 

<center><img src="/assets/images/ml/oneclass-svm/ocsvm01.png" width="800"></center>

<center><img src="/assets/images/ml/oneclass-svm/ocsvm02.png" width="800"></center>


<center><img src="/assets/images/ml/oneclass-svm/ocsvm03.png" width="800"></center>


<center><img src="/assets/images/ml/oneclass-svm/ocsvm04.png" width="800"></center>


<center><img src="/assets/images/ml/oneclass-svm/ocsvm05.png" width="800"></center>


<center><img src="/assets/images/ml/oneclass-svm/ocsvm06.png" width="800"></center>




---
title: "[머신러닝] 이상치 분석 성능 평가에 실루엣 스코어를 사용하는 이유" 
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


# 이상치 분석 성능 평가에 실루엣 스코어를 사용하는 이유


## 1. 서론

PCA 혹은 One class SVM과 같은 방법을 통해 이상치 분석을 할떄는 실루엣 스코어(silouette score)라는 성능 평가 지표를 사용합니다. 
어떻게 이상치 분석 성능지표로 실루엣 스코어를 사용하는게 가능한 것일까요?


## 2. 실루엣 스코어의 개념

실루엣 방법은 최적화된 클러스터 갯수를 찾는데 사용되며 
또한 데이터 클러스터 내부에 존재하는 데이터 포인트들 간 일관성(consistency)의 타당성을 평가하는데 사용됩니다. 
실루엣 방법은 각 데이터 포인트의 실루엣 계수(silouette coefficient)를 계산합니다. 
이때 실루엣 계수가 의미하는 것은 해당 데이터 포인트가 본인이 속한 클러스터가 다른 클러스터에 비해 얼마나 유사한지를 측정합니다. 
즉, 간단하게 말해서 얼마나 분류가 잘 되었는지를 말해주는 것이죠. 


## 3. 실루엣 스코어의 값의 범위

실루엣 스코어(silouette score)는 -1부터 1사이의 값을 가지는데 특정 값이 의미하는 것은 다음과 같습니다. 
우선 실루엣 스코어가 +1이라는 뜻은 해당 샘플이 이웃한 클러스터로부터 멀리 떨어져있다는 것을 의미합니다. 
즉, 실루엣 스코어가 +1이라는 것은 클러스터링이 확실하게 잘되었다는 것을 의미하죠. 
왜냐면 클러스터끼리 멀리 떨어져 있으니까요.

실루엣 스코어가 0이라는 것은 해당 샘플 데이터가 이웃한 클러스터와 매우 가까이 붙어 있다는 것을 의미합니다. 
그리고 실루엣 스코어가 0보다 작다는 것은 해당 샘플 데이터가 잘못된 클러스터에 속해있는 것을 의미합니다. 

## 4. 실루엣 스코어 계산 과정

<center><img src="/assets/images/ml/silouette/silouette01.png" width="800"></center>

<center><img src="/assets/images/ml/silouette/silouette02.png" width="800"></center>

<center><img src="/assets/images/ml/silouette/silouette03.png" width="800"></center>

<center><img src="/assets/images/ml/silouette/silouette04.png" width="800"></center>

<center><img src="/assets/images/ml/silouette/silouette05.png" width="800"></center>

<center><img src="/assets/images/ml/silouette/silouette06.png" width="800"></center>

<center><img src="/assets/images/ml/silouette/silouette07.png" width="800"></center>






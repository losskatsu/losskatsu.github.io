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


## 서론

PCA 혹은 One class SVM과 같은 방법을 통해 이상치 분석을 할떄는 실루엣 스코어(silouette score)라는 성능 평가 지표를 사용합니다. 
어떻게 이상치 분석 성능지표로 실루엣 스코어를 사용하는게 가능한 것일까요?


## 실루엣 스코어의 개념

실루엣 방법은 최적화된 클러스터 갯수를 찾는데 사용되며 
또한 데이터 클러스터 내부에 존재하는 데이터 포인트들 간 일관성(consistency)의 타당성을 평가하는데 사용됩니다. 
실루엣 방법은 각 데이터 포인트의 실루엣 계수(silouette coefficient)를 계산합니다. 
이때 실루엣 계수가 의미하는 것은 해당 데이터 포인트가 본인이 속한 클러스터가 다른 클러스터에 비해 얼마나 유사한지를 측정합니다. 
즉, 간단하게 말해서 얼마나 분류가 잘 되었는지를 말해주는 것이죠. 


## 실루엣 스코어의 값의 범위

실루엣 스코어는 -1부터 1사이의 값을 가지는데 



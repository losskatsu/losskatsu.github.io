---
title: "[머신러닝] 파이썬 데이터 시각화 matplotlib 기초 예제" 
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


# 파이썬 시각화 matplotlib 기초 예제

파이썬으로 데이터 시각화를 하기 위해선 여러가지 시각화 라이브러리를 사용할 수 있습니다. 
그중에서 유명한 것이 matplotlib, seaborn 인데요, 
오늘은 matplotlib 라이브러리를 이용한 파이썬 시각화 기초 예제를 살펴보겠습니다. 

## 라이브러리 불러오기

```python
## 내장 데이터 불러오기 용
from sklearn import datasets

## 시각화 라이브러리
import matplotlib.pyplot as plt
```

## 시각화할 데이터 불로오기

예제에 쓰일 데이터를 불러오기 위해 사이킷런(sklearn)에 내장 되어있는 데이터를 불러오겠습니다. 

```python
raw = datasets.load_breast_cancer()
print(raw.feature_names)
data = pd.DataFrame(raw.data)
target = pd.DataFrame(raw.target)
rawData = pd.concat([data,target], axis=1)
rawData.columns=['mean radius', 'mean texture', 
                 'mean perimeter', 'mean area',
 'mean smoothness', 'mean compactness', 'mean concavity',
 'mean concave points', 'mean symmetry', 'mean fractal dimension',
 'radius error', 'texture error', 'perimeter error', 'area error',
 'smoothness error', 'compactness error', 'concavity error',
 'concave points error', 'symmetry error', 'fractal dimension error',
 'worst radius', 'worst texture', 'worst perimeter', 'worst area',
 'worst smoothness', 'worst compactness', 'worst concavity',
 'worst concave points', 'worst symmetry', 
 'worst fractal dimension', 'cancer']
```

## 산점도

### 기본 산점도 

```python
plt.scatter(rawData['mean radius'], rawData['mean texture'])
plt.xlabel('radius')
plt.ylabel('texture')
plt.title('radius vs texture')
plt.show()
```
<center><img src="/assets/images/ml/visualization/visualization01.png" width=500></center>

### 중첩 산점도

```python
plt.scatter(rawData['mean radius'], rawData['mean texture'], c='blue')
plt.scatter(rawData['worst radius'], rawData['worst texture'], c='red')
plt.xlabel('radius')
plt.ylabel('texture')
plt.title('mean vs worst')
plt.legend(['mean','worst'])
plt.show()
```
<center><img src="/assets/images/ml/visualization/visualization02.png" width=500></center>

## 히스토그램

```python
plt.hist(rawData['cancer'], bins=2, 
            range=(0,1),edgecolor='black', linewidth=1.2)
plt.show()
```
<center><img src="/assets/images/ml/visualization/visualization03.png" width=500></center>

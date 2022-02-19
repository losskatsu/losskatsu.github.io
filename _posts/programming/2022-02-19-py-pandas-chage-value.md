---
title: "[python] 판다스에서 특정 컬럼에 속한 값 원하는 값으로 바꾸기 " 
categories:
  - programming
tags:
  - programming
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# [python] 판다스에서 특정 컬럼에 속한 값 원하는 값으로 바꾸기

**참고링크** 

* [판다스 iloc, loc 차이](https://losskatsu.github.io/programming/py-pandas-iloc/)

## 판다스에서 데이터 불러오기

```py
import pandas as pd
df = pd.read_csv("./data/stella/star_classification_origin.csv")
df
```

## 해당 컬럼에서 유니크 값 확인

```py
df['class'].unique()
```
```
array(['GALAXY', 'QSO', 'STAR'], dtype=object)
```


## 해당 컬럼에서 조건에 맞는 값 바꾸기

```py
df.loc[(df['class']=='GALAXY'), 'class']=0
df.loc[(df['class']=='QSO'), 'class']=1
df.loc[(df['class']=='STAR'), 'class']=2
df
```

## 바뀐 값 확인

```py
df['class'].unique()
```
```
array([0, 1, 2], dtype=object)
```

---
title: "자료구조, 알고리즘 간단 요약" 
categories:
  - Programming
tags:
  - Programming
  - Algorithm
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

## 자료구조 알고리즘 요약

### 1. 리스트(list)

* 데이터(data), 포인터(pointer)로 구성
* 리스트는 데이터가 메모리상에서 연속된 위치에 저장 되지 않아도 되며, 일반적으로 서로 떨어진 영역에 흩어져서 저장됨. 
이것으로 Spark를 사용할 때 dataframe이 왜 리스트 형식인지 추측할 수 있다. 
* 데이터가 흩어져 있으므로 중간에 놓여있는 데이터에 접근하고 싶은 경우 첫 포인터부터 순서대로 따라가야함.
* 데이터 추가, 삭제 시에는 앞뒤 포인터를 변경하기만 하면 되기 때문에 간단함.
* 요약 : 데이터 접근 시에는 시간이 오래걸리지만, 데이터 추가, 삭제는 빠른 시간에 가능.



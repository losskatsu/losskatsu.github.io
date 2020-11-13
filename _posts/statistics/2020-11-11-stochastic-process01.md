---
title: "확률과정론(stochastic process)(1)" 
categories:
  - statistics
tags:
  - statistics
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 확률과정론(stochastic process)(1)

본 포스팅은 [MIT 강의](https://www.youtube.com/watch?v=TuTmC8aOQJE&ab_channel=MITOpenCourseWare)를 참고로 작성했습니다. 

## 1. 확률과정이란

확률과정(stochastic process)란 시계열 랜덤변수의 집합입니다. 
시계열 랜덤변수란 랜덤변수가 시간(time)으로 인덱싱 되어 있는 것을 말합니다. 

$ \{X_t\}_{t\geq 0}\: X_0, X_1, X_2, X_3, ... $   

이때 변수는 이산형일수도 있고 연속형일수도 있습니다. 
확률과정을 다르게 정의하면 지나온 경로에 대한 확률 분포라고 할 수도 있습니다. 

---
title: "몬테카를로 시뮬레이션(monte carlo simulation) 요약" 
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

# 몬테카를로 시뮬레이션(monte carlo simulation) 요약

본 포스팅은 [MIT 강의](https://www.youtube.com/watch?v=OgO1gpXSUzU&ab_channel=MITOpenCourseWare)를 참고했습니다. 

## 1. 몬테카를로 시뮬레이션의 역사

한 수학자가 살고 있었습니다. 
그는 몸이 아팠을 때 도박을 했었는데, 자신이 도박에서 이길 확률을 추정하고 싶었습니다. 
그래서 몸소 주사위를 계~속 던지며 무한 반복을 하면서 확률을 추정했습니다. 
자신이 직접 경험 하면서요. 
근데 본인이 계속 주사위를 던지다보니 너무 힘든 겁니다. 
그래서 내가 직접 게임을 계속하기보다는 컴퓨터로 시뮬레이션을 해보자라는 생각을 하게 됩니다. 
그런데 그는 컴퓨터를 잘 몰랐기에 친구였던 폰 노이만에게 에니악으로 시뮬레이션을 돌려달라고 합니다. 
이것이 몬테카를로 시뮬레이션(Monte Carlo Simulation)의 탄생 이야기 입니다. 
몬테카를로 시뮬레이션은 카드 게임 뿐만이 아니라 수소폭탄 설계에도 쓰입니다. 

## 2. 몬테카를로 시뮬레이션의 정의

몬테카를로 시뮬레이션이란 알려지지 않은 값을 추론적 통계(inferential statistics)방법을 이용해 추정하는 것을 의미합니다. 

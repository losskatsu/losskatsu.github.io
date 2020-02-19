---
title: "[기초통계] 초기하분포 의미 및 개념 정리" 
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

# 초기하분포 의미 및 개념 정리

## 1. 초기하분포 정의

> 초기하분포(hypergeometric distribution)란 비복원추출에서 N개 중에 M개가 원하는 것이고, K번 추출했을때 원하는 것 x개가 뽑힐 확률의 분포이다. 

![figure01](/assets/images/statistics/hypergeometric/hypergeometric01.jpg){: width="500"}


## 2. 복원추출/비복원추출이란

항아리에 5개의 공이 들어있고 그 중 하나씩 뽑는 상황을 가정해봅시다. 
복원추출이란 항아리에서 공을 뽑은 이후 다음 공을 뽑기 전에 이전에 뽑은 공을 다시 항아리속으로 집어넣는 것이고, 
비복원추출이란 한번 공을 뽑으면 다시 공을 집어넣지 않고 다음 공을 뽑는 것입니다. 
이 둘은 얼핏차이 없어보이지만 큰 차이가 있습니다. 
항아리에 공이 5개 있으므로 비복원추출의 경우 뽑을 수 있는 최대 횟수가 5회입니다. 즉 뽑을수있는 횟수에 제한이 있다는 뜻이죠. 
반면 복원추출을 할 경우 공을 뽑은 후 다시 항아리속에 넣기 때문에 뽑을 수 있는 횟수가 무한대입니다. 
즉, 뽑을 수 있는 횟수가 무제한이라는 것입니다. 


## 3. 이항분포와의 관계 

따라서 비복원추출을 가정하는 상황에서는 초기하분포를 사용해야하며, 
복원추출을 가정하는 상황에서는 이항분포를 사용해야 합니다. 


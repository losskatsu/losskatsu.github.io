---
title: "확률적 사고 방식" 
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

# 확률적 사고 방식(stochastic thinking)

본 포스팅은 [MIT 강의](https://www.youtube.com/watch?v=-1BnXEwHUok&t=505s&ab_channel=MITOpenCourseWare)를 참고로 작성했습니다. 

## 1. 역사

동일한 인풋을 넣었을 때 동일한 아웃풋이 나오는 경우, 이 경우를 예측가능(predictable)하다라고 말합니다. 
하지만 실제 우리가 살고 있는 세계는 불확실한 상황이 많기 때문에 예측가능한 프로그래밍은 도움이 안될때가 많습니다. 
예전에 뉴턴역학이 처음 등장했을 때, "사과가 나무에서 떨어지는 것은 중력 때문이다"라는 문장처럼 
이 세계를 명확히 설명할수 있는 것 처럼 보였습니다. 
하지만 시간이 흘러 20세기초, 하이젠베르크는 causal nondeterminism이라는 것을 발표하게 됩니다. 
이는 아주 밑바닥, 근본적인 레벨에서 실제 물리 세계는 예측할 수 없다는 의미입니다. 
즉, 사건이 발생할 것이다라고 예측할순 있어도, 100% 확신할 수는 없다는 의미입니다. 확률이 1이 될 순 없다는 뜻이죠. 
그리고 아인슈타인은 하이젠베르크의 주장을 반대하면서 "신은 주사위 놀이를 하지 않는다"라는 명언을 남겼습니다. 

## 2. 서론

이제 본격적으로 예를 들면서 시작해봅시다. 
두개의 동전을 섞은 후 바닥에 뒤집어 놓는다고 가정해봅시다. 

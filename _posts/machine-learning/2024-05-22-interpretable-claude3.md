---
title: "[딥러닝] Large Language Model(claude3) 작동원리 논문 번역" 
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


# arge Language Model(claude3) 작동원리 논문 번역

원본 논문: [Scaling Monosemanticity: Extracting Interpretable Features from Claude3 Sonnet](https://transformer-circuits.pub/2024/scaling-monosemanticity/index.html)

## 0. Abstract

8개월 전, 우리는 sparse 오토인코더가 작은 one-layer 트랜스포머로부터 단일의미적(monosemantic) 피처를 복구시킬 수 있다는 점을 증명했다. 
그 당시에 이 방법에 대해 주요 이슈는 최첨단 트랜스포머로 확장되기 어렵고, 그 결과 AI 안전에 실질적으로 기여하기는 어려울 것이라는 점이었다. 
그 이후, sparse 오토인코더를 확장시키는 것이 Anthropic interpretability 팀의 주요과제가 되었고, 
Claude 3 Sonnet, 1 Anthropic's 미디움 사이즈 프로덕션 모델로 부터 높은 퀄리티의 피처를 추출하는데 성공했다는 보고를 하게 되어 기쁘다.  

우리는 고도로 추상적인 피처의 다양성을 발견했다. 





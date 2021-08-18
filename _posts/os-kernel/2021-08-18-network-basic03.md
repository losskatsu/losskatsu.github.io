---
title: "네트워크 기초(3) - OSI 7계층 - 2계층: 데이터 링크 계층" 
categories:
  - os-kernel
tags:
  - os
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 네트워크 기초(3) - OSI 7계층 - 2계층: 데이터 링크 계층

**참고 링크**

* [네트워크 기초(1) - OSI 7계층이란?](https://losskatsu.github.io/os-kernel/network-basic01/)
* [네트워크 기초(2) - 1계층: 물리계층](https://losskatsu.github.io/os-kernel/network-basic02/)


## 1. 이더넷(Ethernet)

데이터 링크 계층은 네트워크 장비 사이의 신호를 주고 받는 규칙을 정하는 층입니다. 
아마 네트워크 공부하시면서 이더넷(Ethernet)이라는 단어를 들어보신 적이 있으실 건데요.
바로 이 이더넷이 랜(LAN)에 적용되는 규칙입니다. 
랜(LAN)은 local area network를 의미합니다. 

<center><img src="/assets/images/os/network-basic/network02.jpg" width="800"></center>

이더넷은 앞서 배웠던 허브와 같은 장비를 이용해 데이터를 주고 받을 때 사용하는 규칙입니다. 

<center><img src="/assets/images/os/network-basic/network07.jpg" width="800"></center>

허브는 [물리 계층](https://losskatsu.github.io/os-kernel/network-basic02/)을 다룰 때 배웠던 것 처럼 
특정 컴퓨터에만 데이터를 보내려고 해도 나머지 컴퓨터에게 모두 데이터가 전달된다는 특징이 있었습니다. 
그런데 보낼 때 보내더라도 목적지 이외의 컴퓨터는 데이터를 받아도 무시합니다. 
위 그림으로 예를 들면 컴퓨터 1이 컴퓨터 4에게 데이터를 보내면, 
컴퓨터 4는 데이터를 확인하지만 컴퓨터 2, 컴퓨터 3은 데이터를 받아도 무시합니다. 

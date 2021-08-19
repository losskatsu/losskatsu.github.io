---
title: "네트워크 기초(4) - OSI 7계층 - 3계층: 네트워크 계층" 
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

# 네트워크 기초(4) - OSI 7계층 - 3계층: 네트워크 계층

**참고 링크**

* [네트워크 기초(1) - OSI 7계층이란?](https://losskatsu.github.io/os-kernel/network-basic01/)
* [네트워크 기초(2) - 1계층: 물리계층](https://losskatsu.github.io/os-kernel/network-basic02/)
* [네트워크 기초(3) - 2계층: 데이터 링크 계층](https://losskatsu.github.io/os-kernel/network-basic03/)
* [네트워크 기초(4) - 3계층: 네트워크 계층](https://losskatsu.github.io/os-kernel/network-basic04/)


## 1. 스위치 너머 저편으로

이번 포스팅에서는 OSI 7계층 중 3계층에 해당하는 네트워크 계층에 대해 알아보겠습니다. 

<center><img src="/assets/images/os/network-basic/network02.jpg" width="800"></center>

앞서 [데이터 링크 계층](https://losskatsu.github.io/os-kernel/network-basic03/)에서는 스위치라는 장비를 이용해 스위치에 연결되어 있는 
컴퓨터끼리 이더넷이라는 규칙하에 프레임을 주고 받았습니다. 
그러나 이러한 방법으로는 동일한 스위치에 연결되어 있는 컴퓨터끼리만 데이터를 전송할수 있습니다. 
즉, 스위치 너머에 있는 다른 네트워크로는 데이터를 전송할 수 없습니다. 

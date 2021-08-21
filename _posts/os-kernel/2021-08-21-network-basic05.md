---
title: "네트워크 기초(5) - OSI 7계층 - 4계층: 전송 계층" 
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

# 네트워크 기초(5) - OSI 7계층 - 4계층: 전송 계층

**참고 링크**

* [네트워크 기초(1) - OSI 7계층이란?](https://losskatsu.github.io/os-kernel/network-basic01/)
* [네트워크 기초(2) - 1계층: 물리계층](https://losskatsu.github.io/os-kernel/network-basic02/)
* [네트워크 기초(3) - 2계층: 데이터 링크 계층](https://losskatsu.github.io/os-kernel/network-basic03/)
* [네트워크 기초(4) - 3계층: 네트워크 계층](https://losskatsu.github.io/os-kernel/network-basic04/)


## 1. 신뢰성

이번 포스팅에서는 OSI 7계층 중 4계층에 해당하는 전송 계층에 대해 알아보겠습니다. 

<center><img src="/assets/images/os/network-basic/network02.jpg" width="800"></center>

지금까지 배운것을 잠시 복습해보면 다른 컴퓨터에 데이터를 전송하기 위해 
1계층에서는 허브, 2계층에서는 스위치, 3계층에서는 라우터가 필요했습니다. 
그런데 이렇게 데이터를 보내는것 까진 좋은데 데이터가 잘 전송되었는지, 
아니면 중간에 사고가 발생해 데이터 전송에 문제가 생겼는지는 알아야하지 않을까요? 
지금까지 배웠던 1,2,3계층만을 이용하면 이 문제를 해결할 수 없습니다. 
그래서 등장하는 것이 이번에 배울 전송 계층(Transport Layer)입니다. 

## 2. 전송 계층의 역할

전송 계층은 2가지 역할을 수행합니다. 
첫 번째로 3계층인 네트워크 계층이 데이터를 전달할 때 4계층인 전송 계층은 데이터가 제대로 도착했는지 확인을 합니다. 
또한 데이터가 최종적으로 도착할 애플리케이션이 무엇인지 식별하는 기능도 있습니다.

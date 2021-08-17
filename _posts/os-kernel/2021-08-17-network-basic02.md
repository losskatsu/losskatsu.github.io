---
title: "네트워크 기초(2) - OSI 7계층 - 1계층: 물리 계층" 
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

# 네트워크 기초(2) - OSI 7계층 - 1계층: 물리 계층



## 1. 서론

물리 계층은 OSI 7계층 중에 1계층에 해당합니다. 


## 2. 전기 신호

네트워크 통신에서는 숫자 0과 1만 사용합니다. 
즉, 우리가 전송하고자 하는 데이터는 모두 0과 1로 변환되어 전송됩니다. 
그렇다면 데이터를 0과 1로 이루어진 비트열로 변환만 하면 전송할 수 있을까요? 
아닙니다. 이렇게 변환한 0과 1을 다시 전기 신호로 변환 해야합니다. 
이렇게 전기 신호로 변환한 후 상대 컴퓨터 전송 할 수 있습니다. 
그리고 상대 컴퓨터는 전기 신호를 받고 다시 0과 1로 변환하는 과정을 거칩니다. 


<center><img src="/assets/images/os/network-basic/network04.jpg" width="800"></center>

## 3. 랜(LAN) 카드

컴퓨터에 꼽혀있는 랜카드를 본적이 있으실 겁니다. 
랜카드는 인터넷을 사용하기 위해 필요한 랜 케이블을 꼽는 곳입니다. 


## 4. 리피터(repeater)



<center><img src="/assets/images/os/network-basic/network05.jpg" width="800"></center>

## 5. 허브(hub)


<center><img src="/assets/images/os/network-basic/network06.jpg" width="800"></center>

<center><img src="/assets/images/os/network-basic/network07.jpg" width="800"></center>


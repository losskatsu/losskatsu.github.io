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
* [네트워크 기초(3) - 2계층: 데이터 링크 계층](https://losskatsu.github.io/os-kernel/network-basic03/)

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


## 2. CSMA/CD

허브에 연결된 컴퓨터들끼리 통신 하는 경우를 다시 생각해 보겠습니다. 
이 경우, 서로 다른 컴퓨터가 동시에 데이터를 전송하려고 하면 어떻게 될까요? 

< 충돌 그림 >

만약 서로 다른 컴퓨터가 동시에 데이터를 전송하려고 하면 데이터가 동시에 케이블을 지나가게 되고, 
이렇게 되면 충돌이 날 수 있습니다. 
따라서 이런 충돌을 방지하기 위해 어느 한쪽이 다른 한쪽에서 데이터를 다 전송할때까지 기다려야 되는데요. 
즉, 케이블에 빈자리가 날때 까지 기다리는 것입니다. 

<csma 그림>

이와 같은 방법을 CSMA/CD(Carrier Sense Multiple Access with Collision Detection)라고 합니다. 
우리말로 CSMA/CD를 바꾸면 '반송파 감지 다중 접속 및 충돌 탐지' 정도가 되겠습니다. 
이를 더 쉽게 말하면 '대충 알아서 눈치것 통신하자' 정도가 되겠습니다. 

하지만 스위치라는 장비가 생기면서 CSMA/CD도 현재는 거의 사용하지 않는 기술 입니다. 


## 3. MAC 주소

앞서 [물리 계층](https://losskatsu.github.io/os-kernel/network-basic02/)에서 랜카드에 대해 배웠습니다. 
랜카드는 0과 1로 구성된 데이터를 전기신호로 바꾸는 역할을 한다고 했습니다. 
그런데 이 랜카드에는 MAC주소라는 번호가 할당되어 있습니다. 
사람으로 치면 주민등록번호인데요. 즉, MAC주소가 다르면 서로 다른 랜카드이며, 
동일한 주민등록번호를 가진 사림이 없듯이 동일한 MAC주소를 가진 랜카드는 없습니다. 
즉, 모든 랜카드의 MAC주소는 서로 다른 것입니다.  

<맥주소 그림>

MAC주소는 48비트 숫자로 구성되어 있으며 앞 24비트는 랜카드 제조사 번호이며, 
뒤 24비트는 해당 랜카드 제조사가 랜카드에 붙인 번호 입니다. 

<맥주소 할당받은 컴터 그림>


<이더넷 헤더 그림>

## 4. 스위치




## 5. ARP(Address Resolution Protocol)



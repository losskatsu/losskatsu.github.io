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

<center><img src="/assets/images/os/network-basic/network08.jpg" width="800"></center>

만약 서로 다른 컴퓨터가 동시에 데이터를 전송하려고 하면 데이터가 동시에 케이블을 지나가게 되고, 
이렇게 되면 충돌이 날 수 있습니다. 
따라서 이런 충돌을 방지하기 위해 어느 한쪽이 다른 한쪽에서 데이터를 다 전송할때까지 기다려야 되는데요. 
즉, 케이블에 빈자리가 날때 까지 기다리는 것입니다. 

<center><img src="/assets/images/os/network-basic/network09.jpg" width="800"></center>

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

<center><img src="/assets/images/os/network-basic/network10.jpg" width="800"></center>

MAC주소는 48비트 숫자로 구성되어 있으며 앞 24비트는 랜카드 제조사 번호이며, 
뒤 24비트는 해당 랜카드 제조사가 랜카드에 붙인 번호 입니다.  

앞서 우리는 데이터를 전송할 때 7계층부터 1계층으로 내려오면서 헤더를 붙인다고 배웠습니다. 
데이터링크 층에서는 이더넷 헤더와 트레일러가 붙는데 먼저 이더넷 헤더부터 알아봅니다. 

<center><img src="/assets/images/os/network-basic/network11.jpg" width="800"></center>

이더넷 헤더는 목적지 MAC주소(6바이트), 출발지 MAC 주소(6바이트), 유형(2바이트) 다 합쳐서 14바이트로 구성되어 있습니다. 
이 때 유형은 프로토콜을 나타냅니다. 프로토콜의 종류에는 IPv4, ARP, IPv6 등이 있습니다. 
그리고 트레일러는 FCS(Frame Check Sequence)라고도 부르며 데이터 전송 중 오류가 발생하는지 확인하는 용도입니다. 
따라서 위 그림처럼 이더넷 헤더, 데이터, 트레일러를 합친 것을 프레임(frame)이라고 부릅니다. 
즉, 네트워크 케이블을 통해 프레임이 전송되는 것입니다. 



## 4. 스위치


이번에는 스위치(switch)에 대해 배우겠습니다. 
앞서 허브(hub)가 1계층 장비였다면 이번에 배울 스위치(switch)는 2계층인 데이터 링크 계층에서 동작하는 장비 입니다. 

스위치에는 중요한 특징이 있습니다. 
허브와는 다르게 스위치 내부에는 MAC 주소 테이블(MAC address table)이 존재합니다. 
MAC 주소 테이블은 스위치의 포트 번호와 해당 포트에 연결되어 있는 컴퓨터의 MAC 주소가 등록되어 있는 데이터베이스 입니다. 

## 4.1. 맥 주소 테이블

그런데 스위치 내부의 맥 주소 테이블은 누가 작성하는 것일까요? 
이는 스위치 자체적으로 MAC 주소를 등록합니다. 
이번에는 스위치가 MAC 주소 테이블을 작성하는 과정을 알아봅니다. 

<center><img src="/assets/images/os/network-basic/network12.jpg" width="800"></center>

먼저 스위치(switch)를 사서 연결했다고 하겠습니다. 
아직까지는 아무런 통신을 하지 않았습니다. 
따라서 맥 주소 테이블은 비어 있습니다. 

<center><img src="/assets/images/os/network-basic/network13.jpg" width="800"></center>

이 때 컴퓨터 1이 컴퓨터 3으로 데이터를 전송한다고 하겠습니다. 
이 때 데이터는 스위치를 거치게 되는데 이때 MAC 주소 테이블에 컴퓨터1의 맥주소가 추가됩니다. 

## 4.2. 플러딩(flooding)

자, 그런데 우리는 아직 포트1이 컴퓨터1의 맥주소와 연결되어 있다는 사실 밖에 모릅니다. 
즉, 출발지만 알고 도착지를 모르는거죠. 추리는 컴퓨터 3으로 데이터를 보내야하는데 목적지 맥주소를 모르니 어떻게 해야할까요?

<center><img src="/assets/images/os/network-basic/network14.jpg" width="800"></center>

위 그림처럼 도착지 주소가 아직 맥 주소 테이블에 등록되지 않은 경우 출발지를 제외한 나머지 포트에 연결된 컴퓨터에 모두 
데이터(프레임)가 전송됩니다. 이를 플러딩(flooding)이라고 부릅니다. 
플러딩은 출발지를 제외한 스위치에 연결된 나머지 모두에게 데이터를 전송하는 것이라고 생각하면 편합니다.

## 4.3. MAC 주소가 등록되어 있을때

앞서서는 도착지 맥 주소가 스위치의 맥 주소 테이블에 등록되지 않은 경우, 플러딩을 하게 된다고 배웠습니다. 
이번에는 스위치 맥 주소 테이블에 우리가 원하는 목적지 맥 주소가 등록되어 있는 경우를 보겠습니다. 

<center><img src="/assets/images/os/network-basic/network15.jpg" width="800"></center> 

스위치 맥주소 테이블에 목적지 맥주소가 등록되어 있는 경우는 간단합니다. 
위 그림처럼 목적지에만 데이터를 전송하고 나머지 컴퓨터에는 데이터를 전송하지 않습니다. 
이것이 자신을 제외한 나머지 컴퓨터 모두에게 데이터를 전송하는 [허브(hub)](https://losskatsu.github.io/os-kernel/network-basic02/)와의 차이점 입니다.

## 5. ARP(Address Resolution Protocol)

ARP(Address Resolution Protocol)는 목적지 컴퓨터의 IP 주소를 활용해 MAC 주소를 찾기 위한 프로토콜 입니다. 
이더넷 프레임을 전송하려면 목적지 컴퓨터의 MAC 주소를 지정해야합니다. 

따라서 출발지 컴퓨터가 목적지 컴퓨터의 MAC 주소를 모르면 이를 알아내기 위해 
브로드캐스팅(broadcasting)를 하는데 이를 ARP 요청이라고 합니다. 
이 때 브로드캐스팅이란 네트워크 상에 연결된 모든 컴퓨터들에게 요청하는 것을 의미합니다. 

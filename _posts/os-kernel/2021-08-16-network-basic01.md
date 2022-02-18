---
title: "네트워크 기초(1) - OSI 7계층이란?" 
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

# 네트워크 기초(1) - OSI 7계층이란?


**참고 링크**

* [네트워크 기초(1) - OSI 7계층이란?](https://losskatsu.github.io/os-kernel/network-basic01/)
* [네트워크 기초(2) - 1계층: 물리계층](https://losskatsu.github.io/os-kernel/network-basic02/)
* [네트워크 기초(3) - 2계층: 데이터 링크 계층](https://losskatsu.github.io/os-kernel/network-basic03/)
* [네트워크 기초(4) - 3계층: 네트워크 계층](https://losskatsu.github.io/os-kernel/network-basic04/)
* [네트워크 기초(5) - 4계층: 전송 계층](https://losskatsu.github.io/os-kernel/network-basic05/)
* [네트워크 기초(6) - 5,6,7계층: 응용 계층](https://losskatsu.github.io/os-kernel/network-basic06/)
* [DNS 서버란?](https://losskatsu.github.io/os-kernel/etc-host-dns/)
* [DHCP 서버란?](https://losskatsu.github.io/os-kernel/dhcp/)
* [ifconfig 출력 결과 해석](https://losskatsu.github.io/os-kernel/ifconfig/)
* [네트워크 소켓 프로그래밍](https://losskatsu.github.io/os-kernel/network-socket/)




## 1. OSI 7계층이란

예전에는 같은 회사의 컴퓨터끼리만 통신이 가능했던 시절이 있습니다. 
예를 들어, 삼성 컴퓨터랑 LG 컴퓨터는 서로 통신을 할 수 없는 것입니다. 
따라서 이러한 문제를 해결하기 위해, 서로다른 컴퓨터 회사들의 컴퓨터들이 자유롭게 통신할 수 있도록 
ISO(International Organization for Standardization, 국제표준화기구)에서 OSI 모델이라는 표준 규격을 만들었습니다. 

계층 | 이름 | 설명
-----|-------|-------------------
7계층 | 응용 계층(Application) | 애플리케이션 서비스 제공
6계층 | 표현 계층(Presentation) | 문자코드, 압축, 암호화
5계층 | 세션 계층(Session) | 통신 방식 결정
4계층 | 전송 계층(Transport) | 신뢰성 있는 통신 구현
3계층 | 네트워크 계층(Network) | 다른 네트워크와 통신하기 위한 IP주소 결정
2계층 | 데이터링크 계층(Data Link) | 물리주소 결정
1계층 | 물리 계층(Physical Layer) | 물리적인 연결과 전기 신호 변환

위 표가 바로 그 유명한 OSI 7 계층 입니다. 

데이터를 보내는 쪽(송신)과 받는 쪽(수신)이 있을 때 
데이터를 주고 받는 통신 과정은 다음 그림과 같습니다. 

<center><img src="/assets/images/os/network-basic/network01.jpg" width="800"></center>

데이터를 송신하는 쪽에서는 7계층 부터 시작합니다. 
왜냐면 데이터를 보낸다는 것은 무엇인가 애플리케이션이 특정 데이터를 다른 컴퓨터로 보내고 싶어하는 것이기 때문입니다. 
따라서 송신 쪽에서는 7계층부터 1계층 까지 거치고 받는 쪽에서는 1계층 부터 7계층까지 올라갑니다. 
받는 쪽을 생각해보면 랜선에 데이터가 들어오는 순간부터 데이터를 최종확인하는 애플리케이션까지 흘러가야하므로 
이러한 과정이 1계층부터 7계층까지 가는 과정인 것입니다. 


## 2. TCP/IP 모델 4계층

앞서 배운 OSI 7계층을 4계층 버전으로 바꾼것이 TCP/IP 모델 입니다. 

<center><img src="/assets/images/os/network-basic/network02.jpg" width="800"></center>


## 3. 캡슐화 

데이터를 송신할 때 송신하는 쪽에서는 처음에 보내는 7계층의 데이터로 시작해서 6계층, 5계층으로 내려갈수록 
각 계층에 필요한 헤더(header)를 붙입니다. 
이 때, 헤더(header)란 전송되는 원본 데이터 앞에 추가적으로 붙는 추가 정보 데이터 입니다.   

이렇게 데이터 앞에 헤더를 붙이는 과정을 캡슐화라고 부르고 1계층까지 내려간 후 
수신하는 쪽에 헤더(header)를 붙인 데이터를 보내면 
수신하는 쪽에서는 1계층부터 순차적으로 헤더(header)를 제거합니다. 그리고 마지막 7계층 까지가면 원래 수신하고자 하는 데이터만 남는 거죠. 
이를 그림으로 나타내면 다음과 같습니다. 

<center><img src="/assets/images/os/network-basic/network03.jpg" width="800"></center>

다음 포스팅부터는 OSI 7계층의 각각의 계층에 대해 알아보도록 하겠습니다. 

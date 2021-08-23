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

**참고 링크**

* [네트워크 기초(1) - OSI 7계층이란?](https://losskatsu.github.io/os-kernel/network-basic01/)
* [네트워크 기초(2) - 1계층: 물리계층](https://losskatsu.github.io/os-kernel/network-basic02/)
* [네트워크 기초(3) - 2계층: 데이터 링크 계층](https://losskatsu.github.io/os-kernel/network-basic03/)
* [네트워크 기초(4) - 3계층: 네트워크 계층](https://losskatsu.github.io/os-kernel/network-basic04/)
* [네트워크 기초(5) - 4계층: 전송 계층](https://losskatsu.github.io/os-kernel/network-basic05/)
* [네트워크 기초(6) - 5,6,7계층: 응용 계층](https://losskatsu.github.io/os-kernel/network-basic06/)
* [DNS 서버란?](https://losskatsu.github.io/os-kernel/etc-host-dns/)



## 1. 서론

물리 계층은 OSI 7계층 중에 1계층에 해당합니다. 
물리 계층은 시스템끼리 물리적인 연결을 하며 전기 신호를 변환, 제어 합니다. 
물리 계층은 전송하고자 하는 데이터를 전기 신호로 바꾸어 상대 컴퓨터에게 전송하는 일을 합니다.

<center><img src="/assets/images/os/network-basic/network02.jpg" width="800"></center>



## 2. 전기 신호

네트워크 통신에서는 숫자 0과 1만 사용합니다. 
즉, 우리가 전송하고자 하는 데이터는 모두 0과 1로 변환되어 전송됩니다. 
그렇다면 데이터를 0과 1로 이루어진 비트열로 변환만 하면 전송할 수 있을까요? 
아닙니다. 이렇게 변환한 0과 1을 다시 전기 신호로 변환 해야합니다. 
이렇게 전기 신호로 변환한 후 상대 컴퓨터 전송 할 수 있습니다. 
그리고 상대 컴퓨터는 전기 신호를 받고 다시 0과 1로 변환하는 과정을 거칩니다. 


<center><img src="/assets/images/os/network-basic/network04.jpg" width="800"></center>

그렇다면 0과 1을 누가 전기 신호로 바꿀까요? 
컴퓨터 메인보드에 꼽혀있는 랜(LAN) 카드를 본적이 있으실 겁니다. 
랜 카드는 인터넷을 사용하기 위해 필요한 랜 케이블을 꼽는 곳입니다. 
그렇습니다. 바로 이 랜 카드가 0과 1을 전기 신호로 바꿔 줍니다. 
그렇기 때문에 랜 카드가 있어야만 네트워크 상에서 통신이 가능합니다. 


## 3. 리피터(repeater)

그럼 이제 랜카드를 통해 0과 1을 전기 신호로 변환시켜 전송한다는 것까지 배웠습니다. 
전기 신호를 전송하려면 전선 케이블이 있어야 할 것입니다. 
바로 이때 리피터 라는 장비가 쓰입니다. 
물론 요즘에는 잘 안쓰지만 개념을 배우기 위해 집고 넘어 가겠습니다. 
(사실 저도 리피터 안써봤습니다ㅎㅎ)

<center><img src="/assets/images/os/network-basic/network05.jpg" width="800"></center>

리피터는 위 그림과 같이 전기 신호를 증폭시켜주는 장비입니다. 
상대방이 가까우면 랜 케이블만 연결해도 되지만 컴퓨터가 서로 멀리 있을 때는 신호가 갈수록 약해집니다. 
따라서 신호를 증폭시켜주는 리피터를 중간에 두면 신호를 제대로 받을 수 있습니다. 
리피터를 이용하면 1대1 통신이 가능합니다. 

## 4. 허브(hub)

앞서 배웠던 리피터를 이용하면 1대1 통신이 가능합니다. 
그러나 이번에 배울 허브(hub)를 이용하면 여러 대의 컴퓨터 간 통신이 가능합니다. 

<center><img src="/assets/images/os/network-basic/network06.jpg" width="800"></center> 

허브는 위 그림과 같이 포트가 여러 개 있어서 여러 대의 컴퓨터를 서로 연결할 수 있습니다. 
그리고 허브는 리피터처럼 신호를 증폭시키는 기능까지 가지고 있습니다. 
따라서 허브가 있으면 리피터는 별도로 필요 없는 것입니다. 

<center><img src="/assets/images/os/network-basic/network07.jpg" width="800"></center>

그러나 허브의 단점으로는 위 그림처럼 컴퓨터1이 컴퓨터4에게 데이터를 전송하려고 할때 컴퓨터4에게만 가는 것이 아니라 
허브에 연결되어 있는 모든 컴퓨터게에 전달 되는 것이 단점입니다. 
굳이 보내지 않아도 되는 컴퓨터2, 컴퓨터3에게 까지 전달하는 것이죠. 

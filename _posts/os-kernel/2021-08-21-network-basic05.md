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
* [네트워크 기초(5) - 4계층: 전송 계층](https://losskatsu.github.io/os-kernel/network-basic05/)
* [네트워크 기초(6) - 5,6,7계층: 응용 계층](https://losskatsu.github.io/os-kernel/network-basic06/)
* [DNS 서버란?](https://losskatsu.github.io/os-kernel/etc-host-dns/)



## 1. 신뢰성

이번 포스팅에서는 OSI 7계층 중 4계층에 해당하는 전송 계층에 대해 알아보겠습니다. 

<center><img src="/assets/images/os/network-basic/network02.jpg" width="800"></center>

지금까지 배운것을 잠시 복습해보면 다른 컴퓨터에 데이터를 전송하기 위해 
1계층에서는 허브, 2계층에서는 스위치, 3계층에서는 라우터가 필요했습니다. 

<center><img src="/assets/images/os/network-basic/network24.jpg" width="800"></center>


그런데 이렇게 데이터를 보내는것 까진 좋은데 데이터가 잘 전송되었는지, 
아니면 중간에 사고가 발생해 데이터 전송에 문제가 생겼는지는 알아야하지 않을까요? 
지금까지 배웠던 1,2,3계층만을 이용하면 이 문제를 해결할 수 없습니다. 
그래서 등장하는 것이 이번에 배울 전송 계층(Transport Layer)입니다. 

## 2. 전송 계층의 역할

전송 계층은 2가지 역할을 수행합니다. 
첫 번째로 3계층인 네트워크 계층이 데이터를 전달할 때 4계층인 전송 계층은 데이터가 제대로 도착했는지 확인을 합니다. 
또한 데이터가 최종적으로 도착할 애플리케이션이 무엇인지 식별하는 기능도 있습니다.

## 3. 연결형, 비연결형 통신

통신 방법은 크게 연결형 통신, 비연결형 통신으로 나눠지는데요. 
연결형 통신 방법을 사용하면 데이터를 신뢰성 있게 정확하게 전달 할 수 있습니다. 
그리고 비연결형 통신 방법을 사용하면 효율적으로 데이터를 전달할 수 있습니다. 

연결형 통신은 데이터를 정확하게 전달하기 위해 상대방과 계속 연락하면서 통신하는 방법이고 
비연결형 통신은 상대방의 반응은 확인하지 않고 일방적으로 데이터를 전송합니다. 
이렇게만 보면 비연결형 통신이 안좋아보이는데요. 각각 쓰임새가 다릅니다. 
연결형 통신은 신뢰성, 정확성이 중요할 때 사용하고, 
비연결형 통신은 동영상, 이미지와 같이 데이터가 좀 유실되도 상관없는 분야에 사용됩니다. 

대표적인 연결형 통신 프로토콜에는 TCP(Transmission Control Protocol)가 있으며, 
비연결형 통신 프로토콜에는 UDP(User Datagram Protocol)가 있습니다. 

TCP로 전송할때랑 UDP로 전송할 때랑 서로 다른 헤더를 붙입니다. 


## 4. TCP


## 4.1. 신뢰성 

이번에는 TCP에 대해서 자세하게 알아보겠습니다. 

TCP로 전송할때 붙이는 헤더를 TCP헤더라고 하고 TCP 헤더와 데이터를 합친 것을 세그먼트(segment)라고 부릅니다. 
2계층에서 이더넷헤더+데이터를 프레임이라 부르고, 3계층에서 IP헤더+데이터를 패킷이라고 불렀던 것을 참고해주세요. 

<center><img src="/assets/images/os/network-basic/network25.jpg" width="800"></center>


TCP는 데이터를 전송할 때 상대방의 반응을 계속확인한다고 했습니다. 
이게 가능하려면 상대방과 연결이 되어 있어야 되는데요. 
따라서 TCP 방식으로 전송하려면 먼저 연결(connection)을 통해 가상의 통신로를 이용해 통로를 확보하고 
데이터를 전송합니다. 

이를 위해 TCP헤더를 보면 코드 비트 부분에 연결 제어 정보가 기록됩니다. 

<center><img src="/assets/images/os/network-basic/network26.jpg" width="800"></center>


코드비트는 6비트로 구성되는데 상대방과 연결을 확보하려면 SYN과 ACK가 필요합니다. 
SYN은 연결 요청, ACK는 확인 응답을 의미합니다. 이 둘을 이용해 데이터를 전송하기 전에 
연결을 하기 위해 먼저 
패킷을 전송하는데 다음과 같이 진행합니다. 

<center><img src="/assets/images/os/network-basic/network27.jpg" width="800"></center>


위와 같이 데이터 전송전 패킷을 3번 주고 받는 것을 3-way handshake라고 합니다. 
이는 연결을 끊을때도 진행합니다. 

<center><img src="/assets/images/os/network-basic/network28.jpg" width="800"></center>


연결을 했다면 이제 본격적으로 데이터를 보내는데 TCP 헤더의 
일련번호와 확인 응답 번호를 보면 몇번째 데이터를 주고 받았는지 확인할 수 있습니다.

<center><img src="/assets/images/os/network-basic/network29.jpg" width="800"></center>


그런데 잘 생각해보면 세그먼트 하나를 보낼때 마다 계속 확인을 하면 비효율적일 수 있습니다. 
데이터를 보내는데 드는 수고보다 확인하는데 쓰는 수고가 더 크다고 할까요. 
이런 문제를 해결하기 위해 세그먼트를 몇개 연속으로 보내고 확인 응답을 한번만 보내는 방식을 택합니다. 
그리고 연속으로 받은 세그먼트를 일시적으로 보관하는 장소를 버퍼(buffer)라고 합니다. 
그런데 보내는 쪽에서 버퍼의 크기를 알아야 버퍼가 넘치지 않으니 이를 TCP 헤더에 버퍼 정보를 추가합니다. 
이것이 윈도우 크기(16비트) 입니다. 
윈도우 크기는 데이터를 저장할수 있는 용량을 나타냅니다. 

## 4.2. 식별성 

이번에는 전송된 데이터의 목적지가 어느 애플리케이션인지 구분하는 식별성에 대해 알아봅니다. 
이는 포트 번호(port number)로 구분하는데요. 
각 애플리케이션마다 포트 번호를 다르게 구분함으로써 도착지 애플리케이션 정보를 알 수 있습니다. 
즉, 어떤 컴퓨터로 전송할지는 IP주소가 필요하고 어떤 애플리케이션으로 가야하는지 알려면 포트 번호까지 필요합니다. 

따라서 TCP 헤더에는 출발지 포트 번호와 도착지 포트 번호가 포함되어 있습니다. 
포트 번호는 0번부터 65535번까지 사용할 수 있습니다. 
0~1023번 포트까지는 잘 알려진 포트라고 하고 주요 프로토콜이 사용됩니다. 
1024번은 예약은 되어 있지만 사용하지 않는 포트이고 1025번 이상부터는 랜덤 포트라고 부릅니다. 

대표적인 포트는 다음과 같습니다. 

애플리케이션 | 포트
--------------|---------
SSH | 22
SMTP | 25
DNS | 53
HTTP | 80
POP3 | 110
HTTPS | 443



## 5. UDP

이번에 다룰 UDP는 비연결형 통신이라 데이터 전송할 때 상대방의 반응을 일일이 확인하지 않습니다. 
따라서 UDP는 전송속도가 빠르다는 장점이 있습니다. 
앞서 말했듯, UDP는 데이터가 조금 손실, 유실되도 상관없는 동영상, 이미지를 전송할 때 사용됩니다. 
그리고 동일한 랜에 속하는(동일한 스위치에 연결되어 있는) 컴퓨터 모두에게 데이터를 보내는 브로드캐스팅을 할때도 UDP가 사용됩니다. 

<center><img src="/assets/images/os/network-basic/network30.jpg" width="800"></center>


앞서 TCP 헤더와 데이터를 합친것을 세그먼트라고 했습니다. 
이와 비슷하게 UDP 헤더와 데이터를 합친 것을 UDP 데이터그램이라고 부릅니다. 
복잡했던 TCP헤더와는 달리 UDP헤더는 간결합니다. 

<center><img src="/assets/images/os/network-basic/network30.jpg" width="800"></center>

그리고 상대방과 계속 패킷을 주고받던 TCP와는 달리 UDP는 상대방에게 알방적으로 데이터를 전송하는 것을 볼 수 있습니다. 

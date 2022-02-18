---
title: "네트워크 소켓 프로그래밍 정리" 
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

# TCP/IP 네트워크 소켓 프로그래밍 정리

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


## 1. 간단한 설명

이 포스팅은 윤성우 저 열혈 TCP/IP 소켓 프로그래밍 도서를 참고했습니다. 


네트워크 프로그래밍이란 네트워크로 연결되어 있는 서로 다른 두 컴퓨터가 데이터를 주고 받을 수 있도록 하는 것입니다. 
이때 네트워크 연결이라는 것은 물리적 연결과 소프트웨어적 연결이 존재하는데 물리적 연결은 기본적으로 되어 있다고 가정합니다. 
그렇다면 소프트웨어적 데이터 송수신 방법만 신경쓰면 되는데, 이는 운영체제에서 제공하는 소켓(socket)이라는 것을 이용하면 됩니다.
소켓(socket)이란 물리적으로 연결된 네트워크 상에서 데이터 송수신에 사용할 수 있는 소프트웨어적 장치를 의미합니다.  

네트워크 프로그래밍은 전화를 받는 과정에 비유할 수 있습니다. 전화를 받으려면 우선 전화를 설치해야하고, 전화번호를 부여하고, 
전화기를 전화 케이블에 연결하고 오는 전화를 받으면 됩니다.
이때 소켓은 전화기에 비유할 수 있습니다. 전화기를 설치하는 과정은 socket이라는 함수를 이용합니다. 
그리고 전화번호를 부여하는 것은 bind라는 함수를 이용해 ip, port 번호를 부여하는 것과 동일합니다. 
그리고 전화기를 전화 케이블에 연결하는 것은 listen 함수를 사용하는 것과 같습니다. 
끝으로 오는 전화를 받는 것은 accept 함수를 사용하는 것과 같습니다. 
참고로 상대방에게 전화를 거는 것은 connect 함수를 사용합니다.

함수 | 설명 |비유
-----|------|--
socket | 소켓 생성 | 전화기 설치 
bind | IP, Port 번호 할당 | 전화 번호 부여
listen | 연결 요청 가능 상태로 변경 | 전화 케이블 연결
accept | 연결 요청 수락| 오는 전화 받음
connect | 연결 요청 | 상대방에게 전화거는 행위

## 2. 프로그래밍 순서

연결 요청을 수락하는 기능의 프로그램을 서버(server)라고 합니다. 
서버 프로그램을 작성할 때는 앞서 배운 socket, bind, listen, accept 함수를 순서대로 사용합니다. 

```c
#include <sys/socket.h>
int socket(int domain, int type, int protocol);
int bind(int sockfd, struct sockaddr *myaddr, socklen_t addrlen);
int listen(int sockfd, int backlog);
int accept(int sockfd, struct sockaddr *addr, socklen_t *addrlen);
```

참고로 클라이언트에서 서버로 연결 요청하는 함수인 connect 함수는 다음과 같습니다.

```c
int connect(int sockfd, struct sockaddr *serv_addr, socklen_t addrlen);
```


## 3. 소켓과 리눅스 파일

리눅스는 소켓을 파일이라고 구분 짓습니다. 그래서 리눅스에서의 소켓 조작은 파일 조작과 동일합니다. 
따라서 파일 입출력 함수를 소켓 입출력에 사용할 수 있습니다. 
이말은 네트워크 상에서의 데이터 송수신에 사용할 수 있다는 말입니다. 
(참고로 윈도우는 파일과 소켓을 구분짓고 있습니다.)

리눅스에서 제공하는 파일 입출력 함수를 사용하려면 [파일 디스크립터](https://losskatsu.github.io/os-kernel/linux-redirection/)에 대한 개념을 알아야 합니다. 파일 디스크립터란 시스템으로 부터 할당 받은 파일 또는 소켓에 부여된 정수(int)를 의미합니다. 

파일 디스크립터 | 대상
----------------|------
0 | 표준 입력(Standard Input)
1 | 표준 출력(Standard Output)
2 | 표준 에러(Standard Error)

일반적으로 파일은 생성 과정을 거쳐야 파일 디스크립터가 할당됩니다. 
반면 위에 보이는 세가지 입출력 대상은 별도의 생성 과정을 거치지 않아도 
프로그램이 실행되면 자동으로 할당되는 파일디스크립터 입니다. 
쉽게 말해, 파일 디스크립터는 운영체제가 만든 파일의 지칭을 편히 하기 위해 부여된 숫자입니다. 
파일 디스크립터는 '파워 핸들'이라고도 부릅니다. 

## 4. 프로토콜

프로토콜(protocol)이란 컴퓨터간 대화에 필요한 통신 규약을 의미합니다. 
쉽게말해 프로토콜이란 약속인데, 서로 데이터를 주고 받기위해 정의한 약속을 의미합니다.

## 5. 소켓 구분에 활용되는 PORT번호

우리가 사용하는 IP주소는 컴퓨터를 구분하기 위한 목적으로 존재합니다. 
그래서 IP만 있으면 목적지 컴퓨터로 데이터를 전송할 수 있습니다. 
그러나 IP만으로는 데이터를 수신하는 최종목적지인 응용프로그램까지 
데이터를 전송할 수는 없습니다. 
이때 컴퓨터 내부로 들어온 데이터를 소켓에 분배하는 작업은 운영체제가 담당합니다. 
그리고 이를 위해 운영체제는 PORT 번호를 사용합니다. 
이렇듯 PORT번호는 하나의 운영체제 내에서 소켓을 구분하는 목적으로 사용되기 때문에 
하나의 운영체제 내에서 동일한 PORT 번호를 둘 이상의 소켓에 할당할 수 없습니다. 
PORT 번호는 16비트로 표현되므로 포트 번호 표현 범위는  0이상 65535이하 입니다. 



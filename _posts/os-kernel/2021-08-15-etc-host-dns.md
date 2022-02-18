---
title: "DNS 서버란? /etc/hosts 파일이란?" 
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

# DNS서버란? /etc/hosts 파일이란?

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




이번 포스팅에서는 DNS 서버에 대해 알아보고 이와 연관지어 리눅스에서 /etc/hosts 파일에 대해 알아보겠습니다. 

## 1. DNS?

DNS는 Domain Name System의 줄임말로 웹 사이트의 IP주소와 도메인 주소를 이어주는 시스템을 말합니다. 
그리고 이런 시스템 역할을 하는 서버를 DNS서버라고 부르는 것입니다.  

DNS는 IP주소와 도메인 주소를 이어주는 시스템이라고 했습니다. 그렇다면 도메인이란 무엇일까요? 

## 2. 도메인

만약 우리가 웹사이트를 방문할 때 일일이 IP주소를 입력해야한다면 외우기 힘들고 헷갈릴 것입니다. 
도메인(domain)은 사람이 쉽게 기억할 수 있도록 문자 형태로 만든 인터넷 주소를 말합니다.  

이는 간단한 예를 통해 쉽게 이해할 수 있습니다. 

크롬 브라우저를 열고 주소창에 다음 ip를 입력해보세요. 
다음 아이피 주소는 우리가 알고 있는 네이버 입니다. 

[http://125.209.222.141/](http://125.209.222.141/)

그런데 네이버 접속할 때마다 위 IP를 입력해야한다면 굉장히 귀찮겠죠? 
저 아이피를 보고 네이버를 떠올리기는 쉽지 않을 것입니다. 
따라서 이러한 문제점을 해결하기 위해 도메인을 사용합니다. 
다음 도메인처럼 말이죠.  

[https://www.naver.com/](https://www.naver.com/)

위와 같은 도메인을 보면 한눈에 네이버라는 것을 알 수 있습니다.

## 3. DNS 서버

그렇다면 이제 DNS서버가 무엇을 하는지 알 수 있습니다. 
DNS서버는 우리가 주소창에 [https://www.naver.com/](https://www.naver.com/)를 입력했을때, 
이를 IP주소인 [http://125.209.222.141/](http://125.209.222.141/)로 변환해주는 서버를 의미합니다. 
당연히 DNS서버 내부를 보면 IP주소와 도메인주소가 매핑되어 있을 것입니다. 
예를 들어, [https://www.naver.com/](https://www.naver.com/)와 
[http://125.209.222.141/](http://125.209.222.141/)를 매핑 시키는 것이죠. 


## 4. 우리가 주소창에 네이버를 입력했을 때 일어나는 일

그렇다면 앞서 배운 내용을 토대로 우리가 웹 브라우저 주소창에 [https://www.naver.com/](https://www.naver.com/)를 입력했을 때 
일어난 일을 그림으로 알아보겠습니다. 

<center><img src="/assets/images/os/dns/dns01.jpg" width="800"></center>

우리가 주소창에 [https://www.naver.com/](https://www.naver.com/)를 입력하면 먼저 dns서버에 물어봅니다. 
나는 지금 [https://www.naver.com/](https://www.naver.com/)에 접속하고 싶은데 이분 ip가 뭐야?라고 말이죠. 
그러면 dns서버가 해당 주소의 ip를 알려줍니다. [http://125.209.222.141/](http://125.209.222.141/)라고 말이죠. 
dns 서버를 통해 해당 도메인의 ip를 알아냈다면 알아낸 ip로 접속을 시도합니다. 
그리고 요청을 받은 [http://125.209.222.141/](http://125.209.222.141/)는 저에게 화면을 보여줍니다. 

## 5. 리눅스 /etc/hosts 파일

리눅스 계열의 파일 시스템을 보면 etc 디렉토리에 hosts파일이 존재합니다. 
그리고 이 hosts 파일이 dns서버역할을 합니다. 
예를 들어, 우리가 주소창에 localhost라고 입력했을 때 해당 도메인을 127.0.0.1로 바꿔주는거죠.

/etc/hosts 파일은 다음과 같이 생겼습니다. 

```bash
$ cat /etc/hosts
127.0.0.1       localhost
::1             localhost ip6-localhost ip6-loopback
ff02::1         ip6-allnodes
ff02::2         ip6-allrouters

127.0.1.1               raspberrypi
```

파일을 보면 127.0.0.1이랑 localhost랑 매핑되어 있는 것을 볼 수 있습니다. 

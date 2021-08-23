---
title: "네트워크 기초(6) - OSI 7계층 - 5,6,7계층" 
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

# 네트워크 기초(6) - OSI 7계층 - 5,6,7계층

**참고 링크**

* [네트워크 기초(1) - OSI 7계층이란?](https://losskatsu.github.io/os-kernel/network-basic01/)
* [네트워크 기초(2) - 1계층: 물리계층](https://losskatsu.github.io/os-kernel/network-basic02/)
* [네트워크 기초(3) - 2계층: 데이터 링크 계층](https://losskatsu.github.io/os-kernel/network-basic03/)
* [네트워크 기초(4) - 3계층: 네트워크 계층](https://losskatsu.github.io/os-kernel/network-basic04/)
* [네트워크 기초(5) - 4계층: 전송 계층](https://losskatsu.github.io/os-kernel/network-basic05/)
* [네트워크 기초(6) - 5,6,7계층: 응용 계층](https://losskatsu.github.io/os-kernel/network-basic06/)


## 1. 애플리케이션

이번 포스팅에서는 OSI 7계층 중 5,6,7계층을 한꺼번에 알아볼것인데 주로 응용 계층에 대해 알아봅니다. 

<center><img src="/assets/images/os/network-basic/network02.jpg" width="800"></center>

일반적으로 서비스를 요청하는 쪽을 클라이언트, 서비스를 제공하는 쪽을 서버라고 합니다. 

웹사이트를 볼때는 HTTP, 파일을 전송할때는 FTP, 메일을 보낼 때는 SMTP, 
메일을 받을 때는 POP3라는 프로토콜을 사용합니다. 

## 2. 응용 계층 프로토콜

자주 사용되는 응용 계층 프로토콜은 다음과 같습니다. 

프로토콜 | 역할
---------|-----
HTTP | 웹 사이트 접속
DNS | 도메인 해석
FTP 파일 전송
SMTP | 메일 전송
POP3 | 메일 수신

## 3. 웹

이번에는 웹에 대해 알아보겠습니다. 
인터넷에서 핵심적인 역할을 하는 것은 www(world wide web)입니다. 
우리가 웹(web)이라고 부르는 것은 바로 이 www입니다. 

www는 HTML, URL, HTTP라는 세가지 기술을 사용합니다. 

HTML은 웹페이지를 작성할때 사용하는 언어이고, 
웹사이트를 보기위한 파일이 확장자가 html인 html파일입니다. 
즉, 웹사이트를 보기위해 서버와 클라이언트는 html파일을 주고 받는 것입니다. 

그리고 html파일을 주고 받기 위해 80번 포트를 사용해 HTTP통신을 합니다. 

그리고 URL(Uniform Resource Locator)는 인터넷에서 파일 위치를 지정하기 위해 기술된 주소입니다. 
url은 웹사이트 주소를 지정하기 위해 사용합니다. 

## 4. DNS 

DNS 서버에 대한 내용은 [링크](https://losskatsu.github.io/os-kernel/etc-host-dns/)를 참고해주세요.

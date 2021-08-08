---
title: "라즈베리파이 가상 머신에 설치하기" 
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

# 라즈베리파이 가상 머신에 설치하기

이번 포스팅에서는 버츄어 박스 가상머신에 라즈베리파이 OS를 설치하고 putty로 접속해 보겠습니다.

## 1. 버츄어 박스 다운로드

먼저 다음 사이트로 이동해 버츄어 박스를 다운로드 받고 설치합니다.

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)  

용량이 꽤 큽니다..!


## 2. 라즈베리파이 OS 이미지 다운로드

버츄어 박스를 다운로드 받고 설치했다면, 가상 머신에 올릴 라즈베리파이 OS를 다운로드 받습니다. 

[https://www.raspberrypi.org/software/raspberry-pi-desktop/](https://www.raspberrypi.org/software/raspberry-pi-desktop/)  

위 사이트에 접속하면 다음과 같은 화면이 나오는데 다운로드 받아줍니다. 
확장자는 ISO 입니다. 

<center><img src="/assets/images/os/raspberrypi/vminstall/00.JPG" width="800"></center>

## 3. 버츄어 박스 실행 및 이미지 추가

<center><img src="/assets/images/os/raspberrypi/vminstall/01.png" width="800"></center>

<center><img src="/assets/images/os/raspberrypi/vminstall/02.JPG" width="800"></center>

<center><img src="/assets/images/os/raspberrypi/vminstall/03.JPG" width="800"></center>

<center><img src="/assets/images/os/raspberrypi/vminstall/04.JPG" width="800"></center>

<center><img src="/assets/images/os/raspberrypi/vminstall/05.JPG" width="800"></center>

<center><img src="/assets/images/os/raspberrypi/vminstall/06.JPG" width="800"></center>

<center><img src="/assets/images/os/raspberrypi/vminstall/07.JPG" width="800"></center>

<center><img src="/assets/images/os/raspberrypi/vminstall/08.JPG" width="800"></center>

<center><img src="/assets/images/os/raspberrypi/vminstall/09.JPG" width="800"></center>

<center><img src="/assets/images/os/raspberrypi/vminstall/10.JPG" width="800"></center>

위와 같이 디스크에 비어있음으로 되어있는데 아까 다운로드 받은 ISO 이미지를 추가해줍니다. 
이는 마치 CD롬에 CD를 넣는다고 생각하면 됩니다.

<center><img src="/assets/images/os/raspberrypi/vminstall/09.JPG" width="800"></center>

위 그림에서 '시작'을 눌러줍니다.


## 4. 라즈베리파이 OS 설치

앞서 시작을 눌른 후 화면에서 INSTALL을 눌러 OS를 설치합니다. 

<center><img src="/assets/images/os/raspberrypi/vminstall/11.JPG" width="800"></center>

<center><img src="/assets/images/os/raspberrypi/vminstall/12.JPG" width="800"></center>

설치가 완료되면 다음과 같은 화면이 나오는데 각종 설정을 해줍니다.

<center><img src="/assets/images/os/raspberrypi/vminstall/13.JPG" width="800"></center>

지금부터는 ssh 접속을 가능하게 하기 위한 설정을 해줍니다. 

딸기모양 -> Preferences -> Raspberry Pi Configuration  

을 클릭합니다.

<center><img src="/assets/images/os/raspberrypi/vminstall/14.JPG" width="800"></center>

이 때 기본값이 disable로 되어있는데, enable로 바꿔 줍니다. 

<center><img src="/assets/images/os/raspberrypi/vminstall/15.JPG" width="800"></center>


## 5. 네트워크 설정 및 접속

우리는 22번 포트로 접속할 것이므로 22번 포트를 포트포워딩 해주겠습니다. 
버츄어 박스에서 다음과 같이 설정합니다. 

<center><img src="/assets/images/os/raspberrypi/vminstall/16.JPG" width="800"></center>

<center><img src="/assets/images/os/raspberrypi/vminstall/17.JPG" width="800"></center>

그리고 마지막으로 putty를 사용해 접속하면 됩니다. 

우리는 로컬에 라즈베리파이 OS가 있으므로 127.0.0.1로 접속하면 됩니다. 

<center><img src="/assets/images/os/raspberrypi/vminstall/18.JPG" width="800"></center>


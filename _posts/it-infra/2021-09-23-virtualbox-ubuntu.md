---
title: "[Infra] 버추어박스(virtualbox)에 우분투 설치하기" 
categories:
  - it-infra
tags:
  - it-infra
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 버추어박스(virtualbox)에 우분투 설치하기

**참고 링크**

* [버추어박스-라즈베리파이 설치](https://losskatsu.github.io/os-kernel/raspberry-vminstall/)  
* [버추어박스-우분투 설치](https://losskatsu.github.io/it-infra/virtualbox-ubuntu/)  


## 1. 우분투 다운로드

버추어박스에 우분투를 설치하기 위해 먼저 우분투를 다운로드 하겠습니다. 
다음 사이트에서 우분투를 다운로드합니다.  

[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)  

위 사이트에 접속하면 다음과 같은 모습을 볼수 있는데 다운로드를 클릭합니다.

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb01.png" width="800"></center>

위 사진에서 다운로드를 클릭하면 우분투 이미지를 다운받을 수 있습니다.


## 2. 설정


<center><img src="/assets/images/infra/virtualbox-ubuntu/vb02.png" width="800"></center>

이미지를 다운로드 받았다면 버추어박스를 실행시킨후 "새로만들기"를 클릭하고, 
가상머신의 이름과 종류, 버전을 선택합니다. 이름은 각자 원하는 이름으로 정하고, 
종류는 Linux이고 버전은 우분투 64비트인데 기본적으로 설정되어있으므로 다음을 클릭합니다.

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb03.png" width="800"></center>

다음은 메모리 크기를 설정합니다. 저는 기본적으로 1024로 설정되어 있었는데, 
이는 전체 메모리 크기가 얼마냐에 따라 달라집니다. 다음을 클릭합니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb04.png" width="800"></center>

다음으로 기본 설정으로 지금 새 가상하드 디스크 만들기가 선택되어 있는데 만들기를 클릭합니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb05.png" width="800"></center>

다음도 기본설정인 VDI를 그대로 두고 다음을 클릭합니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb06.png" width="800"></center>

그리고 다음 단계도 동적 할당으로 설정되어 있는데 다음을 누릅니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb07.png" width="800"></center>

다음은 디스크 크기를 정하는데 기본 10GB입니다. 디스크 크기를 변경하고 싶다면 여기서 하면 됩니다. 
디스크 크기를 정했다면 "만들기"를 클릭합니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb08.png" width="800"></center>

그러면 위와 같이 가상 머신이 추가되었는데 본격적인 설치 이전에 설정을 클릭합니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb09.png" width="800"></center>

먼저 저장소를 클릭하고 옆에 컨트롤러:IDE의 비어있음을 클릭하고 오른쪽 디스크 모양을 클릭한다음 
가상 광학 디스크 선택/만들기를 클릭합니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb10.png" width="800"></center>

그리고 추가를 클릭하고 아까 다운로드 받은 우분투 이미지를 추가합니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb11.png" width="800"></center>

그러면 위 그림처럼 우분투 이미지가 추가됩니다. 해당 이미지를 더블클릭합니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb12.png" width="800"></center>

그러면 위 그림처럼 CD가 삽입된 것을 볼 수 있습니다. 확인은 누르지 말고 디스플레이로 이동합니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb13.png" width="800"></center>

디스플레이 섹션으로 넘어간후 그래픽 컨트롤러를 VBoxVGA로 바꿉니다. 
이를 바꾸는 이유는 이후에 가상환경에서 화면 크기를 조절하기 위해서 입니다. 그리고 확인을 누릅니다.

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb14.png" width="800"></center>

그러면 다시 메인화면으로 돌아가는데 저장소에 우분투 이미지가 들어있는 것을 볼 수 있으므로 
시작을 눌러줍니다. 

## 3. 우분투 설치


<center><img src="/assets/images/infra/virtualbox-ubuntu/vb15.png" width="800"></center>

그러면 위 그림처럼 우분투가 실행됩니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb16.png" width="800"></center>

그러면 언어 선택 화면부터 나오는데 우분투를 설치해줍니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb17.png" width="800"></center>

그리고 키보드 언어를 선택하고 계속하기를 선택합니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb18.png" width="800"></center>

그리고 우분투 버전을 선택하는데 기본은 일반설치 입니다. 
그런데 저는 용량을 아끼고 싶어서 최소 설치로 가겠습니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb19.png" width="800"></center>

다음 단계도 지금 설치를 눌러주면 됩니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb20.png" width="800"></center>

다음 화면에서 이름은 계정명을 나타내고, 컴퓨터 이름은 호스트명을 나타냅니다. 
즉 위와 같이 이름을 practice로 하고 컴퓨터 이름을 server01로 정하면 practice@server01이 되는 겁니다. 
그리고 계속하기를 누릅니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu/vb21.png" width="800"></center>

그러면 우분투 설치가 시작됩니다.  

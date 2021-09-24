---
title: "[Infra] 버추얼박스(virtualbox) 우분투에 고정 ip 할당하기" 
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

# 버추얼박스(virtualbox) 우분투에 고정 ip 할당하기

**참고 링크**

* [버추어박스-라즈베리파이 설치](https://losskatsu.github.io/os-kernel/raspberry-vminstall/)  
* [버추어박스-우분투 설치](https://losskatsu.github.io/it-infra/virtualbox-ubuntu/)  


## 1. 호스트(윈도우) 네트워크 설정

이번 포스팅에서는 가상머신(버추얼박스)에 설치된 우분투에 고정 ip를 할당하는 방법을 알아보겠습니다.  

<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip01.png" width="800"></center>

먼저 버추얼박스를 실행하고 파일-> 호스트네트워크 관리자를 클릭합니다. 
이는 호스트 네트워크를 설정하기 위함입니다.

<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip02.png" width="800"></center>

그러면 위와 같은 창이 뜨는데 "만들기"를 클릭하고 DHCP 서버 "사용함"에 체크합니다. 
그리고 속성을 누르면 아래에 DHCP 탭이 있는데 그걸 누르면 여러가지 정보가 나옵니다. 
이를 기억하고, 닫기를 눌러줍니다.

호스트(윈도우) 네트워크 설정은 이것으로 끝입니다.


## 2. 게스트(우분투) 네트워크 설정

앞서 호스트(윈도우) 네트워크 설정을 했다면 이번에는 게스트(우분투)의 네트워크를 설정해봅니다.

<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip03.png" width="800"></center>

그 다음으로 다시 메인화면으로 가는데 우리가 설치한 우분투 머신의 설정을 눌러줍니다. 
이때 주의해야할 점은 우분투의 전원이 꺼져있어야한다는 점입니다. 
왜냐면 우리는 네트워크 설정을 할 것이므로 우부투가 켜져있으면 안됩니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip04.png" width="800"></center>

설정을 누르고 네트워크 탭에 들어가면 어댑터1이 보입니다. 어댑터1은 NAT인데 이거 그냥 건드리지말고 
어댑터2를 클릭합니다. 
만약 아까 설정 누르기전에 우분투가 실행중이라면 어댑터2가 눌러지지 않을 것입니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip05.png" width="800"></center>

어댑터2를 누르고 "네트워크 어댑터 사용하기" 박스를 클릭해줍니다. 
그리고 "호스트 전용 어댑터"를 클릭하고 "고급"을 클릭해서 나오는 MAC주소를 기억해둡시다. 
그리고 확인을 누릅니다.

## 3. 게스트(우분투) ip 설정

이번에는 본격적으로 우분투를 실행해서 ip를 바꿔보겠습니다. 
우분투에 접속해서 터미널을 실행한후 

```bash
$ ifconfig
```

를 실행하면 다음과 같은 그림이 나옵니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip06.png" width="800"></center>

위 그림을 보면 아까 우리가 확인했던 맥주소가 보이는 것을 볼 수 있습니다. 
그러나 아직 맥주소만 있을뿐 ip 주소는 없는 것을 볼 수 있습니다. 
걱정마세요. 우리가 이제 할당할 것입니다. 


<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip07.png" width="800"></center>

우측 상단 화살표가 나오는데 우리가 ip를 할당할 이더넷의 유선 네트워크 설정을 클릭해줍니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip08.png" width="800"></center>

그러면 위와 같은 화면이 나오는데 톱니바퀴 버튼 클릭해줍시다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip09.png" width="800"></center>

그러면 위와 같은 화면이 나오는데 IPv4를 클릭하고 주소, 넷마스크, 게이트웨이 주소를 설정해줍니다. 
이는 맨 처음에 호스트 네트워크 설정할때 봤던 화면을 참고해서 정해주세요. 
다 적었다면 "적용"을 클릭합니다.

<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip10.png" width="800"></center>

그리고 이더넷을 껏다 켜줍니다.(중요) 껏다켜면 위 그림처럼 "연결됨"이라고 뜰겁니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip11.png" width="800"></center>

그리고 다시 터미널로 가서 ip 주소를 확인하면 아까 제가 정한대로 ip가 정해져있는것을 볼 수 있습니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip12.png" width="800"></center> 

ip를 정했으니 이번에는 ssh 서버를 생성하고 포트를 열어보겠습니다. 먼저 터미널에 다음과 같이 입력하면 
ssh가 설치됩니다. 

```bash
$ sudo apt install openssh-server
```

<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip13.png" width="800"></center>

설치가 잘 되엇는지 확인하는 명령어는 다음과 같습니다. 

```bash
$ sudo systemctl status ssh
```

<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip14.png" width="800"></center>

이번에는 ssh 포트를 열어봅니다. 

```bash
$ sudo ufw allow ssh
$ netstat -tnlp
```

위 코드에서 첫 코드는 ssh 상태를 보는거고 두번째 코드는 22번 포트가 열였는지 확인하는 코드입니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip15.png" width="800"></center>

이제 다시 호스트(윈도우)로 돌아와 cmd로 게스트(우분투)에게 ping을 쏴봅니다. 
잘쏴지는 것을 볼 수 있습니다. 

<center><img src="/assets/images/infra/virtualbox-ubuntu-ip/ip16.png" width="800"></center>

putty로 접속해도 잘 되는 것을 볼 수 있습니다. 

지금까지 버추얼박스에 설치된 우분투에 고정 ip를 부여하는 방법을 알아보았습니다. 

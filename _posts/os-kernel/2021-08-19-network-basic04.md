---
title: "네트워크 기초(4) - OSI 7계층 - 3계층: 네트워크 계층" 
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

# 네트워크 기초(4) - OSI 7계층 - 3계층: 네트워크 계층

**참고링크**

| 운영체제 | 프론트엔드 | 백엔드 | 데이터베이스| 인프라 |
|:------:|:------:|:------:|:------:|:------:|
|[리눅스구조](https://losskatsu.github.io/os-kernel/os-linux-structure) | [js필터](https://losskatsu.github.io/frontend/js-map-reduce-filter/) | [아파치에러로그](https://losskatsu.github.io/it-infra/apache-error-log/) | [행삭제](https://losskatsu.github.io/it-infra/sqldelete/) | [아파치스쿱](https://losskatsu.github.io/it-infra/sqoop/) |
|[프로세스](https://losskatsu.github.io/os-kernel/os-process/) | [헬로월드](https://losskatsu.github.io/frontend/react-helloworld/) | [웹서버개념](https://losskatsu.github.io/it-infra/webserver/) | [ES기초](https://losskatsu.github.io/it-infra/es-basic/) | [로그분석](https://losskatsu.github.io/it-infra/log-anal/) |
|[네임스페이스](https://losskatsu.github.io/os-kernel/linux-redirection/) |[프로젝트생성](https://losskatsu.github.io/frontend/react-basic-setup/) | [아파치설치](https://losskatsu.github.io/it-infra/aws-apache/) | [MySQL기초](https://losskatsu.github.io/it-infra/mysql-index/) | [beeline](https://losskatsu.github.io/it-infra/beeline/) |
|[디렉토리](https://losskatsu.github.io/os-kernel/linux-directory/) |[헤더생성](https://losskatsu.github.io/frontend/react-category/) | [flask연동](https://losskatsu.github.io/it-infra/flask-nginx-uwsgi/) | [큐브리드](https://losskatsu.github.io/it-infra/cubrid-summary/) | [하둡기초](https://losskatsu.github.io/it-infra/hadoop-basic-concept/) |
|[리다이렉션](https://losskatsu.github.io/os-kernel/linux-redirection/) |[async-get](https://losskatsu.github.io/frontend/react-request-api-django/) | [장고MsSQL연결](https://losskatsu.github.io/it-infra/mssql-django-conn/) | [null공백](https://losskatsu.github.io/it-infra/db-null/) |  [나이파이](https://losskatsu.github.io/it-infra/nifi/) |
|[쓰레드](https://losskatsu.github.io/os-kernel/process-thread/) | [async-post](https://losskatsu.github.io/frontend/react-request-post/) | [장고MySQL연결](https://losskatsu.github.io/it-infra/mysql-django-conn/) | [MySQL설치(win)](https://losskatsu.github.io/it-infra/mysql-install-win/) | [백본](https://losskatsu.github.io/it-infra/backbone/) |
|[라즈베리파이설치](https://losskatsu.github.io/os-kernel/raspberry-vminstall/) | [로그인페이지](https://losskatsu.github.io/frontend/react-request-post/) | [장고inpectdb](https://losskatsu.github.io/it-infra/django-inspectdb/) | [MySQL테이블생성](https://losskatsu.github.io/it-infra/mysql-create-db/) | [제플린](https://losskatsu.github.io/it-infra/backbone/) |
|[OSI7계층소개](https://losskatsu.github.io/os-kernel/network-basic01/) | | [장고read](https://losskatsu.github.io/it-infra/django-read-data/)  |  | [SSL인증](https://losskatsu.github.io/it-infra/ssl-auth/)|
|[OSI1계층](https://losskatsu.github.io/os-kernel/network-basic02/) | | [장고insert](https://losskatsu.github.io/it-infra/django-post-data/)  | | [커버로스](https://losskatsu.github.io/it-infra/kerberos/) |
|[OSI2계층](https://losskatsu.github.io/os-kernel/network-basic03/) | | [장고put](https://losskatsu.github.io/it-infra/django-put-data/)  | | [도커개념](https://losskatsu.github.io/it-infra/docker00/) |
|[OSI3계층](https://losskatsu.github.io/os-kernel/network-basic04/) | | [장고del](https://losskatsu.github.io/it-infra/django-del-data/) | | [도커설치](https://losskatsu.github.io/it-infra/docker01/) |
|[OSI4계층](https://losskatsu.github.io/os-kernel/network-basic05/) | |  | |[도커기초](https://losskatsu.github.io/it-infra/docker02/)|
|[OSI5,6,7계층](https://losskatsu.github.io/os-kernel/network-basic05/) | |  | | [도커이미지](https://losskatsu.github.io/it-infra/docker03/) |
|[DNS서버](https://losskatsu.github.io/os-kernel/etc-host-dns/) | |  | | [컨테이너네트워크](https://losskatsu.github.io/it-infra/docker04/) |
|[DHCP](https://losskatsu.github.io/os-kernel/dhcp/) | | | | [도커API](https://losskatsu.github.io/it-infra/docker05/) |
|[bashrc](https://losskatsu.github.io/os-kernel/bashrc/) | | | | [도커컴포즈](https://losskatsu.github.io/it-infra/docker06/) |
|[bash](https://losskatsu.github.io/os-kernel/bash/) | | | | [도커볼륨](https://losskatsu.github.io/it-infra/docker07/) |
|[ifconfig](https://losskatsu.github.io/os-kernel/ifconfig/) | | | | [장고이미지](https://losskatsu.github.io/it-infra/docker08/) |
|[소켓프로그래밍](https://losskatsu.github.io/os-kernel/network-socket/) | | | | [도커postgre](https://losskatsu.github.io/it-infra/docker09/) |
|[리눅스유저생성](https://losskatsu.github.io/os-kernel/linux-create-user/) | | | | [도커이미지삭제](https://losskatsu.github.io/it-infra/docker10/)|
|[netstat포트열기](https://losskatsu.github.io/os-kernel/port-open/) | | | |[도커Redis](https://losskatsu.github.io/it-infra/docker11/) |
|[컴파일러](https://losskatsu.github.io/os-kernel/compiler-interpreter/) | | | |[k8s구조](https://losskatsu.github.io/it-infra/kubernetes01/) |
|[운영체제vs커널](https://losskatsu.github.io/os-kernel/diff-kernel-os/) | | | | [k8s설치](https://losskatsu.github.io/it-infra/kubernetes02/) |
|[작업스케쥴링](https://losskatsu.github.io/os-kernel/crontab/) | | | |[k8s서비스배포](https://losskatsu.github.io/it-infra/kubernetes03/) |
|[디스크추가](https://losskatsu.github.io/os-kernel/add-harddisk/) | | | |[POD네트워크](https://losskatsu.github.io/it-infra/kubernetes04/) |
|[aws유저추가](https://losskatsu.github.io/os-kernel/aws-add-user/) | | | | [퍼시스턴트볼륨](https://losskatsu.github.io/it-infra/kubernetes05/)|
|[기초명령어](https://losskatsu.github.io/it-infra/ps-grep-pipe-redirect/) | | | | [k8s에러](https://losskatsu.github.io/it-infra/kubernetes06/)|
|[포트번호](https://losskatsu.github.io/it-infra/port/) | | | | |




## 1. 스위치 너머 저편으로

이번 포스팅에서는 OSI 7계층 중 3계층에 해당하는 네트워크 계층에 대해 알아보겠습니다. 

<center><img src="/assets/images/os/network-basic/network02.jpg" width="800"></center>

앞서 [데이터 링크 계층](https://losskatsu.github.io/os-kernel/network-basic03/)에서는 스위치라는 장비를 이용해 스위치에 연결되어 있는 
컴퓨터끼리 이더넷이라는 규칙하에 프레임을 주고 받았습니다. 
그러나 이러한 방법으로는 동일한 스위치에 연결되어 있는 컴퓨터끼리만 데이터를 전송할수 있습니다. 
즉, 스위치 너머에 있는 다른 네트워크로는 데이터를 전송할 수 없습니다. 


## 2. 라우터

하나의 스위치에 연결되어 있는 컴퓨터들의 모음을 하나의 '네트워크'라고 표현하겠습니다. 
그렇다면 서로다른 네트워크에 있는 컴퓨터들은 서로 어떻게 데이터를 주고받을 수 있을까요? 

<center><img src="/assets/images/os/network-basic/network16.jpg" width="800"></center>

이때 등장하는 것이 네트워크 계층입니다. 네트워크 계층은 서로 다른 네트워크 간의 통신을 가능하게 해줍니다. 
즉, 서로다른 네트워크에 속한 컴퓨터들끼리 데이터를 주고 받을 수 있다는 뜻입니다. 

1계층에서 허브라는 장비를 사용했고, 2계층에서 스위치라는 장비를 사용했다면 
3계층에서는 라우터(router)라는 장비를 사용합니다. 
2계층 데이터링크 계층에서는 데이터를 전송하기 위해 상대방 맥 주소가 필요했습니다. 
이와 비슷하게 3계층에서는 상대방의 IP 주소를 알아야 데이터를 전송할 수 있습니다. 
또한 목적지인 상대방 IP 주소 뿐만 아니라 어떤 경로로 보낼지도 결정해야하는데 이를 라우팅(routing)이라고 합니다. 

라우터는 거리에 상관없이 데이터를 보낼수 있습니다. 그리고 라우터에는 라우팅 테이블(routing table)을 이용해 
경로 정보를 등록, 관리 합니다. 

## 3. IP 주소 개요

네트워크 계층에서는 IP(Internet Protocol)라는 프로토콜을 사용합니다. 
그리고 네트워크 계층에서는 캡슐화할 때 IP 헤더를 붙입니다. 
IP헤더에는 버전, 헤더 길이, 서비스 유형, 전체 패킷 길이, ID, flags, fragment offset, TTL, 
프로토콜, 헤더체크섬, 출발지 IP, 목적지 IP 순서로 헤더가 구성되어 있습니다. 

<center><img src="/assets/images/os/network-basic/network17.jpg" width="800"></center>

이렇게 보내려고 하는 데이터에 IP 헤더를 포함한 것을 IP 패킷이라고 합니다. 
(참고로 데이터링크에서는 프레임이라고 불렀습니다.)

IP 주소는 ISP(인터넷 서비스 제공자)에게 받을 수 있습니다. 
ISP는 쉽게 말해 인터넷 사용하려고 신청한 통신사를 의미합니다. 

IP 버전은 IPv4, IPv6 두 종류가 있습니다. 
IPv4는 32비트로 구성되어 있으며, IPv6는 128비트로 구성되어 있습니다. 
기존에는 IPv4를 사용하다가 IP주소가 부족해서 만들어진것이 IPv6 입니다. 

IP주소는 2계층에서 배운 MAC 주소와는 비트 수가 다릅니다. 
MAC 주소는 48비트, 16진수로 표시하고, IP주소는 32비트 10진수로 표시합니다. 
물론 IP주소를 10진수로 표시하긴 하지만 이는 사람이 보기 편하기 위해 10진수로 표현하는 것이지 
실제 IP주소는 2진수로 되어 있습니다.
참고로 8비트를 옥텟(octet)이라고 부릅니다. 

따라서 요새는 IP가 부족한 상황이기 때문에 
ISP에서 주는 공인 IP주소는 라우터에만 할당하고 
랜에 속하는 호스트들은 사설 IP 주소를 받게 됩니다. 
이 때 사설 IP 주소는 원하는 주소를 할당할 수도 있고, 
DHCP(Dynamic Host Configuration Protocol) 기능을 이용해 자동으로 주소를 할당 할 수도 있습니다. 



## 3. IP 구조

IP 주소는 네트워크 ID와 호스트 ID로 구성되어 있습니다. 
이름그대로 네트워크 ID는 자신이 속한 네트워크가 어떤 네트워크인지를 나타내는 것이고, 
호스트 ID는 해당 네트워크 내에서 어떤 컴퓨터를 나타내는 것인지를 의미합니다. 
따라서 IP주소는 '나는 어떤 네트워크에 속하는 어떤 컴퓨터이다'를 나타내는 것입니다. 

앞서 IP주소는 네트워크 ID와 호스트 ID로 구분된다고 했습니다. 
그렇다면 어디까지가 네트워크 ID고 어디부터가 호스트 ID일까요? 
이는 조정할 수 있습니다. 네트워크 ID부분을 크게 사용할수도 있고, 반대로 호스트ID 부분을 크게 사용할수도 있습니다. 

이처럼 네트워크 ID 부분의 크기를 나누는 것을 클래스 개념으로 나눈다라고 표현합니다. 

클래스 | 내용
-------|-------
A 클래스 | 대규모 네트워크
B 클래스 | 중간 규모 네트워크
C 클래스 | 소규모 네트워크
D 클래스 | 멀티캐스트 주소
E 클래스 | 연구 및 특수용도 주소 

지금부터 위 클래스에 대해 알아보겠습니다. 

<center><img src="/assets/images/os/network-basic/network18.jpg" width="800"></center>


### 3.1. A 클래스

A 클래스는 처음 1옥텟(8비트)이 네트워크 ID이고 나머지 24비트가 호스트 ID입니다. 
이처럼 A 클래스는 호스트 ID 부분이 큰 것을 알 수 있습니다. 그만큼 배정해야할 호스트가 많다는 뜻이겠죠.  
A 클래스에 할당할 수 있는 호스트 수는 1677만 7214대 입니다. 

A 클래스의 1옥텟(8비트)의 범위는 1 ~ 127입니다. 
그리고 2 ~ 4 옥텟의 범위는 0 ~ 255 입니다. 



### 3.2. B 클래스

B 클래스는 처음 16비트가 네트워크 ID고 나머지 16비트가 호스트 ID입니다. 

B 클래스의 1 옥텟의 범위는 128~191 입니다. 그리고 최대 호스트 수는 6만 5534대 입니다. 


### 3.3. C 클래스

C 클래스는 처음 24비트가 네트워크 ID고 다음 8비트가 호스트 ID입니다. 
C 클래스의 1옥텟의 범위는 192~223 입니다. 최대 호스트 수는 254대 입니다. 

### 3.4. 공인, 사설 IP 주소

먼저 클래스별 공인 IP 주소 범위에 대해 알아봅니다. 

클래스 | 공인 IP 주소 범위
-------|------------------
A 클래스 | 1.0.0.0 ~ 9.255.255.255, 11.0.0.0 ~ 126.255.255.255 
B 클래스 | 128.0.0.0 ~ 172.15.255.255, 172.32.0.0 ~191.255.255.255
C 클래스 | 192.0.0.0 ~ 192.167.255.255, 192.169.0.0 ~ 223.255.255.255

이번에는 사설 IP 주소 범위에 대해 알아봅니다. 

클래스 |  IP 주소 범위
-------|------------------
A 클래스 | 10.0.0.0 ~ 10.255.255.255.255 
B 클래스 | 172.16.0.0 ~ 172.31.255.255
C 클래스 | 192.168.0.0 ~ 192.168.255.255

### 3.5. 네트워크 주소, 브로드캐스트 주소

IP 주소 중에는 네트워크 주소와 브로드캐스트 주소라는 특수한 주소가 있습니다. 
네트워크 주소는 호스트 ID가 10진수로 모두 0인 주소를 의미합니다. 
그리고 브로트캐스트 주소는  호스트 ID가 10진수로 모두 255인 주소를 의미합니다. 
이 주소들은 컴퓨터나 라우터의 IP로 할당할 수 없습니다.

이 네트워크 주소와 브로트캐스트 주소는 어디에 사용하는 것일까요? 
네트워크 주소는 이름 그대로 해당 네트워크를 대표하는 주소라고 생각하면 됩니다. 

<center><img src="/assets/images/os/network-basic/network19.jpg" width="800"></center>


그리고 브로트캐스트 주소는 해당 네트워크에 있는 컴퓨터 모두에게 데이터를 전송할때 사용되는 IP주소입니다. 


## 3.6. 서브넷(subnet)

지금까지 배운걸 잠시 정리하면 IP 주소는 규모에 따라 A,B,C클래스로 나눌 수 있고 
네트워크 주소와 브로드캐스트 주소가 있다고 했습니다. 
그런데 A클래스에 있는 컴퓨터들에게 브로드캐스트로 패킷을 전송한다고 생각해봅시다. 
A클래스에는 1677만 7214개의 컴퓨터가 있다고 했습니다. 한번에 1677만대의 컴퓨터에게 패킷을 보낸다고 생각하면 끔찍하네요. 

이럴때 서브넷(subnet)이라는 개념이 등장합니다. A클래스와 같은 대규모 네트워크를 작은 네트워크로 분할하는 것을 서브넷팅이라고 하고 
분할된 각각의 네트워크를 서브넷(subnet)이라고 합니다. 

<center><img src="/assets/images/os/network-basic/network20.jpg" width="800"></center>


따라서 서브넷을 사용할 경우 기존 네트워크 ID, 호스트 ID로 구성되었던 IP 주소가  네트워크 ID, 서브넷 ID, 호스트 ID로 
더 세부적으로 나눠지는 것입니다. 이 때  서브넷 ID는 기존의 호스트 ID의 일부를 서브넷 ID로 사용하는 것입니다. 

그렇다면 서브넷 ID는 IP주소 중 몇번째 비트부터 인지 어떻게 알수 있을까요? 
이를 나타내기 위한 것이 서브넷 마스크 입니다. 
서브넷 마스크를 보면 네트워크 ID와 호스트 ID를 구분할 수 있습니다. 

클래스 | 서브넷 | 프리픽스 표기
-------|--------|--------------
A 클래스 | 255.0.0.0 | /8
B 클래스 | 255.255.0.0 | /16
C 클래스 | 255.255.255.0 | /24


## 4. 라우터

이번에는 네트워크 계층의 핵심 장비인 라우터(router)에 대해 알아봅니다. 
라우터는 서로다른 네트워크끼리 통신할때 필요하다고 했습니다. 

<center><img src="/assets/images/os/network-basic/network21.jpg" width="800"></center>


동일한 스위치에 연결되어 있는 컴퓨터들은 동일한 네트워크에 속합니다. 
그리고 라우터는 서로다른 네트워크를 연결해줍니다. 
즉, 그림에서 라우터는 두 개의 네트워크를 연결하고 있는 것입니다. 

<center><img src="/assets/images/os/network-basic/network22.jpg" width="800"></center>


반대로 위 그림처럼 두개의 스위치에 연결되어 있는 각각의 네트워크를 
스위치로 연결하면 이는 2개의 네트워크가 아닌 1개의 네트워크 입니다. 

<center><img src="/assets/images/os/network-basic/network23.jpg" width="800"></center>


라우터를 사용하면 서로 다른 네트워크간 통신이 가능하다고 했습니다. 
예를 들어 보겠습니다. 
컴퓨터 1이 다른 네트워크에 존재하는 컴퓨터4 로 패킷을 보낸다고 했을 때 
이를 전송하려면 라우터의 IP 주소가 필요합니다. 
이처럼 네트워크의 출입구 설정을 기본 게이트웨이(default gateway)라고 합니다. 

컴퓨터1은 컴퓨터4가 어디 있는지 모릅니다. 따라서 우선 기본 게이트웨이인 라우터 주소로 데이터를 보냅니다. 
그 다음은 어떻게 될까요? 라우터가 일단 컴퓨터 1의 데이터를 받았다고 합시다. 
다음 단계는 라우터가 컴퓨터4로 보내야합니다. 
이 때 필요한 것이 라우팅 테이블(routing table) 입니다.

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

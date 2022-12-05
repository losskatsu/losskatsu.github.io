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

먼저 버츄어 박스를 실행합니다. 

<center><img src="/assets/images/os/raspberrypi/vminstall/01.png" width="800"></center>

그리고 위와 같이 머신 -> 새로만들기를 클릭합니다.


<center><img src="/assets/images/os/raspberrypi/vminstall/02.JPG" width="800"></center>

그리고 위 사진과 같이 운영체제의 종류와 버전을 설정해줍니다. 
기본값은 윈도우로 되어 있는데 리눅스로 바꿔줍니다. 

<center><img src="/assets/images/os/raspberrypi/vminstall/03.JPG" width="800"></center>

그리고 메모리 크기를 설정해줍니다. 기본이 1024인데 만약 본인이 좀더 많이 사용하고 싶다면 조절할 수 있습니다. 
나머지는 기본설정 그대로 갑니다.

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


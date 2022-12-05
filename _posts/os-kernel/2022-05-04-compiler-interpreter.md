---
title: "[리눅스] 컴파일러 vs 인터프리터 차이" 
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

# [리눅스] 컴파일러 vs 인터프리터 차이


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
|[OSI4계층](https://losskatsu.github.io/os-kernel/network-basic05/) | | [flask한글요청](https://losskatsu.github.io/programming/py-flask-korean/) | |[도커기초](https://losskatsu.github.io/it-infra/docker02/)|
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

**관련 링크**

* [bash란? #!/bin/bash의 의미 ](https://losskatsu.github.io/os-kernel/bash/)
* [bashrc와 bash_profile의 차이](https://losskatsu.github.io/os-kernel/bashrc/)
* [컴파일러와 인터프리터의 차이](https://losskatsu.github.io/os-kernel/compiler-interpreter/)

## 1. 컴파일러(compiler)

컴파일러(compile)는 특정 프로그래밍 언어로 쓰여있는 문서를 다른 프로그래밍 언어로 옮기는 언어 변역 프로그램을 말합니다. 
예를 들어 C로 작성한 소스코드가 있다고 하면 컴파일러는 이를 어셈블리 언어와 같은 다른 언어로 번역해줍니다. 
이때, C로 작성한 소스코드는 고급 프로그래밍 언어라고 하며, 어셈블리 언어는 저급 프로그래밍 언어라고 합니다. 
즉, 컴파일러는 고급 프로그래밍 언어를 저급 프로그래밍 언어로 바꿔주는 역할을 하며, 
컴파일 되기 전 코드를 원시코드(source code)라고 하며, 컴파일 된 이후의 코드를 목적코드(object code)라고 합니다. 

<center><img src="/assets/images/os/compiler/compiler02.png" width="800"></center>

즉, 원시코드는 컴파일러의 인풋이 되는 것이고 목적코드는 컴파일러의 아웃풋이 되는 것입니다. 
정확히 말하면 목적코드(object code)는 머신 코드(machine code)의 실행가능한 버전이라고 생각하면 됩니다.

## 2. 인터프리터(interpreter)

인터프리터(interpreter)란 프로그래밍 언어의 원시코드를 바로 실행하는 컴퓨터 프로그램을 말합니다. 
앞서 원시코드는 고급 프로그래밍 언어라고 했는데, 인터프리터는 원시코드의 내용을 한번에 한줄씩 읽어들여서 실행합니다. 

<center><img src="/assets/images/os/compiler/compiler03.png" width="800"></center>

인터프리터의 장점은 컴파일 단계를 거칠 필요가 없다는 장점이 있지만 컴파일러를 사용한 것보다 느리다는 단점이 있습니다.

## 3. 컴파일러 vs 인터프리터

컴파일러나 인터프리터 둘다 영어와 같은 인간의 언어로 작성한 코드를 컴퓨터가 이해할 수 있도록 변환시킨다는 점에서는 같습니다. 
그러나 둘 사이에는 다음과 같은 차이가 있습니다. 

먼저 인터프리터는 소스 코드를 한 줄씩(one statement) 해석하지만, 
컴파일러는 전체 프로그램 코드(entire program code)를 스캔하고 코드 전체를 통째로 목적코드로 한번에 변환 시킵니다. 

그리고 인터프리터는 소스 코드를 해석하는데는 적은 시간이 걸리지만 실행 시간은 느립니다. 
반면 컴파일러는 소스코드를 해석하는데는 많은 시간이 걸리지만 실행 시간은 빠릅니다. 

인터프리터 언어의 종류에는 루비, 파이썬 등이 있고 
컴파일 언어의 종류에는 C, C++ 등이 있습니다. 



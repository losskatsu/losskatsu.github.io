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

---
title: "[네트워크] 로드밸런서(loadbalancer)의 개념" 
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

# 로드밸런서의 개념


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

* [운영체제와 커널의 차이](https://losskatsu.github.io/os-kernel/diff-kernel-os/)
* [bash란? #!/bin/bash의 의미 ](https://losskatsu.github.io/os-kernel/bash/)
* [bashrc와 bash_profile의 차이](https://losskatsu.github.io/os-kernel/bashrc/)
* [컴파일러와 인터프리터의 차이](https://losskatsu.github.io/os-kernel/compiler-interpreter/)
* [리다이렉션, 파이프의 개념](https://losskatsu.github.io/os-kernel/linux-redirection/)
* [크론탭(crontab)을 이용한 작업 스케쥴링](https://losskatsu.github.io/os-kernel/crontab/)
* [AWS EC2 유저 추가](https://losskatsu.github.io/os-kernel/aws-add-user/)


## 1. 서론

주어진 서버에 너무나 많은 트래픽이 몰린다면 이를 어떻게 처리해야할까요? 
이번 포스팅에서는 로드밸런서의 개념에 대해 알아보겠습니다.


## 2. 로드밸런서(loadbalancer)란?

주어진 서버에 너무나 많은 트래픽이 몰린다면 이를 어떻게 처리해야할까요? 
이럴 때는 다수의 서버를 구축하고 수많은 트래픽을 여러 서버로 분산시켜주는 기술이 필요합니다. 
이때 사용되는 기술을 로드밸런싱(loadbalancing)이라고 하고, 
로드밸런싱을 하는데 필요한 장치 또는 기술을 로드밸런서(loadbalancer)라고 합니다. 
이번 포스팅에서는 로드밸런서의 개념에 대해 알아보겠습니다.


## 3. 로드밸런싱 알고리즘

로드밸런싱 알고리즘은 크게 다음과 같은 종류가 있습니다. 

### 3.1. 라운드로빈 방식(round robin method)

라운드로빈 방식은 다수의 서버에 순서대로 요청을 할당하는 방식입니다. 

### 3.2. 최소 연결 방식(least connection method)

요청이 들어온 시점에 연결 수가 가장 적은 서버에 할당하는 방식입니다. 

### 3.3. IP 해시 방식(IP Hash Method)

요청을 할당할 때 클라이언트의 IP 주소를 해시함수를 통해 해싱해서 그 결과를 통해 할당하는 방식을 의미합니다.


## 4. 로드밸런서의 종류

로드 밸런서는 크게 하드웨어 로드밸런서와 소프트웨어 로드밸런서로 나뉩니다.

### 4.1. 하드웨어 로드밸런서

하드웨어 로드밸런서는 하드웨어 장비를 활용해 로드밸런싱합니다. 

### 4.2. 소프트웨어 로드밸런서

소프트웨어 형식으로 로드밸런서를 구축하는 경우 클라우드를 사용하는 경우, 해당 서비스에서 제공하는 
로드밸런서를 활용할수도 있습니다. 
예를 들어, AWS는 Elastic Load Balancing(ELB)라는 로드밸런싱 서비스를 제공합니다. 
또하나의 방법은 직접 구축하하는 것인데 nginx를 통해 로드밸런서를 만들 수 있습니다. 


# 5. nginx로 로드밸런서 만들기

## 5.1. 라운드로빈 방식

```bash
http {
    upstream myapp1 {
        server srv1.example.com;
        server srv2.example.com;
        server srv3.example.com;
    }

    server {
        listen 80;

        location / {
            proxy_pass http://myapp1;
        }
    }
}
```

위와 같은 방식으로 nginx 설정파일을 수정해 로드밸런싱을 할 수 있습니다. 
위 코드는 80번 포트로 들어온 요청을 srv1, srv2, srv3으로 로드밸런싱하는 코드입니다. 
위 코드에서는 로드밸런싱 알고리즘을 지정하지는 않았는데 디폴드 방식은 라운드로빈 방식입니다. 


## 5.2. 최소 연결 방식


```bash
    upstream myapp1 {
        least_conn;
        server srv1.example.com;
        server srv2.example.com;
        server srv3.example.com;
    }
```

만약 로드밸런싱 알고리즘을 최소 연결방식으로 지정하고 싶다면 위와 같이 설정해줍니다.  
최소 연결 방식으로 지정하면 이미 힘들어하고 있는 서버에게 더 많은 요청을 주지는 않습니다. 
이미 수많은 요청을 처리하느라고 바쁜 서버보다는 상대적으로 널널한 서버에게 요청을 주는 방법이죠.


## 5.3. ip hash 방식

앞서 실습했던 라운드로빈 방식이나 최소 연결 방식은 동일한 클라이언트가 여러번 요청을 보냈을 때 
다수의 요청을 모두 동일한 서버가 응답해준다는 보장은 없습니다. 
만약 특정 클라이언트는 특정 서버가 응답해주는 것을 보장해주고 싶을 때는 ip 해시 방식을 사용합니다.

```bash
upstream myapp1 {
    ip_hash;
    server srv1.example.com;
    server srv2.example.com;
    server srv3.example.com;
}
```

만약 로드밸런싱 알고리즘을 ip hash 방식으로 적용하고 싶다면 위와 같은 코드를 작성해줍니다. 
ip hash 방법을 활용하면 클라이언트의 ip 주소를 해싱한 값을 키(key)로 활용해 어떤 서버가 응답해줄 것인지를 정합니다. 


## 5.4. 가중치 적용 방식

```bash
    upstream myapp1 {
        server srv1.example.com weight=3;
        server srv2.example.com;
        server srv3.example.com;
    }
```

혹은 위와 같은 코드로 특정 서버에 가중치를 줄 수도 있습니다.

## 5.5. 파일 수정이 끝났다면?

```bash
service nginx reload
```

파일을 수정했다면 nginx를 재가동 시킵시다. 

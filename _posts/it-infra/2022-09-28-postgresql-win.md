---
title: "[PostgreSQL] 윈도우에 PostgreSQL 설치하기"
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

# [PostgreSQL] 윈도우에 PostgreSQL 설치하기

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

## 참고 링크  

### DB

* [MySQL 윈도우에 설치하기](https://losskatsu.github.io/it-infra/mysql-install-win/)
* [MySQL 간단 정리, 우분투, 맥에 설치 하기](https://losskatsu.github.io/it-infra/mysql-index/)
* [맥 OS에 MySQL 설치](https://losskatsu.github.io/it-infra/mysql-install-mac/)
* [파이썬, MySQL 연동](https://losskatsu.github.io/programming/py-db-conn/)
* [데이터베이스에서 널(null)과 공백의 차이](https://losskatsu.github.io/it-infra/db-null/)
* [우분투에 PostgreSQL 설치](https://losskatsu.github.io/it-infra/postgresql-ubuntu/)
* [윈도우에 PostgreSQL 설치](https://losskatsu.github.io/it-infra/postgresql-win/)


### 백엔드  

* [(1-1)MySQL에 데이터베이스, 테이블 생성하기](https://losskatsu.github.io/it-infra/mysql-create-db/)
* [(1-2)장고, MsSQL 연결하기](https://losskatsu.github.io/it-infra/mssql-django-conn/)
* [(1-2)장고, MySQL 연결하기](https://losskatsu.github.io/it-infra/mysql-django-conn/)
* [(1-3)장고 inpectdb로 DB 데이터 model.py로 만들기](https://losskatsu.github.io/it-infra/django-inspectdb/)
* [(1-4)장고로 MySQL에 있는 데이터 웹상에서 보여주기](https://losskatsu.github.io/it-infra/django-read-data/)
* [(1-5)장고로 MySQL에 데이터 insert 하기](https://losskatsu.github.io/it-infra/django-post-data/)
* [(1-6)장고로 MySQL에 데이터 수정(put) 하기](https://losskatsu.github.io/it-infra/django-put-data/)

### 프론트엔드  

* [(2-1)기본 리액트 프로젝트 생성](https://losskatsu.github.io/frontend/react-basic-setup/)
* [(2-2)리액트 카테고리 레이어 헤더 만들기](https://losskatsu.github.io/frontend/react-category/)
* [(2-3)장고 API 서버에 요청해서 자료 받아오기(GET)](https://losskatsu.github.io/frontend/react-request-api-django/)
* [(2-4)장고 API 서버에 요청해서 자료 받아오기(GET)](https://losskatsu.github.io/frontend/react-request-post/)  


## 1. PostgreSQL 설치하기(2022.09.28 수정)

본 예제는 윈도우11 환경에서 실행했습니다.

먼저 다음 url에 접근합니다.  

[https://www.postgresql.org/download/](https://www.postgresql.org/download/)   


<center><img src="/assets/images/infra/postgresql/psql01.png" width="800"></center>  


위와 같은 화면에서 windows를 클릭합니다. 

<center><img src="/assets/images/infra/postgresql/psql02.png" width="800"></center>  


그리고 위 화면에서 download the installer를 클릭합니다. 

<center><img src="/assets/images/infra/postgresql/psql03.png" width="800"></center>  

그러면 위와 같은 다운로드 화면이 나타나는데 윈도우 쪽을 클릭해서 다운로드 해줍니다. 
다운로드 용량은 313MB 정도 되는데 네트워크 환경에 따라 시간이 걸릴 수 있습니다. 
다운로드를 완료하면 해당 파일을 실행해 줍니다. 

<center><img src="/assets/images/infra/postgresql/psql04.png" width="800"></center>  

그러면 위와 같은 설치 마법사가 실행되는데 next를 눌러줍시다. 

<center><img src="/assets/images/infra/postgresql/psql05.png" width="800"></center>  

위와 같은 설치 경로가 나타나면 건드리지 말고 next를 눌러줍시다.

<center><img src="/assets/images/infra/postgresql/psql06.png" width="800"></center>  

그러면 postgreSQL 구성 요소 중 무엇을 설치할지 선택하라고 뜨는데, 여기서는 자신이 원하는 것을 선택합시다. 
저는 변경없이 모두 설치하겠습니다.

<center><img src="/assets/images/infra/postgresql/psql07.png" width="800"></center>  

그리고 PostgreSQL의 데이터를 저장할 디렉토리를 선택하라고 뜨는데 건들지 말고 그냥 next 눌러줍시다. 

<center><img src="/assets/images/infra/postgresql/psql08.png" width="800"></center>  

그러면 위와 같이 postgres 계정의 비밀번호를 설정하라고 뜨는데, 자신이 원하는 비밀번호를 입력합시다. 
저는 귀찮아서 그냥 1234라고 설정했습니다. 

<center><img src="/assets/images/infra/postgresql/psql09.png" width="800"></center>  

다음은 포트 설정 화면입니다. PostgreSQL의 기본포트는 5432 포트입니다. 
가급적 변경하지 말고 next 눌러줍니다. 

<center><img src="/assets/images/infra/postgresql/psql10.png" width="800"></center>  

다음은 locale을 설정하는 화면인데 저는 변경하지 않고 next를 눌러주겠습니다. 

<center><img src="/assets/images/infra/postgresql/psql11.png" width="800"></center>  

설치 준비가 모두 끝났습니다. 설치해줍니다. 

<center><img src="/assets/images/infra/postgresql/psql12.png" width="800"></center>  

next를 눌러줍니다. 

<center><img src="/assets/images/infra/postgresql/psql13.png" width="800"></center>  

그러면 설치가 시작 됩니다. 


<center><img src="/assets/images/infra/postgresql/psql14.png" width="800"></center>  

설치가 완료되면 위와 같은 화면이 뜹니다. 
Finish를 눌러 설치를 마치겠습니다. 

<center><img src="/assets/images/infra/postgresql/psql16.png" width="800"></center>  
 
설치를 마쳤으면 시작을 누르고 sql shell(psql)을 실행하고 위와 같이 셋팅을 해줍니다. 
기본적으로 아무것도 입력하지 않고 엔터를 누르면 기본값이 설정되며, 마지막으로 비밀번호를 설정해줍니다.

<center><img src="/assets/images/infra/postgresql/psql15.png" width="800"></center>  

그후 시작을 누르고 pgadmin4를 실행하면 위와 같이 비밀번호를 설정하라고 뜨는데, 
자신이 원하는 비밀번호를 입력합니다. 
저는 또 1234로 설정하겠습니다. 

<center><img src="/assets/images/infra/postgresql/psql17.png" width="800"></center>  

그리고나서 위와 같이 데이터베이스를 연결해줍니다. 
Name은 자기가 원하는 이름으로 설정해줍니다.

<center><img src="/assets/images/infra/postgresql/psql18.png" width="800"></center>  

그리고 나머지 정보들도 입력해줍니다.

<center><img src="/assets/images/infra/postgresql/psql19.png" width="800"></center>  

그러면 위와 같이 연결되는 것을 알 수 있습니다. 

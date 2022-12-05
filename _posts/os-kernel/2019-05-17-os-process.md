---
title: "[운영체제] 프로세스(process)란(1)" 
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

# 프로세스(process)란?


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
|[OSI2계층](https://losskatsu.github.io/os-kernel/network-basic03/) | | [장고del](https://losskatsu.github.io/it-infra/django-del-data/)  | | [도커개념](https://losskatsu.github.io/it-infra/docker00/) |
|[OSI3계층](https://losskatsu.github.io/os-kernel/network-basic04/) | |  | | [도커설치](https://losskatsu.github.io/it-infra/docker01/) |
|[OSI4계층](https://losskatsu.github.io/os-kernel/network-basic05/) | |  | |[도커기초](https://losskatsu.github.io/it-infra/docker02/)|
|[OSI5,6,7계층](https://losskatsu.github.io/os-kernel/network-basic05/) | | [장고put](https://losskatsu.github.io/it-infra/django-put-data/) | | [도커이미지](https://losskatsu.github.io/it-infra/docker03/) |
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



예전 컴퓨터는 한번에 하나의 프로그램만 실행가능 했었다. 
그리고 실행중인 프로그램은 모든 시스템 자원을 사용했었다. 
시간이 흘러 현대의 컴퓨터는 여러 프로그램을 메모리에 올리고 동시에 실행이 가능하다. 
여기서 프로세스(process)라는 개념이 탄생하는데, 여러 프로그램 중 실행중인 프로그램을 프로세스라고 한다. 
현대 개발자는 프로세스는 작업 단위로 생각한다. 
그러므로 시스템은 프로세스의 집합이라고 생각할 수 있다. 
OS는 시스템 코드 뿐만 아니라 유저가 실행한 코드도 실행한다. 

## 프로세스 개념

운영체제에서 논의되는 쟁점들은 모두 CPU activity와 관련이 있다. 그것이 배치 잡(batch job)이던, 
유저 프로그램(user program)이나 태스크(task)던 말이다. 
심지어 유저프로그램 하나만 놓고봐도 유저는 여러가지 프로그램을 동시에 실행시킨다. 
예를들어 웹브라우저를 켜고, 워드프로세스 실행하고, 노래를 듣는 것 처럼 말이다. 
이때 운영체제는 메모리 관리 같은 것을 도와준다. 
job이라는 용어와 process라는 용어는 함께 사용될 수 있다. 개인적으로는 process라는 용어를 선호하지만...

### 프로세스

서두에서 말했듯, 프로세스는 실행중인 프로그램이다. 
프로세스는 아래와 같은 공간을 포함한다. 

* 프로세스 스택(process stack): 임시 데이터를 담는 곳이다. 
* 데이터 섹션(data section): 전역 변수를 담는 곳.
* 힙(heap): 프로세스 실행 중 동적 할당되는 메모리 영역. 

프로그램 자체를 프로세스라고 혼동하지마라. 둘은 다르다. 
프로그램은 비활성 객체(passive entity)이다. 즉, 디스크안에서 명령문(instruction)을 포함하고 있다. 
마치 나 좀 실행해 주세요라고 말하는것처럼. 
반대로 프로세스는 활성 객체(active entity)이다. 프로그램은 실행가능한 파일이 메모리에 올라갈때 프로세스가 된다. 
두가지 프로세스는 하나의 같은 프로그램과 연관되있을수 있지만, 그럼에도 불구하고 그 두 프로세느는 분리된 실행순서로 고려된다. 
예를들어 한 유저가 똑같은 크롬 브라우저를 여러개 실행할 수 있다. 
각각의 프로세스는 각자의 데이터, 힙, 스택 부분을 따로 가진다. 

### 프로세스 상태(Process State)

* New: 프로세스 생성
* Running: 명령문(Instruction) 실행됨
* Waiting: 프로세스는 이벤트(I/O이나 시그널) 발생을 기다리는 중...
* Ready: 프로세스는 프로세서에 할당되기를 기다림
* Terminated: 프로세스 실행됨.

### 프로세스 컨트롤 블락(Process Control Block)

각 프로세스는 운영체제에 의해 PCB(process control block)로 표현된다. 
PCB는 각 프로세스에 관해 아래와 같은 정보를 포함한다. 
쉽게말해 PCB는 프로세스마다 다양한 정보를 저장하는 저장소라고 할 수 있다. 

* Process state: new, readyk, running, waiting 중 어떤 상태인지 나타냄
* Program counter: 해당 프로세스에 대해 다음 실행 예정인 명령문 주소를 담고 있는 레지스터
* CPU registers: 우리가 잘 알고 있는 그 레지스터.
* CPU-scheduling information: 프로세스 우선순위, 스케쥴링 큐, 파라미터에 대한 포인터
* 메모리 관리 정보: 페이지테이블, 세그먼터 테이블 과 같은 정보
* Accounting information: CPU 사용량, 시간 제한, account number, job 또는 프로세스 넘버.
* I/O status information: 해당 프로세스와 관련된 I/O 디바이스 정보

### 쓰레드(Threads)

프로세스는 싱글 쓰레드를 실행하는 프로그램이다. thread of execution을 줄여서 쓰레드(thread)라고 부른다.
예를들어, 프로세스가 워드프로그램을 실행할때, 명령문의 싱글쓰레드가 실행된다. 
컨트롤의 싱글 쓰레드는 프로세스가 한번에 하나의 테스크를 수행하게 한다. 
현대에는 프로세스의 개념을 확장시켜, 
하나의 프로세스가 다중 쓰레드(multiple threads)를 가져, 한가지 이상의 테스크를 동시에 수행하게 도와준다. 


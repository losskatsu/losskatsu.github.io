---
title: "프로그램, 바이너리, 프로세스, 스레드의 개념" 
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

# 프로그램, 바이너리, 프로세스, 스레드의 개념

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



## 1. 프로그램(program)

프로그램(program)은 실행 가능한 명령어(instruction)의 집합입니다. 
프로그램은 하드디스크와 같은 저장 장치에 저장되어 있지만 메모리에는 올라가 있지 않은 정적인 상태를 의미합니다. 
프로그램은 보통 디스크에 저장되어 컴파일된 바이너리 이미지 형태일 수도 있고, 
파이썬 스크립트 같이 해석되는(interpret) 고급어 형태일 수도 있습니다. 
프로그램으로 정의되는 범위는 넓은데, 
내 컴퓨터에 설치된 파워포인트 파일도 프로그램이고, 
내가 짠 "hello world" 출력하는 파이썬 스크립트도 프로그램 입니다. 
이 때 중요한 것은 디스크에 저장돈 실행 가능한 명령어의 집합인지 아닌지의 여부 입니다. 

<center><img src="/assets/images/os/process_thread/01.jpg" width="800"></center>


## 2. 바이너리(binary)

바이너리(binary)는 디스크와 같은 저장장치에 기록되어 있는 프로그램을 의미합니다. 
바이너리는 특정 운영체제 및 아키텍처에서 접근할 수 있는 형식으로 컴파일 되어 실행할 준비가 되었지만, 
아직 실행되지는 않은 프로그램을 의미합니다. 
컴파일 되었다는 것은 고급 언어를 기계어로 변환 했다는 의미입니다. 
바이너리는 흔히 프로그램을 지칭하며 때로는 애플리케이션을 의미하기도 합니다. 

## 3. 프로세스(process)

프로그램을 실행하는 순간 해당 파일은 컴퓨터 메모리에 올라가게 되는데, 
프로세스(process)란 메모리에 적재(load)되어 실행되고 있는 프로그램을 의미합니다. 
프로그램이 정적인 것과는 달리 프로세스는 메모리에 올라서 실제 실행 중인 프로그램을 일컫기 때문에 동적이라고 표현하기도 합니다.

<center><img src="/assets/images/os/process_thread/02.jpg" width="800"></center>

프로세스를 '프로그램의 인스턴스'라고 표현하기도 하는데 실제 객체 지향에서 사용하는 개념인 클래스와 인스턴스와 비교해보겠습니다. 
'프로그램:프로세스'의 관계와 '클래스:인스턴스' 관계의 공통점은 한 클래스가 여러 인스턴스를 생성할 수 있는 것처럼 
하나의 프로그램에서 생성되는 여러 프로세스가 동시에 존재할 수 있다는 것입니다. 
예를 들어, 메모장을 두 번 실행하고 파일 이름을 각각 1.txt, 2.txt라고 지으면 메모장이라는 하나의 프로그램에서 
1.txt, 2.txt라는 두 개의 인스턴스가 생성되는 것을 볼 수 있습니다. 

<center><img src="/assets/images/os/process_thread/03.jpg" width="800"></center>

반대로 차이점은 프로그램은 클래스처럼 다른 프로그램을 상속하지는 않는다는 것입니다. 

프로세스는 커널에 의해 직접 관리 되는데, 커널 메모리 안에는 관리하고 있는 프로세스에 대한 데이터들이 존재합니다. 
이 정보는 Process Control Block(PCB)라고 하는 자료구조 안에 포함되는데, 커널 프로세스를 제어하는데 필요한 정보들이 담겨 있습니다. 
PCB는 실행 가능 기계어 이미지, 실행 프로세스 메모리 주소 등과 같은 정보를 포함합니다. 

<center><img src="/assets/images/os/process_thread/04.jpg" width="800"></center>

앞서 커널 메모리 안에서 PCB 정보를 관리한다고 했는데, 이 때 커널 메모리 말고, 
유저가 사용하는 메모리 공간 상의 프로세스 정보는 다음 4가지 분류로 나뉩니다. 

(1) code: 프로그램의 실제 코드 저장 
(2) data: 전역변수, 정적 변수 저장
(3) heap: 동적 변수(함수 내 변수 등) 저장, 동적 할당시(new(), mallock() 등)
(4) stack: 임시 메모리 영역(지역 변수, 매개변수, 리턴값)

정리하면 프로세스는 실행 중인 프로그램이며, 
메모리에 적재되고 가상화된 메모리와 열린 파일 디스크립터, 연관된 커널 리소스 등을 포함해 일컫는 말입니다. 

## 4. 스레드(thread)

스레드는 영어로 thread라고 쓰며 thread를 영어 사전에서 검색하면 '실'이라는 뜻이 나옵니다. 
실제로 스레드를 그림으로 나타낼 때 실처럼 표현하기도 합니다. 
스레드(thread)는 프로세스 내에서 실행되는 흐름, 프로세스 내 실행단위를 의미합니다. 
예를 들어, 파이썬 스크립트에서 한줄 한줄 실행되는 흐름이 곧 스레드라고 할 수 있습니다. 
일반적으로 하나의 프로세스는 하나의 스레드로 시작되며 이를 메인스레드라고 합니다. 
스레드를 추가로 생성하지 않는 한 모든 프로그램은 메인 스레드에서 실행됩니다. 

코드에 비유하면 스레드는 코드내 선언된 함수들이 되고, 
메인 함수 또한 일종의 스레드라고 볼 수 있는 것입니다. 

스레드는 프로세스 내 실행단위라고 했습니다. 
프로세스는 스레드의 컨테이너입니다. 프로세스는 스레드의 정보를 담고 있는 것에 불과 합니다. 

<center><img src="/assets/images/os/process_thread/05.jpg" width="800"></center>

스레드는 운영체제의 프로세스 스케줄러에 의해 스케줄링 될 수 있는 최소한의 실행단위 입니다. 
각각의 스레드는 저마다의 가상화된 프로세서, 스택 등을 포함합니다. 
참고로 가상 프로세서는 스레드와 관련있으며 프로세스와는 무관합니다. 

## 5. 프로세스와 스레드의 관계

하나의 프로세스는 스레드를 하나 이상 포함합니다. 
싱글 스레드란 프로세스의 스레드가 1개이며, 해당 프로세스는 단일 실행단위를 가지며 한번에 하나만 한다는 뜻입니다. 
따라서 싱글 스레드 프로세스에서는 프로세스가 곧 스레드가 됩니다. 

프로세스는 운영체제로부터 독립된 시간, 공간 자원을 할당 받아 실행되는 반면, 
스레드는 한 프로세스 내에서 자원을 공유하면서 병렬적으로 실행됩니다. 
참고로 프로세스간 통신은 스레드간 통신 보다 어렵습니다. 

차이 | 프로세스 | 스레드 
-----|---------|--------
자원할당 | 실행시 새로운 자원 할당 | 프로세스 자원 공유
자원공유 | 서로 다른 프로세스는 자원을 공유하지 않음 | 동일 프로세스 내 스레드들은 스택을 제외한 나머지 세영역 공유
독립성 | 일반적으로 독립적 | 일반적으로 프레세스 하위 집합
주소 소유  | 별개의 주소 공간을 갖는다 | 주소 공간 공유함
통신 | 시스템이 제공하는 IPC 방법으로 통신 | 자유롭게 다른 스레드와 통신
컨텍스트 스위치 | 스레드보다 느림 | 프로세스보다 빠름

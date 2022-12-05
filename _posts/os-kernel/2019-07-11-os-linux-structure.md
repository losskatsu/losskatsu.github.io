---
title: "[운영체제] 리눅스 구조 정리" 
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

# [운영체제] 리눅스 구조 정리

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


## 1. 컴퓨터 시스템 개요

컴퓨터의 기본 요소는 CPU와 메모리. CPU는 메모리에 있는 내용을 읽고 연산 결과를 메모리의 다른 영역에 기록한다. 

**프로그램**: 사용자에게 필요한 하나의 처리(기능)로 정리한 것

일반적으로 OS는 여러가지 프로그램을 프로세스 단위로 실행. OS는 여러개의 프로세스를 동시에 실행 가능. 

**애플리케이션**: 사용자가 직접 사용 


## 2. 사용자 모드로 구현되는 기능

프로세스는 커널의 도움이 필요할 경우 시스템 콜을 통해 커널에 처리를 요청.

**시스템 콜의 종류**

* 프로세스 생성, 삭제
* 메모리 확보, 해제
* 프로세스 간 통산(IPC)
* 네트워크
* 파일 시스템 다루기
* 파일 다루기(디바이스 접근)

프로세스는 보통 사용자 모드로 실행되고 있지만 커널에 처리를 요청하고자 시스템 콜을 호출하면 CPU에서는 인터럽트 이벤트 발생. 
인터럽트 이벤트가 발생하면 CPU는 사용자 모드에서 커널 모드로 변경되며 요청한 내용을 처리하기 위해 커널은 동작하기 시작함. 

**strace**: 프로세스가 어떤 시스템 콜을 호출했는지 확인 가능.

```bash
$ strace -o hello.log ./hello
```

**sar**: 프로세스가 사용자 모드와 커널 모드 중 어느쪽에서 실행되고 있는지 비율 확인

```bash
$ sar -P ALL 1 1
```
이 때, 세번째 파라미터는 1초 단위로 측정(측정 시간 단위), 네번째 파라미터는 1회 측정(측정 횟수). 
%user + %nice = 사용자모드, %system = 커널모드. 
대체로 %system 수치가 크면 시스템에 과부하가 걸려있는 등 좋지 않은 상태를 뜻함. 
<br />

시스템 콜은 C언어 같은 고급언어에서는 호출이 불가능하다. 아케텍처에 의존하는 어셈블리 코드를 사용해 호출해야함. 
이러한 문제를 해결하기 위해 OS는 내부적으로 시스템 콜을 호출하는 일만 하는 함수를 제공하는 데, 이를 wrapper라고 한다. 

**ldd**: 프로그램이 어떤 라이브러리를 링크하고 있는지 확인

```bash
$ ldd /bin/echo
```

## 3. 프로세스 관리

**fork()**: 실행한 프로세스와 함께 새로운 프로세스 1개 생성. 같은 프로그램의 처리를 여러 개의 나눠서 처리함. 

**execve()**: 전혀 다른 프로그램 생성 시 사용. 

**엔트리포인트(entry point)**: 최초로 실행할 명령의 메모리 주소

리눅스의 실행파일은 ELF(Executable Linkable Format)이라는 형식 사용. 

**readelf**: ELF 형식의 각종 정보 확인 가능. -h옵션으로 시작 주소 획득 가능. 
-S 옵션으로 오프셋, 사이즈, 메모리맵 시작주소 확인 가능. 
결과에서 .text는 코드영역 정보, .data는 데이터 영역 정보를 의미  

```bash
$ readelf -h /bin/sleep
$ readelf -S /bin/sleep
```

## 4. 프로세스 스케줄러

프로세스 스케줄러(process scheduler)라는 기능은 여러개의 프로세스를 동시에 동작시킴. 
정확히는 동시에 동작시키는 것처럼 보이게한다. 

**타임슬라이스**: 하나의 CPU에 여러 개의 프로세스를 실행해야할 때 각 프로세스를 적절한 시간으로 쪼개서 번갈아 처리. 

**컨텍스트 스위치(context switch)**: 논리 CPU 상에서 동작하는 프로세스가 바뀌는 것을 의미. 
프로세스가 어떤 프로그램을 수행 중이더라도 타임 슬라이스를 모두 소비하면 발생. 

하이퍼스레드(hyperthread) 기능이 있으면 각 코어 내의 각각의 하이퍼스레드가 논리 CPU로 인식됨. 

**taskset**: -c옵션으로 논리 CPU를 지정하고 여기에서만 지정한 프로그램을 동작하게 할 수 있음. 

```bash
$ taskset -c 0 ./sched <동시에 동작하는 프로세스 수> <프로그램 동작 총시간> <데이터 수집 간격>
$ taskset -c 0 ./sched 1 100 1
```

결과를 저장하고 싶다면

```bash
$ taskset -c 0 ./sched 1 100 1 > 1core-1process.txt 
```

**스루풋(throughput)**: 단위 시간당 처리된 일의양 = 완료한 프로세스의 수 / 경과 시간

**레이턴시(latency)**: 각각의 처리가 시작부터 종료까지의 경과된 시간 = 처리 종료 시간 - 처리 시작 시간 

**로드밸런서**: 여러 개의 논리 CPU에 프로세스를 공평하게 분배해 주는 역할을 함. 

**ps -eo**: time, etime 필드는 프로세스 시작 부터 현재까지의 경과 시간과 사용시간 표시 

```bash
$ ps -eo pid,comm,time,etime
```

## 5. 메모리 관리

**free**: 시스템의 총 메모리 양과 사용중인 메모리 양 확인

```bash
$ free
```

**sar -r**: 메모리에 관한 통계 정보 확인. 두번째 파라미터는 단위 초 간격 

```bash
$ sar -r 1
```

프로세스가 생성된 뒤 메모리의 획득, 해제를 반복하면 메모리 단편화(memory fragmentation) 문제 발생. 
이와 더불어 여러가지 문제를 해결하기 위해 가상 메모리 기능 탑재. 

**가상 메모리**: 시스템에 탑재된 메모리를 프로세스가 직접 접근하지 않고 가상 주소라는 주소를 사용하여 
간접적으로 접근하도록 하는 방식. 

**가상 주소**: 프로세스에 보이는 메모리 주소. readelf 쳤을 때 나온 주소는 가상 주소임. 

**물리 주소**: 시스템에 탑재된 메모리의 실제 주소

**가상 주소 공간**: 주소에 따라 접근 가능한 범위 

참고로 프로세스로 부터 메모리에 직접 접근하는 방법, 
즉, 물리 주소에 직접적으로 접근하는 방법은 없음. 

**페이지 테이블**: 가상 주소에서 물리 주소로 변환하는 과정은 커널 내부에 보관되어 있는 페이지 테이블이라는 표를 사용함. 
가상 메모리는 전체 메모리를 페이지라는 단위로 나눠서 관리하고 있어서 변환은 페이지 단위로 이루어짐. 

**페이지 테이블 엔트리**: 페이지 테이블에서 한 페이지에 대한 데이터를 페이지 테이블 엔트리라고 부름. 
이 페이지 테이블 엔트리에는 가상 주소와 물리 주소의 대응 정보가 들어 있음. 

**페이지 폴트(page fault)**: 가상 주소가 물리 메모리에 매핑되지 않을때 발생함. 

**mmap()**: 리눅스 커널에 새로운 메모리를 요구하는 시스템 콜 호출 

**system()**: 첫번째 파라미터에 지정된 명령어를 리눅스 시스템에 실행함. 

* mmap() 함수는 페이지 단위로 메모리를 확보하지만 malloc() 함수는 바이트 단위로 메모리를 확보함. 
* 가상 주소공간은 프로세스 별로 만들어지며, 또한 페이지 테이블도 프로세스 별로 만들어짐. 

**디맨드 페이징(demand paging)**: 프로세스가 생성 될때, mmap() 시스템 콜로 프로세스에 메모리를 할당했을때의 단점이 존재함.
그게 뭐냐면, 확보한 메모리 중에는 프로세스가 종료할때까지 사용하지 않는 영역도 있기 때문에 메모리를 낭비하는 단점이 존재함. 
이러한 문제를 해결하기 위해 디맨드 페이징을 사용함. 
디맨드 페이징을 사용하면 프로세스의 가상 주소 공간 내의 각 페이지에 대응하는 주소는 페이지에 처음 접근할 때 할당 됨. 

**가상 메모리 확보했음**: 프로세스가 mmap() 함수 등을 이용해 메모리를 확보하는 것을 뜻함

**물리 메모리 확보했음**: 확보한 가상 메모리에 접근하여 물리 메모리를 확보하고 매핑하는 것. 

**가상 메모리 부족**: 프로세스가 가상 주소공간의 범위가 꽉 차도록 가상 메모리를 전부 사용한 뒤에도 가상 메모리를 더 요청했을 때 발생. 
가상 메모리 부족은 물리 메모리가 얼마가 남아있든 관계 없이 발생함. 

**물리 메모리 부족**: 시스템에 탑재된 물리 메모리를 전부 사용하면 발생. 
물리 메모리 부족은 프로세스의 가상 메모리가 얼마나 남아있느냐에 관계없이 발생함. 

3장에서 설명한 프로세스 생성에 사용된 fork() 시스템 콜도 가상 메모리의 방식을 사용해서 고속화됨. 
fork() 시스템콜을 수행할 때는 부모 프로세스의 메모리를 자식 프로세스에 전부 복사하지 않고 페이지 테이블만 복사함. 

**스왑(swap)**: 메모리 부족에 대응하는 장치이며, 스왑은 저장 장치의 일부를 일시적으로 메모리 대신 사용하는 방식임. 
구체적으로는 시스템의 물리 메모리가 부족한 상태가 되어 물리 메모리를 획득할 때, 
기존에 사용하던 물리 메모리의 일부분을 저장 장치에 저장하여 빈 공간을 만들어냄. 
이 때 메모리의 내용이 저장된 영역을 스왑 영역이라고 부름. 

시스템에서 스와핑이 자주 발생할 때에는 시스템을 다시 설계하는 것이 좋다. 서버에서 스와핑은 발생하지 않는게 좋다. 

**swapon --show**: 스왑 영역 확인

```bash
$ swapon --show
```

**free**: 스왑 영역 사이즈 확인

```bash
$ free
```

**sar -W**: 스와핑 발생 여부 확인

```bash
$ sar -W 1
```

## 6. 메모리 계층

**캐시 메모리(cache memory)**: 레지스터 안에서 계산하는 것과 메모리에 접근하는 것, 양쪽의 처리 시간의 차이를 메우는 데 필요. 
메모리에서 레지스터로 데이터를 읽어올 때는, 일단 캐시 메모리에 읽어온 뒤 같은 내용을 다시 레지스터로 읽어들임. 
이때 읽어오는 크기는 CPU에서 정한 캐시 라인 사이즈(cache line size)만큼임. 
캐시 메모리는 일반적으로 CPU에 내장되어 있지만 CPU 바깥에 있는 캐시메모리도 있음. 

케시 메모리는 L1, L2, L3 등과 같은 이름이 붙어 있는데, (L은 Level을 의미) 
가장 레지스터에 가깝고 용량이 적으며 빠른 것이 L1 캐시이다. 
번호가 늘어날수록 레지스터로부터 멀어지며 용량이 커지고 속도가 느려짐.  

## 7. 파일 시스템

리눅스에서는 저장 장치 안의 데이터에 접근할 때 일반적으로 직접 저장 장치에 접근하지 않고 편의를 위해 파일시스템을 통해 접근함. 
만약 메모리의 값을 저장장치에 저장했더라도 다음에 읽을 때는 데이터를 보관한 주소와 사이즈를 기억해야 찾을수 있음. 
이처럼, 어디에 어느 정도의 데이터가 있는지, 어디가 빈 영역인지 관리하는 방법이 파일시스템이다. 
파일시스템은 사용자에게 의미가 있는 하나의 데이터를 이름, 위치, 사이즈 등의 보조 정보를 추가하여 파일이라는 단위로 관리함. 

단순한 파일시스템의 사양은 다음과 같다. 
* 0기가바이트의 지점부터 파일의 리스트를 기록 
* 하나의 파일에 대해 이름, 장소, 사이즈라는 세 가지의 정보를 기록함. 

파일시스템에는 데이터와 메타데이터라는 두 종류의 데이터가 존재함.

* 데이터: 사용자가 작성한 문서나 사진, 동영상, 프로그램 등의 내용 
* 메타데이터: 파일의 이름이나 저장 장치 내에 위치 사이즈 등의 보조 정보 

**쿼터(quota)**: 파일시스템의 용량을 무제한으로 사용할 수 있다면 다른 용도로 사용할 용량이 부족하게 되는 일이 발생함. 
이런 상황을 피하기 위해 파일시스템의 용량의 용도별로 사용할수 있게 제한하는 기능을 쿼터라고 부름. 



참고: 실습과 그림으로 배우는 리눅스 구조, 다케우치 사토루

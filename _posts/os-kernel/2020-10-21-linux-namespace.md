---
title: "[리눅스] 네임스페이스(namespace) 개념" 
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

# 리눅스 - 네임스페이스(namespace)의 개념


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



## 1. 네임스페이스?

### 1.1. 개념

네임스페이스는 최근 유행하는 도커(docker)와 같은 컨테이너(container) 기반의 가상화 기술의 기반이 되는 기능(feature)입니다. 
네임스페이스는 동일한 시스템에서 별개의 독립된 공간을 격리된 환경에서 운영하는 가상화 기술입니다. 
이는 아파트가 각 호실별로 격리된 주거환경을 제공하는 것과 비슷한 개념으로 생각하면 됩니다. 

## 1-2. 하이퍼바이저와의 차이

네임스페이스는 하이퍼바이저(hypervisor)와 비슷하다고 생각할 수 있지만 차이가 있습니다. 
하이버바이저의 경우 하드웨어(hardware) 자체를 가상화합니다. 
하이퍼바이저는 하드웨어를 물리적으로 구분해서 가상화 한다고 생각할 수 있습니다. 
따라서 하이퍼바이저 위에 올라가는 게스트 OS는 서로 물리적으로 구분된 공간에서 돌아갑니다. 
그러나 네임스페이스는 하드웨어를 분리하지는 않습니다. 
동일한 OS 및 커널(kernel)을 깔고 그 위에서 돌아갑니다. 


## 2. 네임스페이스 확인

### 2-1. 프로세스 네임스페이스 확인

먼저 ```/proc```디렉토리를 보겠습니다. 
```/proc``` 디렉토리는 프로세스 정보가 있는 디렉토리이며, 컴퓨터를 켜기 전에는 빈 디렉토리 이지만
부팅하면서 내용물이 채워지는 디렉토리 입니다. 

1번 프로세스의 네임스페이스를 확인해보겠습니다. 

```bash
$ cd /proc/1/ns
$ sudo ls -al
합계 0
dr-x--x--x 2 root root 0  8월  2 08:58 .
dr-xr-xr-x 9 root root 0  7월 30 17:57 ..
lrwxrwxrwx 1 root root 0  8월  2 08:59 cgroup -> 'cgroup:[4026531835]'
lrwxrwxrwx 1 root root 0  8월  2 08:59 ipc -> 'ipc:[4026531839]'
lrwxrwxrwx 1 root root 0  8월  2 08:59 mnt -> 'mnt:[4026531840]'
lrwxrwxrwx 1 root root 0  8월  2 08:59 net -> 'net:[4026531992]'
lrwxrwxrwx 1 root root 0  8월  2 08:59 pid -> 'pid:[4026531836]'
lrwxrwxrwx 1 root root 0  8월  2 08:59 pid_for_children -> 'pid:[4026531836]'
lrwxrwxrwx 1 root root 0  8월  2 08:59 user -> 'user:[4026531837]'
lrwxrwxrwx 1 root root 0  8월  2 08:59 uts -> 'uts:[4026531838]'
```

## 3. 네임스페이스의 종류

리눅스 네임스페이스는 크게 6가지로 나눌수 있습니다. 
네임스페이스는 unshare라는 명령어를 통해 네임스페이스를 구성할 수 있습니다. 

### 3.1 UTS namespace

hostname을 네임스페이스 별로 분할 격리 시켜줍니다. 
이는 리눅스 시스템 콜 중 하나인 uname에서 utsname이라는 구조체에 정의된 식별자 중 노드네임(nodename)을 isolate 하는 것입니다. 

아래는 /usr/include/linux/utsname.h 내부 코드 입니다.

```c
#define __NEW_UTS_LEN 64

struct new_utsname {
  char sysname[__NEW_UTS_LEN + 1];
  char nodename[__NEW_UTS_LEN + 1];
  char release[__NEW_UTS_LEN + 1];
  char version[__NEW_UTS_LEN + 1];
  char machine[__NEW_UTS_LEN + 1];
  char domainname[__NEW_UTS_LEN + 1];
};
```

UTS 네임스페이스 사용법은 아래와 같이 unshare에 -u 옵션을 써서 사용합니다.  

```bash
$ unshare -u /bin/bash
```

예를 들면 아래와 같이 사용합니다. 

```bash
user@testcomputer:~$ hostname
testcomputer
user@testcomputer:~$ sudo unshare -u /bin/bash
root@testcomputer:~# hostname newhost
root@testcomputer:~# hostname 
newhost
root@testcomputer:~# exit
exit
user@testcomputer:~$ hostname
testcomputer
```

### 3.2 IPC namespace

IPC는 프로세스간 데이터를 주고받는 경로를 의미합니다. 
IPC 네임스페이스는 IPC 리소스를 분할 격리 시켜줍니다. 즉, 프로세스간 통신을 격리시킵니다. 
semaphore, file locking, mutex 와 같은 것에 대한 접근 제어를 제공합니다. 

### 3.3 PID namespace

PID(process ID)를 분할 관리합니다. 
PID 네임스페이스를 이용하면 하나의 시스템에서 동일한 PID가 2개인것처럼보이게 프로세스를 만들 수 있습니다. 

### 3.4 NS namespace

파일 시스템의 마운트(mount)지점을 분할하여 격리합니다.

### 3.5 NET namespace

네트워크 인터페이스, iptables 등 네트워크 리소스와 관련된 정보를 분할합니다. 

### 3.6 USER namespace

user와 group ID를 분할하고 격리합니다. 



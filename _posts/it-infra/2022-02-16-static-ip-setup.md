---
title: "[Infra] 초기 네트워크 설정 - dhcp, 고정 아이피, ssh 설치" 
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

# [Infra] 리눅스 초기 네트워크 설정 - dhcp, 고정 아이피, ssh 설치

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

본 작업은 우분투를 대상으로 
초기 설치 이후의 IP 설정에 대한 내용입니다. 

## 0. ip 확인
작업을 하기전에 ip 확인부터 합시다.

```bash
$ ip a
```

## 1. DHCP 서버로부터 자동으로 IP 받기

### 1-1. 우선 다음 커맨드를 입력해서  dhclient를 리뉴

```bash
$ sudo dhclient -r
```

### 1-2. 이제 ip를 받읍시다.

```bash
$ sudo dhclient
```

### 1-3. 이더넷에 ip를 받고 네트워크를 재시작

```bash
# ifdown eth0
# ifup eth0
# /etc/init.d/network restart
or
# /etc/init.d/network restart
```

## 2. 만약 1번이 안통하는 경우(dhcp 서버로부터 ip를 받을 수 없는 경우)

만약 dhcp 서버로부터 ip를 받을 수 없는 경우라면 수동으로 ip를 입력해야한다. 

### 2-1. 네트워크 인터페이스 확인

일단 서버에 어떤 네트워크 인터페이스가 있는지 확인해 봅시다

```bash
$ ip link
```

### 2-2. netplan 설정 파일 생성

netplan 설정 파일은 /etc/netplan 폴더에 위치하고 있음. 
혹시나 /etc/netplan 디렉토리가 없다면 다음 명령으로 생성합니다. 

```bash
$ sudo netplan generate
```

### 2-3. 설정 파일 확인 

```bash
# cat /etc/netplan/01-network-manager-all.yaml

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
```

### 2-4. 설정 파일 수정.

```bash
# sudo vi /etc/netplan/01-network-manager-all.yaml

# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: no
      addresses: [192.168.200.100/23]
      gateway4: 192.168.200.1
      nameservers:
              addresses: [168.126.63.1]
```

위 코드에서 hdcp4: no 라고 쓰써야되는데, 이는 dhcp로부터 자동으로 ip를 받지 않겠다는 것을 의미합니다. 
addresses는 사용할 ip인데, 보통 마지막을 100번으로 부여해서 사용하는 것 같습니다. 
gateway4는 말그대로 게이트웨이(라우터)를 의미하며 
nameservers는 dns 서버를 의미하는데 이는 kt냐 skt냐 lg냐에 따라 달라집니다. 
(아래 표를 보면 위 코드는 kt를 쓰는 곳이라는 것이라는 것을 알수있죠) 

```
KT 기본(168.126.63.1), 보조(168.126.63.2)
SKT 기본(210.220.163.82), 보조(219.250.36.130)
LG 기본(164.124.101.2), 보조(203.248.252.2)
```

### 2-5. 설정 반영

바꿨으면 반영합니다. 

```bash
# sudo netplan apply
```

### 2-6. 설정 반영 확인

```bash
$ ip addr
$ ip route
```

## 3. ssh 설치 및 권한 설정

### 3-1. open ssh server 설치

터미널에서 다음과 같이 open ssh server 설치 

```bash
$ sudo apt update
$ sudo apt install openssh-server
```

### 3-2. SSH server 실행

만약 ssh가 실행 중이면 다음과 같이 나옵니다. 

```bash
$ sudo systemctl status ssh

● ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2022-02-07 11:37:00 KST; 1 weeks 1 days ago
  Process: 25236 ExecReload=/bin/kill -HUP $MAINPID (code=exited, status=0/SUCCESS)
  Process: 25229 ExecReload=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
 Main PID: 1059 (sshd)
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/ssh.service
           └─1059 /usr/sbin/sshd -D
```

만약 실행중이 아니라면 다음과 같이 실행합니다. 

```bash
$ sudo systemctl enable ssh
$ sudo systemctl start ssh
```

### 3-3. 방화벽에 ssh 허용

방화벽에 22번포트(ssh)를 허용해줍시다. 

```bash
$ sudo ufw allow ssh
```

### 3-4. 방화벽에 ssh(22번 포트) 열린거 확인

```bash
$ sudo ufw status
```


### 4-5. 특정 ip 접속 허용

```bash
# vi /etc/hosts.allow

# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "rpcbind" for the
# daemon name. See rpcbind(8) and rpc.mountd(8) for further information.
#

sshd: 211.57.136.82
```

허용을 했으면 재시작을 해줍니다

```bash
# systemctl restart sshd
```


## 5. 아이디, 패스워드를 이용한 원격 접속 허용 

위 설정만하고 돌아간다면 아이디와 비밀번호를 이용한 원격 로그인이 안될수있다. 
만약 올바르게 아이디와 비밀번호를 입력해서 ssh 접속을 하려고 하는데 
permioon denied가 뜬다면 다음과 같이 파일을 수정하자.

```bash
$ sudo vim /etc/ssh/sshd_config
----파일 내용----
#PermitRootLogin prohibit-password
PermitRootLogin yes
...
PasswordAuthentication yes
```

파일을 수정했다면 재시작

```bash
$ sudo /etc/init.d/ssh restart
```

그리고 나서 ssh 접속을 해보자! 잘 될 것이다. 


### 부록: ssh 비활성화

```bash
$ sudo systemctl stop ssh
```

만약 부팅 중에 실행되지 않도록 하려면 다음 커맨드를 입력

```bash
$ sudo systemctl disable ssh
```

만약 부팅 중에 실행되게끔 하려면 다음 커맨드를 입력

```bash
$ sudo systemctl stop ssh
$ sudo systemctl enable ssh
```

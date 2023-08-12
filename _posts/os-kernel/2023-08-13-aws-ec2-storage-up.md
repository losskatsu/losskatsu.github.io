---
title: "[리눅스] AWS EC2 인스턴스 스토리지 용량 늘리는 법" 
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

# AWS 아마존 리눅스 유저 추가하고 password 접속 허용


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


## 1. AWS 사이트에서 인스턴스 용량 증가

AWS 사이트에서 인스턴스를 클릭해서 스토리지 용량을 클릭해서 증가시켜줍니다. 
저는 30G 까지 늘렸습니다. 

## 2. 인스턴스에 접속해서 작업하기 

약 3분정도 지난 후 인스턴스에 접속해서 디스크 현황을 파악합니다.

```bash
ubuntu@k8s-master:~$ lsblk
NAME     MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0      7:0    0  24.4M  1 loop /snap/amazon-ssm-agent/6312
loop1      7:1    0  55.6M  1 loop /snap/core18/2745
loop2      7:2    0  63.3M  1 loop /snap/core20/1879
loop3      7:3    0 111.9M  1 loop /snap/lxd/24322
loop4      7:4    0  53.2M  1 loop /snap/snapd/19122
loop5      7:5    0  53.3M  1 loop /snap/snapd/19457
loop6      7:6    0  55.7M  1 loop /snap/core18/2785
loop7      7:7    0  63.4M  1 loop /snap/core20/1974
loop8      7:8    0  24.8M  1 loop /snap/amazon-ssm-agent/6563
xvda     202:0    0    30G  0 disk
├─xvda1  202:1    0   7.9G  0 part /
├─xvda14 202:14   0     4M  0 part
└─xvda15 202:15   0   106M  0 part /boot/efi
```

위 결과를 보면 xvda가 30G로 늘어나 있는 것을 볼 수 있습니다. 
그리고 기존의 xvda1은 처음 설정 그대로인 7.9G인 것을 볼 수 있습니다. 

```bash
ubuntu@k8s-master:~$ sudo growpart /dev/xvda 1
CHANGED: partition=1 start=227328 old: size=16549855 end=16777183 new: size=62687199 end=62914527
```

위에서 확인한 xvda의 용량을 키워줍니다. 

```bash
ubuntu@k8s-master:~$ lsblk
NAME     MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0      7:0    0  24.4M  1 loop /snap/amazon-ssm-agent/6312
loop1      7:1    0  55.6M  1 loop /snap/core18/2745
loop2      7:2    0  63.3M  1 loop /snap/core20/1879
loop3      7:3    0 111.9M  1 loop /snap/lxd/24322
loop4      7:4    0  53.2M  1 loop /snap/snapd/19122
loop5      7:5    0  53.3M  1 loop /snap/snapd/19457
loop6      7:6    0  55.7M  1 loop /snap/core18/2785
loop7      7:7    0  63.4M  1 loop /snap/core20/1974
loop8      7:8    0  24.8M  1 loop /snap/amazon-ssm-agent/6563
xvda     202:0    0    30G  0 disk
├─xvda1  202:1    0  29.9G  0 part /
├─xvda14 202:14   0     4M  0 part
└─xvda15 202:15   0   106M  0 part /boot/efi
```

그리고 다시 `lsblk`로 디스크를 확인하면 xvda가 30G로 증가된 것을 볼 수 있습니다. 

```bash
ubuntu@k8s-master:~$ sudo resize2fs /dev/root

resize2fs 1.46.5 (30-Dec-2021)
Filesystem at /dev/root is mounted on /; on-line resizing required
old_desc_blocks = 1, new_desc_blocks = 4
The filesystem on /dev/root is now 7835899 (4k) blocks long.
```

그리면 이제 `resize2fs`를 활용해 파일 시스템의 크기를 변경해보겠습니다. 
`/dev/root`는 루트 파일 시스템을 의미하는데, 찾아보니까
`/dev/root`라고 입력해도 되고 `/dev/xvda1`이라고 입력해도 된다고 합니다. 


```bash
ubuntu@k8s-master:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        29G  7.4G   22G  26% /
tmpfs           483M  1.1M  482M   1% /dev/shm
tmpfs           194M  892K  193M   1% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
/dev/xvda15     105M  6.1M   99M   6% /boot/efi
tmpfs            97M  4.0K   97M   1% /run/user/1000
```

그리고 용량을 확인해보면 /dev/root가 29G로 증가된 것을 볼 수 있습니다. 

---
title: "[리눅스] AWS 아마존 리눅스 유저 추가하고 password 접속 허용" 
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


## 1. 서론?

처음에 AWS에 가입하고 EC2 인스턴스를 생성하게 되면 pem키를 생성하게 됩니다. 
그래서 EC2 인스턴스에 접속하려면 pem키를 이용해서 접속하게 되는데, 
이번 포스팅에서는 EC2 인스턴스에서 유저를 추가하고 pem키없이 패스워드 입력방식으로 접속할수 있게끔 작업해보겠습니다. 

## 2. pem 키를 이용한 초기 접속  

가장 처음 접속을 할 때는 pem 키를 이용해야 합니다. 
EC2 인스턴스 생성할 떄 pem키를 로컬에 받으셨을텐데 해당 파일의 경로와 파일이름을 이용해 다음과 같이 접속합니다. 

```bash
$ ssh -i {pem키 경로} ec2-user@{ip주소}
```

위와 같이 접속을 하는데 주의할 점은
유저 이름을 자신의 aws 아이디를 적는게 아니라 ec2-user라고 적어야한다는 점입니다. 
이는 각 운영체제 별로 이름이 정해져 있습니다. 
저는 AWS 아마존 리눅스 운영체제를 설치했으므로 ec2-user라는 이름이 설정되어 있습니다. 

운영체제 별 이름은 [다음](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/TroubleshootingInstancesConnecting.html)과 같이 정리할 수 있습니다.

운영체제 | 유저네임
---------|------
Amazon Linux AMI | ec2-user 
CentOS AMI | centos or ec2-user
Debian AMI | admin
Fedora AMI | fedora or ec2-user
RHEL AMI | ec2-user or root
SUSE AMI | ec2-user or root
Ubuntu AMI | ubuntu
Oracle AMI | ec2-user
Bitnami AMI | bitnami
otherwise | check AMI provider

## 3. user 추가 및 password 설정

일단 pem 키를 이용해 접속했지만 계속 이렇게 pem키로 접속하기는 불편합니다. 
따라서 추가적인 사용자를 추가하고 
패스워드 입력방식으로 ssh 접속할 수 있게끔 해보겠습니다. 
이를 위해 유저를 추가하고 비밀번호를 설정하겠습니다. 
새롭게 추가할 유저 이름을 abcde라고 하겠습니다.

```bash
# sudo -i
# sudo adduser abcde
# sudo passwd abcde

Changing password for user abcde
New password:
Retype new password:
passwd: all authentication tokens updated successfully.
```


## 4. sudoers 파일에 생성한 user 추가

sudoers 파일은 sudo 명령어와 관련된 권한을 설정하는 파일을 의미합니다.
우리가 앞서 추가한 유저명 abcde에 대한 내용을 sudoers 파일에 추가하겠습니ㅏㄷ. 

```bash
# sudo chmod u+w /etc/sudoers
```

먼저 ```/etc/sudoes``` 파일에 대해 유저에게 쓰기 권한을 추가하겠습니다. 
```u+w```에서 ```u```는 user를 의미하고 ```+```는 추가를 의미하며, 
```w```는 쓰기를 의미합니다. 

```bash
# sudo vim /etc/sudoers

abcde    ALL=(ALL:ALL)    ALL
```

쓰기 권한을 얻었으므로 sudoers 파일을 열어 가장 아래에 위와 같은 코드를 추가합니다. 


## 5. sshd_config 파일 설정 

이번에는 abcde로 접속할때 패스워드를 사용해서 접속할 수 있게끔 설정을 변경해보겠습니다. 

```bash
# sudo vim /etc/ssh/sshd_config

PasswordAuthentication yes
```

위 코드와 같이 vim으로 sshd_config 설정 파일을 열면 
중간쯤에 PasswordAuthentication라는 항목이 있고 기본값으로 No라고 설정되어 있을 겁니다. 
이를 yes로 바꿔줍시다. 

## 6. 서비스 재시작

```bash
# sudo service sshd restart

Redirecting to /bin/systemctl restart sshd.service
```

## 7. 새롭게 추가한 유저네임으로 ssh 접속해보기 

이제 모든 작업이 완료되었습니다. 
새롭게 추가한 유저네임 abcde로 ssh 접속을 해보겠습니다. 

```bash
$ ssh abcde@{ip주소}
```

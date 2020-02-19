---
title: "[Infra] AWS EC2 리눅스 AMI에 아파치(apache) 서버 설치하기" 
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

# AWS EC2 리눅스 AMI에 아파치(apache) 서버 설치하기

### 참고링크
* [아파치, 톰캣, 엔진엑스 차이](https://losskatsu.github.io/it-infra/webserver/)
* [아파치 서버 에러 로그 확인](https://losskatsu.github.io/it-infra/apache-error-log/)
* [SSL, CRS 인증 관련 정리](https://losskatsu.github.io/it-infra/ssl-auth/)


## 운영체제 확인하기

먼저 운영체제를 확인합시다. 저는 아마존 Linux AMI 를 사용하고 있습니다. 
명령어는 대부분 CentOS와 비슷합니다. 

```bash
$ cat /etc/issue
Amazon Linux AMI release 2018.03
Kernel \r on an \m
```

## 아파치(apache) 서버 설치

```bash
$ sudo yum install -y httpd
```


## 아파치 서버 시작

```bash 
$ sudo service httpd start
Starting httpd:         [  OK  ]
```

## 서버 잘 돌아가는지 확인

```bash
$ ps -ef | grep httpd
root     13298     1  0 06:27 ?        00:00:00 /usr/sbin/httpd
apache   13305 13298  0 06:27 ?        00:00:00 /usr/sbin/httpd
apache   13306 13298  0 06:27 ?        00:00:00 /usr/sbin/httpd
apache   13307 13298  0 06:27 ?        00:00:00 /usr/sbin/httpd
apache   13308 13298  0 06:27 ?        00:00:00 /usr/sbin/httpd
apache   13309 13298  0 06:27 ?        00:00:00 /usr/sbin/httpd
apache   13310 13298  0 06:27 ?        00:00:00 /usr/sbin/httpd
apache   13311 13298  0 06:27 ?        00:00:00 /usr/sbin/httpd
apache   13312 13298  0 06:27 ?        00:00:00 /usr/sbin/httpd
ec2-user 13342 12346  0 06:27 pts/0    00:00:00 grep --color=auto httpd

```

## 방화벽설정

### 1. (참고)CentOS 7 사용자일 경우(아마존 AMI 사용자이신 경우는 2로 가주세요~)

참고로 centOS 6에서는 iptables를 사용하며, centOS 7에서는 firewalld를 사용합니다. 

### 1-1.firewalld 설치

```bash
$ sudo yum install firewalld
```

### 1-2. 시스템에 등록 후 작동되도록 실행

```bash
$ systemctl unmask firewalld
$ systemctl enable firewalld
$ systemctl start firewalld
```

### 1-3. 방화벽설정

```bash
$ firewall-cmd --permanent --add-service=http
$ firewall-cmd --permanent --add-service=https
$ firewall-cmd --reload
```

## 2. AWS EC2 사용자이신 경우

AWS ec2 사용자이신 분들은 firewalld가 설치가 되지 않으실 겁니다. 
EC2는 웹콘솔로 접근하셔서 아래와 같은 절차를 진행해주세요. 

먼저 인스턴스 상태를 확인하시고 **보안그룹**을 봐주세요. 

![figure01](/assets/images/infra/aws_server/001.JPG){: width="500"}

거기서 **인바운드 규칙 보기**를 보시면 아직 22번 포트밖에 열려있지 않음을 보실수 있습니다. 
인바운드 규칙보기 옆에 launch-wizard-1를 누르셔서 설정을 변경합시다. 

![figure01](/assets/images/infra/aws_server/002.JPG){: width="500"}

인바운드탭에서 편집을 눌러주세요. 

![figure01](/assets/images/infra/aws_server/003.JPG){: width="500"}

거기서 규칙추가 누르시고 유형은 HTTP, 접근가능 사용자는 "0.0.0.0/0, ::/0" 이라고 입력해줍시다.

![figure01](/assets/images/infra/aws_server/004.JPG){: width="500"}

이제 마지막으로 웹사이트에 접속되는지 확인해봅시다. 

![figure01](/assets/images/infra/aws_server/010.jpg){: width="500"}

성공적으로 설치된 것을 보실 수 있습니다.

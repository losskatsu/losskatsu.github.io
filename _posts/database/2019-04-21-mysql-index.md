---
title: "[Infra] mysql 정리 " 
categories:
  - b
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

# mysql 정리

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


### 관련 링크  

* [MySQL 윈도우에 설치하기](https://losskatsu.github.io/it-infra/mysql-install-win/)
* [MySQL 간단 정리, 우분투, 맥에 설치 하기](https://losskatsu.github.io/it-infra/mysql-index/)
* [파이썬, MySQL 연동](https://losskatsu.github.io/programming/py-db-conn/)
* [데이터베이스에서 널(null)과 공백의 차이](https://losskatsu.github.io/it-infra/db-null/)

## jdbc url

> jdbc:mysql://IP주소:포트/DB명

## 1. Mysql 설치하기

### mysql 버전확인
```bash
$ mysql --version
```

### 1.1 맥에서 Mysql 설치하기
```bash
$ brew install mysql
```
비밀번호 설정
```bash
$ mysql_secure_installation
```
Mysql실행
```bash
$ mysql.server start
```
상태확인
```bash
$ mysql.server status
```
mysql실행정지
```bash
$ mysql.server stop
```
### 1.2 우분투에서 Mysql 설치하기 
```bash
$ sudo apt update
$ sudo apt install mysql-server
```
비밀번호 설정
```bash
$ sudo mysql_secure_installation
```

mysql서버 실행
```bash
$ service mysql start
```
mysql서버 상태확인
```bash
$ service mysql status
● mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2020-03-23 08:00:07 KST; 5min ago
 Main PID: 8182 (mysqld)
    Tasks: 29 (limit: 4915)
   CGroup: /system.slice/mysql.service
           └─8182 /usr/sbin/mysqld --daemonize --pid-file=/run/mysqld/mysqld.pid

 3월 23 08:00:07 cheolwon-910S3L-911S3L systemd[1]: Starting MySQL Community Server...
 3월 23 08:00:07 cheolwon-910S3L-911S3L systemd[1]: Started MySQL Community Server.
```

mysql 서버 종료
```bash
$ service mysql stop
```
종료후 상태확인
```bash
$ service mysql status
● mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: inactive (dead) since Mon 2020-03-23 08:06:50 KST; 2s ago
 Main PID: 8182 (code=exited, status=0/SUCCESS)

 3월 23 08:00:07 cheolwon-910S3L-911S3L systemd[1]: Starting MySQL Community Server...
 3월 23 08:00:07 cheolwon-910S3L-911S3L systemd[1]: Started MySQL Community Server.
 3월 23 08:06:49 cheolwon-910S3L-911S3L systemd[1]: Stopping MySQL Community Server...
 3월 23 08:06:50 cheolwon-910S3L-911S3L systemd[1]: Stopped MySQL Community Server.
```

## 2. mysql 기본 명령어

mysql접속
```bash
$ sudo mysql
# 또는
$ sudo mysql -u root -p 
```
### 2.1 DB 관련

DB목록보기
```bash
mysql> show databases; 
```
DB 선택
```bash
mysql> use db명;
```
DB 생성 
```bash
mysql> create database db명;
```
DB 삭제
```bash
mysql> drop database db명;
```
선택중인 DB확인
```bash
mysql> select database();
```
선택중인 user확인
```bash
mysql> select user(); 
```


### 2.2 테이블 관련

테이블 목록 확인
```bash
mysql> show tables;
```
테이블 구조 확인
```bash
mysql> desc 테이블명;
mysql> describe 테이블명;
mysql> explain 테이블명;
```

테이블 이름 변경
```bash
mysql> rename table 테이블명1 to 테이블명2;
```

테이블 삭제
```bash
mysql> drop table 테이블명; 
```

## mysql MMM 구조

MMM이란 Multi-Master replication Manager for MySQL의 줄임말로, 
기본적으로 한쪽이 마스터, 다른쪽이 슬레이브이지만 
이슈발생시 슬레이브가 마스터가 될 수 있는 이중화 구조 중 하나.



## mysql 인덱스(index)

### 책의 찾아보기와 비유

책의 마지막에 있는 "찾아보기"가 인덱스에 비유된다면 책의 내용은 데이터 파일에 해당한다고 볼 수 있다. 

* 찾아보기 : 페이지번호 = 인덱스 : 데이터파일에 저장된 레코드 주소
* DBMS도 데이터베이스 테이블의 모든 데이터를 검색해서 원하는 결과를 가져오려면 시간이 오래걸림. 
* 시간이 오래걸리므로, 칼럼값과 해당레코드가 저장된 주소를 키-값쌍(Key-Value pair)으로 인덱스를 만듦.
* 찾아보기와 인덱스의 공통점 = 정렬

### 자료구조와 비유

* 인덱스   
SortedList와 같은 자료구조, 저장되는 값을 항상 정렬된 상태로 유지하는 자료구조, 데이터가 저장 될때마다 항상 값을 정렬해야 하므로, 
저장하는 과정이 복잡하고 느리지만, 이미 정렬돼 있어서 아주 빨리 원하는 값을 찾아올 수 있음. 
즉, INSERT, UPDATE, DELETE 문장의 처리는 느리지만 
SELECT 문장은 매우 빠르게 처리할 수 있다. 결국, INSERT, UPDATE, DELETE 성능을 희생하는 대신 데이터 읽기 속도를 높이는 기능. 
즉, 인덱스 하나를 추가할 지 말지는 데이터의 저장 속도를 어디까지 희생할 수 있는지, 읽기 속도를 얼마나 더 빠르게 만들어야 하는지에 
따라 결정되야 한다. 

* 데이터파일     
ArrayList와 같은 자료구조, 저장되는 순서대로 유지하는 자료구조

### 인덱스의 구분

* 프라이머리 키(Primary key)  
레코드를 대표하는 칼럼의 값으로 만들어진 인덱스를 의미. 이 칼럼은 테이블에서 해당 레코드를 식별할 수 있는 기준값이 되기 때문에 
이를 식별자라고 부른다. 프라이머리키는 NULL값과 중복을 허용하지 않는다. 

* 보조 키(Secondary key)


참고자료 : real mysql

---
title: "[PostgreSQL] 우분투에 PostgreSQL 설치하고 둘러보기"
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

# [PostgreSQL] 우분투에 PostgreSQL 설치하고 둘러보기

## 참고 링크  

### DB

* [MySQL 윈도우에 설치하기](https://losskatsu.github.io/it-infra/mysql-install-win/)
* [MySQL 간단 정리, 우분투, 맥에 설치 하기](https://losskatsu.github.io/it-infra/mysql-index/)
* [맥 OS에 MySQL 설치](https://losskatsu.github.io/it-infra/mysql-install-mac/)
* [파이썬, MySQL 연동](https://losskatsu.github.io/programming/py-db-conn/)
* [데이터베이스에서 널(null)과 공백의 차이](https://losskatsu.github.io/it-infra/db-null/)
* [우분투에 PostgreSQL 설치](https://losskatsu.github.io/it-infra/postgresql-ubuntu/)


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

본 예제는 우분투 환경에서 실행했습니다.

```bash
$ sudo apt update
```

먼저 우분투 패키지를 업데이트 합니다. 


```bash
$ sudo apt install postgresql postgresql-contrib
```

위 명령어를 입력해 postgresql을 설치합니다. 
postgresql이 설치되면 자동으로 작동합니다.

```bash
$ sudo systemctl status postgresql.service
● postgresql.service - PostgreSQL RDBMS
     Loaded: loaded (/lib/systemd/system/postgresql.service; enabled; vendor preset: enabled)
     Active: active (exited) since Wed 2022-09-28 04:21:48 UTC; 1min 43s ago
    Process: 62002 ExecStart=/bin/true (code=exited, status=0/SUCCESS)
   Main PID: 62002 (code=exited, status=0/SUCCESS)
        CPU: 1ms

Sep 28 04:21:48 ip-172-31-40-144 systemd[1]: Starting PostgreSQL RDBMS...
Sep 28 04:21:48 ip-172-31-40-144 systemd[1]: Finished PostgreSQL RDBMS.
```

위 명령어는 postgresql이 정상적으로 작동되고 있는지 확인하는 코드입니다. 
active 라고 되어 있는거 보니 제대로 작동 되고 있는 것을 알 수 있습니다. 


## 2. PostgreSQL 롤(role)과 기초 사용

### 2.1. 롤(role)이란

PostgreSQL에는 인증과 관련해서 "롤(roles)"이라는 개념이 있습니다. 
롤은 유닉스 시스템에서 유저와 그룹의 개념이라고 생각할 수 있습니다. 

일단 PostgreSQL을 설치하면 기본적으로 postgres라는 유저 계정이 생성되게 되는데, 
이 postgres라는 계정이 디폴트 Postgres role입니다. 
그렇다면 postgres라는 계정을 이용해 postgreSQL를 사용해 보겠습니다. 


### 2.2. PostgreSQL 사용해보기

일단 계정을 postgres로 변경해줍니다.

```bash
$ sudo -i -u postgres
```

위 명령어를 입력하면 postgres 계정으로 변경되며 PostgreSQL을 사용할 수 있습니다. 

```bash
$ psql
psql (14.5 (Ubuntu 14.5-0ubuntu0.22.04.1))
Type "help" for help.

postgres=# \q
$
```

psql 커맨드를 입력하면 PostgreSQL이 실행되게 됩니다. 
만약 종료하고 싶다면 위와 같이 역슬래시+q를 입력하면 됩니다.


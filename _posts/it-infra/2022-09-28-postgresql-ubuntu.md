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


## 2. 롤(role) 개념과 PostgreSQL 시작하기

### 2.1. 롤(role)이란

PostgreSQL에는 인증과 관련해서 "롤(roles)"이라는 개념이 있습니다. 
롤은 유닉스 시스템에서 유저와 그룹의 개념이라고 생각할 수 있습니다. 

일단 PostgreSQL을 설치하면 기본적으로 postgres라는 유저 계정이 생성되게 되는데, 
이 postgres라는 계정이 디폴트 Postgres role입니다. 
그렇다면 postgres라는 계정을 이용해 postgreSQL를 사용해 보겠습니다. 
이는 다음과 같이 두가지 방법이 있습니다.


### 2.2. PostgreSQL 시작하기(1)

일단 계정을 postgres로 변경해줍니다.

```bash
$ sudo -i -u postgres
postgres@server$
```

위 명령어를 입력하면 postgres 계정으로 변경되며 PostgreSQL을 사용할 수 있습니다. 

```bash
postgres@server$ psql
psql (14.5 (Ubuntu 14.5-0ubuntu0.22.04.1))
Type "help" for help.

postgres=# \q
postgres@server$ exit
$
```

psql 커맨드를 입력하면 PostgreSQL이 실행되게 됩니다. 
만약 종료하고 싶다면 위와 같이 역슬래시+q를 입력하면 됩니다.
그리고 나서 exit를 입력하면 postgre 계정에서 로그아웃하게 됩니다.

### 2.3. PostgreSQL 시작하기(2)

위 방법으로는 유저를 postgres로 변경하고 psql을 실행함으로써 
총 두 단계의 과정을 거쳤는데, 
다음 커맨드를 사용하면 더 편하게 PostgreSQL을 사용할 수 있습니다.

```bash
$ sudo -u postgres psql
psql (14.5 (Ubuntu 14.5-0ubuntu0.22.04.1))
Type "help" for help.

postgres=# \q
$
```

위 방법을 사용하면 역슬래시q 이후에 exit를 별도로 입력할 필요가 없어서 편합니다. 


### 2.4. 비밀번호 설정하기 

postgres 계정의 비밀번호를 설정하는 방법은 다음과 같습니다. 
저는 간단하게 1234라고 설정했습니다. 

```bash
$ sudo -u postgres psql postgres
[sudo] password for :
psql (14.5 (Ubuntu 14.5-0ubuntu0.22.04.1))
Type "help" for help.

postgres=# \password
Enter new password for user "postgres":
Enter it again:
postgres=# \q
```

### 2.4. 데이터베이스 확인하기

postgres 계정으로 데이터베이스를 확인해보겠습니다. 

```bash
postgres=# \list
                              List of databases
   Name    |  Owner   | Encoding | Collate |  Ctype  |   Access privileges
-----------+----------+----------+---------+---------+-----------------------
 postgres  | postgres | UTF8     | C.UTF-8 | C.UTF-8 |
 template0 | postgres | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres          +
           |          |          |         |         | postgres=CTc/postgres
 template1 | postgres | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres          +
           |          |          |         |         | postgres=CTc/postgres
(3 rows)
```

위와 같이 역슬래시list를 입력하면 데이터베이스를 확인할 수 있는데, postgres라는 계정명과 동일한 데이터베이스를 확인할 수 있습니다. 
postgreSQL에서는 롤이 생성되면 롤 이름과 동일한 데이터베이스가 생성되는 것을 알 수 있습니다.

### 2.5. 새로운 롤 생성하기 

새로운 롤을 생성하고 싶다면 postgres계정으로 다음 커맨드를 입력하면 됩니다. 

(방법1)
```bash
postgres@server~:$ createuser --interactive
Enter name of role to add: testuser1
Shall the new role be a superuser? (y/n) y
```

(방법2)
```bash
$ sudo -u postgres createuser --interactive
```

위와 같이 롤을 생성한다면 롤이 추가되었는지 확인해보겠습니다. 

```bash
$ sudo -i -u postgres
postgres@server~:$ psql
psql (14.5 (Ubuntu 14.5-0ubuntu0.22.04.1))
Type "help" for help.

postgres=# \du
                                   List of roles
 Role name |                         Attributes                         | Member of
-----------+------------------------------------------------------------+-----------
 postgres  | Superuser, Create role, Create DB, Replication, Bypass RLS | {}
 testuser1 | Superuser, Create role, Create DB                          | {}
```

## 3. 외부 접근 허용하기 

`/etc/postgresql/14/main` 경로에 존재하는 pg_hba.conf 파일을 다음과 같이 수정합니다.

```bash
# Database administrative login by Unix domain socket
local   all             postgres                                peer

# TYPE  DATABASE        USER            ADDRESS                 METHOD

# "local" is for Unix domain socket connections only
local   all             all                                     peer
# IPv4 local connections:
host    all             all             127.0.0.1/32            scram-sha-256
host    all             all             0.0.0.0/0               scram-sha-256
# IPv6 local connections:
host    all             all             ::1/128                 scram-sha-256
# Allow replication connections from localhost, by a user with the
# replication privilege.
local   replication     all                                     peer
host    replication     all             127.0.0.1/32            scram-sha-256
host    replication     all             ::1/128                 scram-sha-256
```

그리고 다음과 같이 postgresql을 다시 시작합니다.

```bash
$ sudo systemctl restart postgresql
```

그리고 netstat으로 확인을 해봅니다. 

```bash
$ netstat -ntlp | grep 5432
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 0.0.0.0:5432            0.0.0.0:*               LISTEN 
```

## 3. 데이터는 어디에 저장될까?

PostgreSQL에서 데이터는 다음 두 경로에 저장됩니다. 

```bash
/var/lib/postgresql
/etc/postgresql
```

그렇다면 위 경로에 어떤 데이터가 존재하는지 알아봅시다. 

먼저 `/var/lib/postgresql` 경로부터 확인해보겠습니다. 

```bash
server@host:/var/lib/postgresql/14/main# ll
total 92
drwx------ 19 postgres postgres 4096 Sep 28 05:56 ./
drwxr-xr-x  3 postgres postgres 4096 Sep 28 04:21 ../
-rw-------  1 postgres postgres    3 Sep 28 04:21 PG_VERSION
drwx------  5 postgres postgres 4096 Sep 28 04:21 base/
drwx------  2 postgres postgres 4096 Sep 28 05:57 global/
drwx------  2 postgres postgres 4096 Sep 28 04:21 pg_commit_ts/
drwx------  2 postgres postgres 4096 Sep 28 04:21 pg_dynshmem/
drwx------  4 postgres postgres 4096 Sep 28 07:51 pg_logical/
drwx------  4 postgres postgres 4096 Sep 28 04:21 pg_multixact/
drwx------  2 postgres postgres 4096 Sep 28 04:21 pg_notify/
drwx------  2 postgres postgres 4096 Sep 28 04:21 pg_replslot/
drwx------  2 postgres postgres 4096 Sep 28 04:21 pg_serial/
drwx------  2 postgres postgres 4096 Sep 28 04:21 pg_snapshots/
drwx------  2 postgres postgres 4096 Sep 28 05:56 pg_stat/
drwx------  2 postgres postgres 4096 Sep 28 04:21 pg_stat_tmp/
drwx------  2 postgres postgres 4096 Sep 28 04:21 pg_subtrans/
drwx------  2 postgres postgres 4096 Sep 28 04:21 pg_tblspc/
drwx------  2 postgres postgres 4096 Sep 28 04:21 pg_twophase/
drwx------  3 postgres postgres 4096 Sep 28 04:21 pg_wal/
drwx------  2 postgres postgres 4096 Sep 28 04:21 pg_xact/
-rw-------  1 postgres postgres   88 Sep 28 04:21 postgresql.auto.conf
-rw-------  1 postgres postgres  130 Sep 28 05:56 postmaster.opts
-rw-------  1 postgres postgres  107 Sep 28 05:56 postmaster.pid
```

다음으로는 `/etc/postgresql` 경로를 보겠습니다. 

```bash
server@host:/etc/postgresql/14/main# ll
total 68
drwxr-xr-x 3 postgres postgres  4096 Sep 28 05:54 ./
drwxr-xr-x 3 postgres postgres  4096 Sep 28 04:21 ../
drwxr-xr-x 2 postgres postgres  4096 Sep 28 04:21 conf.d/
-rw-r--r-- 1 postgres postgres   315 Sep 28 04:21 environment
-rw-r--r-- 1 postgres postgres   143 Sep 28 04:21 pg_ctl.conf
-rw-r----- 1 postgres postgres  5080 Sep 28 05:54 pg_hba.conf
-rw-r----- 1 postgres postgres  1636 Sep 28 04:21 pg_ident.conf
-rw-r--r-- 1 postgres postgres 29029 Sep 28 05:50 postgresql.conf
-rw-r--r-- 1 postgres postgres   317 Sep 28 04:21 start.conf
```


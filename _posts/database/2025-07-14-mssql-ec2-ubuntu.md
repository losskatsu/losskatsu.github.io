---
title: "[database] MSSQL 데이터베이스, EC2 우분투에 설치하고 SSMS로 접속하기"
categories:
  - database
tags:
  - database
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# MSSQL, 우분투에 설치하고 SSMS로 접속하기

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


## 1. EC2 인스턴스 생성

본 실습에서 할 내용은 AWS EC2에 MSSQL을 설치하고 로컬 SSMS에서 EC2의 MSSQL에 접속할 예정입니다. 
이를 위해 가장 먼저 해야할 일은 EC2인스턴스를 만드는 일입니다. 
다음과 같이 EC2 인스턴스를 만들어줍니다. 

<center><img src="/assets/images/infra/mssql-ubuntu/01.png" width="800"></center>

저는 t2.medium으로 만들었는데, 최소 사양만 맞춰주면 문제없습니다. 
MSSQL을 설치하기 위한 최소 사용은 디스크 용량 20G, RAM 2기가입니다. 
그리고 운영체제를 선택할 때 주의해야하는데, 
2025년 7월 기준, 가장 최근 우분투 버전은 noble인데, noble에서는 MSSQL을 설치할 수 없고, 
jammy 버전까지만 지원가능합니다. 따라서 운영체제를 선택할때 저처럼 jammy 버전으로 선택해주세요.


<center><img src="/assets/images/infra/mssql-ubuntu/02.png" width="800"></center>

여러가지 설정을 마치면 위와 같이 t2.medium 인스턴스를 만든 것을 볼 수 있습니다. 

<center><img src="/assets/images/infra/mssql-ubuntu/03.png" width="800"></center>

인스턴스를 만든김에 인바운드 규칙도 추가해서 1433 포트를 미리 열어주겠습니다. 
MSSQL은 기본적으로 1433포트를 사용합니다. 



## 2. MSSQL 설치

이번절에서는 MSSQL을 설치해보겠습니다. git bash나 putty 등을 활용해 ec2 인스턴스에 접속해 다음과 같이 설치과정을 진행해보겠습니다.  
참고로 MSSQL 설치 과정은 [MSSQL 설치 홈페이지](https://learn.microsoft.com/ko-kr/sql/linux/quickstart-install-connect-ubuntu?view=sql-server-ver17&tabs=ubuntu2004)에서 확인할 수 있습니다. 

```bash
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.5 LTS
Release:        22.04
Codename:       jammy
```

먼저 운영체제가 확실히 jammy 버전으로 설치되어 있는지 확인해보겠습니다. 
위와 같은 커맨드를 입력했을 떄 jammy가 아닌 noble이 나온다면 인스턴스를 잘못 생성한 것이니 다시 만드셔야합니다. 

```bash
$ sudo apt update
Hit:1 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu noble InRelease
Get:2 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]
Get:3 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu noble-backports InRelease [126 kB]
Get:4 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu noble/universe amd64 Packages [15.0 MB]
Get:5 http://security.ubuntu.com/ubuntu noble-security InRelease [126 kB]
...중략
```

위와 같이 apt update를 진행 해줍니다. 

```bash
$ sudo apt install net-tools
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  net-tools
...중략
```

그리고 기본적으로 net-tools를 설치가 잘되는지 확인합니다. 

```bash
$ curl -fsSL https://packages.microsoft.com/keys/microsoft.asc | sudo gpg --dearmor -o /usr/share/keyrings/microsoft-prod.gpg
```

다음은 MSSQL 설치를 위해 필요한 key 정보를 위와 같이 추가합니다. 

```bash
$ curl -fsSL https://packages.microsoft.com/config/ubuntu/22.04/mssql-server-preview.list | sudo tee /etc/apt/sources.list.d/mssql-server-preview.list
deb [arch=amd64,arm64,armhf signed-by=/usr/share/keyrings/microsoft-prod.gpg] https://packages.microsoft.com/ubuntu/22.04/mssql-server-preview jammy main
```

다음은 위와 같이 레포지토리 정보를 추가해줍니다. 

```bash
$ sudo apt-get update
$ sudo apt-get install -y mssql-server
```

이제 설치할 준비가 모두 끝났습니다. 위와 같은 코드로 설치해줍니다. 

```bash
$ sudo /opt/mssql/bin/mssql-conf setup
/opt/mssql/lib/mssql-conf/mssqlsettings.py:550: SyntaxWarning: invalid escape sequence '\.'
  if re.search("^[a-zA-Z0-9\.;-]+$", setting_value):
Locale C not supported. Using en_US.
Choose an edition of SQL Server:
  1) Evaluation (free, no production use rights, 180-day limit)
  2) Enterprise Developer (free, no production use rights)
  3) Standard Developer (free, no production use rights)
  4) Express (free)
  5) Web (PAID)
  6) Standard (PAID)
  7) Enterprise (PAID) - CPU core utilization restricted to 20 physical/40 hyperthreaded
  8) Enterprise Core (PAID) - CPU core utilization up to Operating System Maximum
  9) I bought a license through a retail sales channel and have a product key to enter.
 10) Standard (Billed through Azure) - Use pay-as-you-go billing through Azure.
 11) Enterprise Core (Billed through Azure) - Use pay-as-you-go billing through Azure.

Details about editions can be found at
https://go.microsoft.com/fwlink/?LinkId=2109348

Use of PAID editions of this software requires separate licensing through a
Microsoft Volume Licensing program.
By choosing a PAID edition, you are verifying that you have the appropriate
number of licenses in place to install and run this software.
By choosing an edition billed Pay-As-You-Go through Azure, you are verifying
that the server and SQL Server will be connected to Azure by installing the
management agent and Azure extension for SQL Server.

Enter your edition(1-10): 2
The license terms for this product can be found in
/usr/share/doc/mssql-server or downloaded from: https://aka.ms/useterms

The privacy statement can be viewed at:
https://go.microsoft.com/fwlink/?LinkId=853010

Do you accept the license terms? [Yes/No]:Yes


Choose the language for SQL Server:
(1) English
(2) Deutsch
(3) Español
(4) Français
(5) Italiano
(6) 日本語
(7) 한국어
(8) Português
(9) Руѝѝкий
(10) 中文 – 简体
(11) 中文 （繝体）
Enter Option 1-11: 7
Enter the SQL Server system administrator password:
Confirm the SQL Server system administrator password:
Configuring SQL Server...

ForceFlush feature is enabled for log durability.
[INFO] [StartUp::OpenDBsAndRecover]: In Startup, FEnableResilientBufferPoolExtensionEnabled() = [0]. IsRBPEXSupportedNonHyperscaleEdition() = [0]. IsSubCore = [0].
[INFO][DBDDLAgent::AttachDatabase] Starting Database Attach.
TDS initialization result: 0.
SQLSERVR_SSL_CERTIFICATE_DNS_OR_SUBJECT_NAME environment variable was not set as SSL cert is self signed or untrusted.
[INFO][DBDDLAgent::AttachDatabase] Starting Database Attach.
[Auditing][SecAuditPkg::AutoStartAuditSessions] Entered function.
Created symlink /etc/systemd/system/multi-user.target.wants/mssql-server.service → /lib/systemd/system/mssql-server.service.
Setup has completed successfully. SQL Server is now starting.
```

설치가 끝났으면 위와 같이 설정을 해줘야하는데 차례대로 다음과 같은 질문을 합니다. 
몇번 버전을 사용할거니?(저는 2번 선택), 약관 동의하니(Yes), 어떤 언어 사용할거니?(저는 7번 한국어 선택), 비밀번호 입력, 비밀번호 확인 순서입니다. 
위 순서를 거치면 설치가 완료됩니다. 


```bash
$ systemctl status mssql-server --no-pager
● mssql-server.service - Microsoft SQL Server Database Engine
     Loaded: loaded (/lib/systemd/system/mssql-server.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2025-07-14 02:03:05 UTC; 35s ago
       Docs: https://docs.microsoft.com/en-us/sql/linux
   Main PID: 3154 (sqlservr)
      Tasks: 83
     Memory: 413.7M
        CPU: 10.477s
     CGroup: /system.slice/mssql-server.service
             ├─3154 /opt/mssql/bin/sqlservr
             └─3183 /opt/mssql/bin/sqlservr
```

그리고 시스템 가동을 확인했을 때 위와 같이 active 상태이면 성공입니다. 


```bash
$ sudo ss -tulnp | grep 1433
tcp   LISTEN 0      128               0.0.0.0:1433      0.0.0.0:*    users:(("sqlservr",pid=3183,fd=79))
tcp   LISTEN 0      128                     *:1433            *:*    users:(("sqlservr",pid=3183,fd=78))
```

그리고 외부에서 접속할 것이므로 위와 같이 외부로 1433 포트가 열려있으면 성공입니다. 


## 3. 로컬 SSMS에서 EC2 우분투 MSSQL로 접속

모든 설치가 완료되었으면 로컬에서 SSMS를 실행해 다음 정보로 접속해줍니다. 

<center><img src="/assets/images/infra/mssql-ubuntu/04.png" width="800"></center>

## 4. ubuntu에 설치된 MSSSQL을 다룰때 주의사항

우분투에 설치된 MSSQL을 통해 데이터베이스 테이블 등을 만들때 주의할 점이 있습니다. 
예를 들어 CSV 파일을 insert burk 한다고 했을때,  윈도우 PC에서는 다음과 같이 인코딩을 cp949로 설정해도 가능했습니다. 

```bash
BULK INSERT Customers
FROM 'C:/경로/Customers.csv'
WITH (
    FORMAT = 'CSV',
    FIRSTROW = 2,
    FIELDTERMINATOR = ',',
    ROWTERMINATOR = '\n',
    CODEPAGE = '949'
);
```

그러나 우분투에서 작업할 때는 우선 기본적으로 ```CODEPAGE = '949'``` 옵션을 사용할 수 없습니다. 
우분투에서는 utf8만 가능하므로, 파일의 인코딩이 ```cp949```나 ```euc-kr```일 경우 ```utf8```로 바꿔줘야합니다.  

```bash
# iconv -f euc-kr -t utf-8 -c issuedelay_ukey.tsv -o issuedelay_ukey-utf8.tsv
# sed '1s/^\xEF\xBB\xBF//' issuedelay_ukey-utf8.tsv > issuedelay_ukey-clean.tsv
# sudo chown mssql:mssql issuedelay_ukey-clean.tsv
```

위와 같은 코드를 통해 ```utf8```로 변경해야합니다. 

```bash
# cat issuedelay_ukey-clean.tsv | head
```

그리고 한글이 잘 보이는지 꼭 위와 같은 코드로 확인해야합니다. 

```bash
CREATE TABLE test01.dbo.IssueDelay_Ukey (
    STAT_DT NVARCHAR(100),
    SVSET_ORD_NUM NVARCHAR(100),
    SVSET_REQ_NUM NVARCHAR(100),
    POST_ORG_ID NVARCHAR(100),
...(중략)
```
그리고 테이블을 만들때도 ```VARCHAR```가 아닌 ```NVARCHAR```로 만들어줘야합니다. 


```bash
BULK INSERT test01.dbo.IssueDelay_Ukey
FROM '/var/opt/mssql/data/issuedelay_ukey-clean.tsv'
WITH (
    FIELDTERMINATOR = '\t',
    ROWTERMINATOR = '\n',
    FIRSTROW = 2
);
```

그리고 테이블에 데이터를 넣을때는 위와 같은 코드를 참고해주세요.

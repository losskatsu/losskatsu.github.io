---
title: "[리눅스] 리눅스(linux) 명령어 모음" 
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

# 리눅스(linux) 명령어 모음

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


---------------------------------------------

## ps - 현재 실행 중인 프로세스 확인 

```bash
$ ps -ef | grep apache
```

ps 옵션 | 설명 
--------|------
-e | 모든 프로세스 출력
-f | Full 포맷  
-eo | etime, time 필드는 프로세스의 시작부터 현재까지의 경과시간과 사용시간 표시

```bash
$ ps -eo pid,comm,time,etime
```
* vsz 필드: 가상 메모리 양
* rss 필드: 확보된 물리 메모리 양
* maj_flt + min_flt 필드: 프로세스 생성시부터의 페이지 폴트 횟수

---------------------------------------------

## 파이프(|) - 출력 결과를 필터링

| wc -l : 줄 수 확인

```bash
$ cat hello.log | wc -l  
```

---------------------------------------------

## grep - 파일 패턴을 스캔

* 하위폴더 포함, 존재하는 모든 파일에서 원하는 단어를 찾아주는 명령어

```bash
$ grep -rni [검색어] [경로명 또는 파일명]
```

* r : 하위 디렉토리까지 검색
* n : 파일내 몇번째 라인인지 표시 
* i : 검색어 대소문자 구분없이 검색

* 예) 현재 디렉토리이하 abc라는 문자열 포함되는 경우 검색

```bash
$ grep -rni "abc" ./
```

---------------------------------------------

## find - 하위폴더에 존재하는 파일 찾아줌

```bash
$ find [검색 디렉토리] -iname [파일명]
```

* -name : 대소문자 구분하여 파일명 검색
* -iname : 대소문자 구분하지 않고 파일명 검색 

---------------------------------------------

## 리다이렉션(>) - 출력 결과를 파일로 저장 


기호 | 의미
-----|-----
\>  | 결과를 파일로 저장
\>> | 결과를 기존 파일에 데이터 추가
\<  | 파일 데이터를 입력  

예를 들어,

```bash
$ ls -al > abc.txt
```
라고 하면 ls -al을 입력 후 출력되는 결과물을 abc.txt라는 파일에 저장하라는 뜻. 

리눅스 파일 디스크립터

기호 | 의미
-----|-----
0  | 표준입력
1 | 표준출력
2  | 표준에러 

```bash
$ nohup ./a.sh 1>a.log 2>&1 &
```

* 1>a.out 의 의미는 표준출력을 a.log 파일에 쓰는 것
* 2>&1 표준에러를 표준출력 장소에 전달하라는 의미, 즉 표준에러를 a.out에 씀.
* &의 의미는 백그라운드 실행  

---------------------------------------------

## strace

strace : 프로세스가 어떠한 시스템 콜을 호출했는지 확인

```bash
$ strace -o hello.log ./hello
$ cat hello.log
```

* -T 옵션을 붙이면 시스템 콜 처리에 걸린 시간을 마이크로 초 단위로 측정 가능
```bash
$ strace -T -o hello.log ./hello
$ cat hello.log
```

---------------------------------------------

## sar

sar : 프로세스가 사용자 모드와 커널 모드 중 어느쪽에서 실행되고 있는지 비율 확인

```bash
$ sar -P ALL 1 1
```

sar -r : 메모리에 관련된 통계 정보 확인
sar -r 1 : 1초 간격으로 확인

```bash
$ sar -r 1
```

sar -B 1 :1초 간격으로 페이 


* 세번째 파라미터 : 측정 시간 단위(1초마다 측정)
* 네번째 파라미터 : 측정 횟수 단위(1회 측정)

---------------------------------------------

## getppid()

getppid() : 부모 프로세스의 프로세스 ID 획득

---------------------------------------------

## ldd

ldd : 프로그램이 어떤 라이브러리에 링크하고 있는지 확인

```bash
$ ldd /bin/echo
```

---------------------------------------------

## OS가 제공하는 프로그램

* 시스템 초기화: init
* OS 동작 바꿈: sysctl, nice, sync
* 파일 관련: touch, mkdir
* 텍스트 데이터 가공: grep, sort, uniq
* 성능 측정: sar, iostat
* 컴파일러: gcc
* 스크립트 언어 실행환경: perl, python, ruby
* 셸: bash
* 윈도우 시스템: X

---------------------------------------------

## taskset

```bash
$ taskset -c 0 ./hello 1 100 1
```

* -c : 논리 cpu지정. 예제에서는 cpu 0번을 지정하였다.
* 첫번째 파라미터: 동시에 동작하는 프로세스 수
* 두번째 파라미터: 프로그램 동작 총 시간
* 세번째 파라미터: 데이터 수집 간격


---------------------------------------------

## 시스템에 탑재된 논리 cpu 갯수 확인

```bash
$ grep -c processor /proc/cpuinfo
```

---------------------------------------------

## free

free: 시스템의 총 메모리양과 사용 중인 메모리 양 확인

---------------------------------------------

## tail

tail: 파일 끝부분 n줄을 출력해줌(기본값 10줄), 보통 로그 확인할 때 쓰인다

옵션 | 뜻
-----|----
-f | 파일 마지막 라인 10개 실시간으로 계속 출력
-n | n라인만큼 출력

```bash
$ tail -f -n 100 abc.log   
```
abc.log 파일의 마지막 100라인 출력 


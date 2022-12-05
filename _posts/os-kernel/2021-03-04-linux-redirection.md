---
title: "[리눅스] 리다이렉션(redirection), 파이프(pipe)의 개념" 
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

# 리눅스 - 리다이렉션(redirection), 파이프(pipe)의 개념


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



## 1. 표준 스트림(standard stream)

리눅스에서 프로그램 실행시 다음과 같이 기본적으로 3개의 스트림이 자동적으로 열립니다. 

- 표준 입력 스트림(standard input, stdin)
- 표준 출력 스트림(standard output, stdout)
- 표준 에러 스트림(standard error, stderr)

표준 입력 스트림은 입력을 위한 스트림이고, 표준 출력 스트림은 출력을 위한 스트림, 표준 에러 스트림은 에러메시지 출력을 위한 스트림입니다. 

> 스트림: 유닉스 계열 운영체제에서 프로그램(프로세스)과 주변 기기 사이에 미리 연결된 입출력 통로.

스트림의 정의를 보면 마지막 단어가 '입출력 통로라고 되어 있습니다. 
통로라면 무엇인가를 이어준다는 의미인데, 스트림은 무엇을 이어줄까요? 
먼저 표준 입력 스트림부터 보겠습니다. 

<center><img src="/assets/images/os/redirection/01.jpg" width="800"></center>

표준 입력 스트림은 입력을 위한 스트림이라고 했습니다. 
보통 '입력'하면 생각나는 장치는? 키보드 입니다. 
입력스트림은 키보드로부터 시작되서 프로세스까지의 스트림을 의미합니다. 

그렇다면 표준 출력스트림, 표준 에러 스트림은 어떨까요? 
이 둘은 결과물 출력이냐, 에러 메시지 출력이냐의 차이점이 있을뿐 둘다 출력을 위한 스트림입니다. 
출력 스트림은 어디서부터 어디를 연결한 스트림일까요? 
정답은 바로 프로세스로부터 출력 장치까지의 스트림입니다. 
출력 장치라고 함은 우리가 결과를 확인하는 모니터를 의미합니다. 
출력결과가 터미널에 찍히는 것을 모니터로 보는 것이죠. 


## 2. 파일 디스크립터(file descriptor)

파일은 읽거나 쓰기전에 반드시 열어야(open) 합니다. 
커널은 파일 테이블이라고 하는 테이블을 이용해 프로세스 별로 열린 파일 목록을 관리합니다. 
파일 테이블의 각 항목은 열린 파일에 대한 정보를 담고 있으며, 각종 메타데이터가 포함되어 있습니다. 
파일 테이블은 모든 열려진 파일을 커널에서 관리하기 위한 테이블 입니다. 

파일 디스크립터(fd)는 프로세스가 파일에 접근하기 위해 제공되는 고유 식별자 입니다. 
참고로 리눅스 시스템의 모든 것은 파일로 구성되어 있습니다. 
프로세스가 특정 파일에 접근하기 위해 해당 파일의 디스크립터를 이용하면 접근할 수 있게 됩니다다. 
예를 들어, 특정 파일에 접근하거나 새로운 파일을 만들면 커널에서 프로세스에게 파일 디스크립터를 사용하지않는 양수값을 fd값으로 할당합니다. 
fd값 후보의 범위는 0이상의 양수입니다. 
그리고 커널은 사용되고 있는 파일의 디스크립터를 테이블의 형태로 관리하는데 이것이 파일 테이블 입니다. 

<center><img src="/assets/images/os/redirection/01.jpg" width="800"></center>

다시 위 그림을 보겠습니다. stdin 옆에 숫자 0은 무엇을 의미하는 것일까요? 

종류 | 영문 | 파일 디스크립터
-----|-----|---------------
표준 입력 스트림 | stdin | 0
표준 출력 스트림 | stdout | 1
표준 오류 스트림 | stderr | 2

위와 같이 fd값으로 기본적으로 할당 받는 값들이 있기 때문에 
대부분의 파일 디스크립터들은 3번부터 차례대로 할당 됩니다. 

## 3. 리다이렉션(redirection)

리다이렉션을 이용하면 각 스트림의 방향을 지정할 수 있습니다. 

종류 | 기호 | 사용법 | 설명
-----|------|-------|------
표준 출력(덮어쓰기) | > | 명령어 > 파일 | 명령어의 표준 출력 스트림의 도착 지점을 파일로 설정(덮어쓰기)
표준 출력(추가) | >> | 명령어 >> 파일 | 명령어의 표준 출력 스트림의 도착지점 파일에 내용 추가
표준 입력 | < | 명령어 < 파일 | 파일로부터 입력 받음

### 3.1 표준 출력(덮어쓰기) 실습

ls 출력 결과 저장해 보겠습니다.
먼저 적당한 리렉토리를 만들고, 예제 텍스트 파일을 만듭시다. 
아무 말이나 입력한 01.txt, 02.txt 파일을 만들고 터미널에서 ls를 입력하면 다음과 같은 결과가 출력 됩니다. 

```bash
$ ls
01.txt 02.txt
```

지금은 ls의 출력 결과과 터미널 창에 표시됩니다. 
그럼 이번에는 ls의 출력 결과를 텍스트 파일로 저장합니다. 
방법은 위에서 설명한 것과 같이 표준 출력의 도착 지점을 파일로 설정하는 것입니다. 
저는 ls_list.txt라고 저장하겠습니다. 

```bash
$ ls > ls_list.txt
$ ls
01.txt 02.txt ls_list.txt
$ cat ls_list.txt
01.txt
02.txt
ls_list.txt
```

위와 같이 ls의 출력 결과가 ls_list.txt 파일에 저장된 것을 볼 수 있습니다. 

### 3.2 표준 출력(추가) 실습

이번에는 표준 출력 결과를 기존 파일에 추가하는 방법을 실습해 보겠습니다. 

```bash
$ ls >> ls_list.txt
$ ls
01.txt 02.txt ls_list.txt
$ cat ls_list.txt
01.txt
02.txt
ls_list.txt
01.txt
02.txt
ls_list.txt
```

앞서 이미 ls_list.txt에 내용이 존재했으므로 해당 파일에 다시 ls 출력결과를 추가하면 
위 결과와 같이 ls의 출력 결과가 ls_list.txt에 추가되는 것을 볼 수 있습니다. 

### 3.3 표준 입력 실습

이번에는 표준 입력 실습을 해보겠습니다. 
앞서 만든 ls_list.txt 파일의 마지막 부분 2개 행을 출력해보겠습니다. 

```bash
$ tail -n 2 < ls_list.txt
02.txt
ls_list.txt
```

tail 커맨드는 마지막 행을 출력하는 명령어입니다. 
그리고 -n 2 옵션은 마지막 2개 행을 출력하겠다는 뜻입니다. 
따라서 위 커맨드의 의미는 ls_list.txt 파일을 입력받아 마지막 2개 행을 출력하라는 의미입니다. 

## 4. 파이프(pipe)

앞서 배운 리다이렉션이 프로세스의 입력 또는 출력을 파일로 사용하는 것이라면 
이번에 배울 파이프(pipe)는 서로다른 프로세스간 작동하는 방식입니다. 
특수기호는 '|'을 사용합니다. 일반적으로 A|B 형태로 사용하는데, 
이말은 A 커맨드의 표준 출력을 B 커맨드의 표준 입력으로 사용한다는 의미입니다. 

```bash
$ ps -ef | grep gnome
(결과 생략)
```

위 커맨드는 ps -ef 명령어를 통해 나온 출력 결과중 
gnome이라는 문자를 포함하는 결과를 출력한다는 내용입니다. 
참고로 ps 명령어는 실행중인 프로세스 목록을 보는 명령어 이며, 
-e 옵션은 실행중인 모든 모르세스 정보 출력, 
-f 옵션은 프로세스에 대한 자세한 정보를 출력한다는 옵션입니다. 

## 5. 리다이렉션 + 파이프

마지막으로 리다이렉션과 파이프를 함께 사용해보겠습니다. 

```bash
$ ps -ef | grep gnome > ps_gnome.txt
$ cat ps_gnome.txt
```

위 코드는 ps -ef 커맨드의 출력 결과중 gnome이라는 문자를 포함하는 결과만 추출한 후, 해당 결과를 
ps_gnome.txt 라는 파일에 저장하라는 의미입니다. 

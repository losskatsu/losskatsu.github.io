---
title: "[Infra] 리버스 프록시(reverse proxy) 서버 개념" 
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

# 리버스 프록시(reverse proxy) 서버 개념

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

**참고 링크**

* [flask, nginx, uwsgi (1)개념](https://losskatsu.github.io/it-infra/flask-nginx-uwsgi-concept/)
* [flask, nginx, uwsgi (2)연동 실습](https://losskatsu.github.io/it-infra/flask-nginx-uwsgi/)  
* [AWS에 아파치 서버 설치하기](https://losskatsu.github.io/it-infra/aws-apache/)
* [아파치 서버 에러 로그 확인](https://losskatsu.github.io/it-infra/apache-error-log/)
* [커버로스 인증 개념](https://losskatsu.github.io/it-infra/kerberos/)
* [아파치, 톰캣, nginx 차이](https://losskatsu.github.io/it-infra/webserver/)
* [SSL, CRS 인증 관련 정리(대칭키, 공개키, 개인키)](https://losskatsu.github.io/it-infra/ssl-auth/)
* [프록시 서버, 리버스 프록시 서버 정리](https://losskatsu.github.io/it-infra/reverse-proxy/)  

## 1. 프록시(proxy) 서버란?

프록시 서버란 무엇일까요? 
프록시 서버를 구글에 검색하면 이런 뜻이 나옵니다. 

> 프록시 서버(proxy server)는 클라이언트가 자신을 통해서 다른 네트워크 서비스에 간접적으로 접속할 수 있게 해 주는 컴퓨터 시스템이나 응용 프로그램을 가리킨다. 서버와 클라이언트 사이에 중계기로서 대리로 통신을 수행하는 것을 가리켜 '프록시', 그 중계 기능을 하는 것을 프록시 서버라고 부른다. 

프록시 서버를 사용하면 보안성, 성능, 안정성을 향상 시킬 수 있습니다.

프록시 서버는 크게 포워드 프록시 서버(forward proxy server)와 리버스 프록시 서버(reverse proxy server)로 나눠집니다. 
그리고 리버스 프록시 서버를 설명하기 전에 포워드 프록시 서버에 대해 먼저 이해하면 리버스 프록시 서버를 이해하는데 도움이 됩니다.  

## 2. 포워드 프록시(forward) 서버란?

우리가 흔히 말하는 '프록시 서버'란 포워드 포록시 서버를 의미합니다. 
프록시 서버는 아래 그림처럼 클라이언트 앞에 놓여 있습니다.
다음 그림을 보면 클라이언트가 인터넷 웹서버에 요청을 보내면 중간에서 그 요청을 프록시 서버가 가로챕니다. 
그리고나서 프록시 서버는 해당 요청을 웹서버에게 다시 보내고 웹서버에게 받은 응답을 다시 클라이언트에게 전달합니다. 

<center><img src="/assets/images/infra/reverse_proxy/reverse_proxy01.PNG" width="800"></center>

그렇다면 포워드 프록시 서버는 왜 사용하는 것일까요?

우선 정부, 학교, 기업 등과 같은 기관은 해당 기관에 속한 사람들의 제한적인 인터넷 사용을 위해 방화벽을 사용합니다. 
포워드 프록시 서버는 이런 제한을 위해 사용합니다. 즉, 해당 기관에 속한 사람들이 그들이 방문하고자 하는 
웹사이트에 직접적으로(directly) 방문하는 것을 방지합니다. 

이 말은 곧 포워드 프록시 서버는 기관에 속한 유저가 특정 컨텐츠에 접근하는 것을 방지하는데 사용된다는 말과 동일합니다. 
예를 들어, 포워드 프록시 서버에 룰을 추가해서 특정 사이트에 접속하는 것을 막을 수 있습니다. 

마지막으로 포워드 프록시 서버를 사용하면 유저의 정체를 숨겨줍니다. 
인터넷을 사용하는 대부분 유저들은 익명성을 바라는데 프록시 서버를 사용하지 않으면 자신의 정체가 탄로 날 수 있습니다. 
하지만 만약 포워드 프록시 서버를 사용하면 IP 주소를 역추적해도 정체를 파악하기 어렵습니다. 
왜냐면 IP 추적해도 프록시 서버만 보이기 때문입니다. 


## 3. 리버스 프록시(reverse proxy) 서버란?

리버스 프록시 서버는 아래 그림 처럼 웹서버 앞에 놓여 있습니다. 
포워드 프록시 서버는 클라이언트 앞에 놓여져 있는 반면, 리버스 프록시 서버는 웹서버 앞에 놓여 있습니다. 

<center><img src="/assets/images/infra/reverse_proxy/reverse_proxy02.PNG" width="800"></center>

그렇다면 리버스 프록시 서버는 왜 사용하는 것일까요?  

우선 리버스 프록시 서버는 로드 밸런싱(load balancing)에 사용됩니다. 
유명한 웹 사이트는 하루에도 수백만명이 방문합니다. 
그리고 그러한 대량의 트래픽을 하나의 싱글 서버로 감당해 내기란 어렵습니다. 
하지만 리버스 프록시 서버를 여러개의 서버 앞에 두면 특정 서버가 과부화 되지 않게 로드밸런싱이 가능합니다.  

또한 리버스 프록시를 사용하면 보안에 좋습니다. 
리버스 프록시를 사용하면 본래 서버의 IP 주소를 노출시킬 필요가 없습니다. 
따라서 해커들의 DDoS 공격과 같은 공격을 막는데 유용합니다. 
대신 CDN과 같은 리버스 프록시 서버가 공격의 타겟이 될수는 있습니다.  

그리고 리버스 프록시 서버에는 성능 향상을 위해 캐시 데이터를 저장할 수 있습니다. 
만약 어떤 한국에 있는 유저가 미국에 웹서버를 두고 있는 사이트에 접속할때, 
리버스 프록시 서버가 한국에 있다고 해봅시다. 
그러면 한국에 있는 유저는 한국에 있는 리버스 프록시 서버와 통신합니다. 
따라서 리버스 프록시 서버에 캐싱되어 있는 데이터를 사용할 경우에는 더 빠른 성능을 보여줄수 있는 것입니다. 

마지막으로 SSL 암호화에 좋습니다. 
본래 서버가 클라이언트들과 통신을 할때 SSL(or TSL)로 암호화, 복호화를 할 경우 비용이 많이 듭니다. 
그러나 리버스 프록시를 사용하면 들어오는 요청을 모두 복호화하고 나가는 응답을 암호화해주므로 
클라이언트와 안전한 통신을 할수 있으며 본래 서버의 부담을 줄여줍니다.

## 4. 포워드 프록시 vs 리버스 프록시

위 그림만 봐서는 포워드 프록시 서버와 리버스 프록시 서버의 차이점이 거의 없는 것 같습니다. 
하지만 분명 차이가 있습니다. 
포워드 프록시 서버는 클라이언트 앞에 놓여져 있는 반면, 리버스 프록시 서버는 웹서버 앞에 놓여 있습니다. 

포워드 프록시 서버를 사용하면 클라이언트와 직접 통신하는 웹서버가 없다는 것을 알 수 있습니다. 
반면 리버스 프록시 서버를 사용하면 웹서버와 직접 통신하는 클라이언트가 없다는 것을 알 수 있습니다.


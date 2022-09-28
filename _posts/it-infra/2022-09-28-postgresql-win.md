---
title: "[PostgreSQL] 윈도우에 PostgreSQL 설치하기"
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

# [PostgreSQL] 윈도우에 PostgreSQL 설치하기

## 참고 링크  

### DB

* [MySQL 윈도우에 설치하기](https://losskatsu.github.io/it-infra/mysql-install-win/)
* [MySQL 간단 정리, 우분투, 맥에 설치 하기](https://losskatsu.github.io/it-infra/mysql-index/)
* [맥 OS에 MySQL 설치](https://losskatsu.github.io/it-infra/mysql-install-mac/)
* [파이썬, MySQL 연동](https://losskatsu.github.io/programming/py-db-conn/)
* [데이터베이스에서 널(null)과 공백의 차이](https://losskatsu.github.io/it-infra/db-null/)
* [우분투에 PostgreSQL 설치](https://losskatsu.github.io/it-infra/postgresql-ubuntu/)
* [윈도우에 PostgreSQL 설치](https://losskatsu.github.io/it-infra/postgresql-win/)


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

본 예제는 윈도우11 환경에서 실행했습니다.

먼저 다음 url에 접근합니다.

[https://www.postgresql.org/download/](https://www.postgresql.org/download/)  


<center><img src="/assets/images/infra/postgresql/psql01.png" width="800"></center>


위와 같은 화면에서 windows를 클릭합니다. 

<center><img src="/assets/images/infra/postgresql/psql02.png" width="800"></center>


그리고 위 화면에서 download the installer를 클릭합니다. 

<center><img src="/assets/images/infra/postgresql/psql03.png" width="800"></center>

그러면 위와 같은 다운로드 화면이 나타나는데 윈도우 쪽을 클릭해서 다운로드 해줍니다. 
다운로드 용량은 313MB 정도 되는데 네트워크 환경에 따라 시간이 걸릴 수 있습니다. 
다운로드를 완료하면 해당 파일을 실행해 줍니다. 

<center><img src="/assets/images/infra/postgresql/psql04.png" width="800"></center>

그러면 위와 같은 설치 마법사가 실행되는데 next를 눌러줍시다. 

<center><img src="/assets/images/infra/postgresql/psql05.png" width="800"></center>

위와 같은 설치 경로가 나타나면 건드리지 말고 next를 눌러줍시다.

<center><img src="/assets/images/infra/postgresql/psql06.png" width="800"></center>

그러면 postgreSQL 구성 요소 중 무엇을 설치할지 선택하라고 뜨는데, 여기서는 자신이 원하는 것을 선택합시다. 
저는 변경없이 모두 설치하겠습니다.

<center><img src="/assets/images/infra/postgresql/psql07.png" width="800"></center>

그리고 PostgreSQL의 데이터를 저장할 디렉토리를 선택하라고 뜨는데 건들지 말고 그냥 next 눌러줍시다. 

<center><img src="/assets/images/infra/postgresql/psql08.png" width="800"></center>

그러면 위와 같이 postgres 계정의 비밀번호를 설정하라고 뜨는데, 자신이 원하는 비밀번호를 입력합시다. 
저는 귀찮아서 그냥 1234라고 설정했습니다. 

<center><img src="/assets/images/infra/postgresql/psql09.png" width="800"></center>

다음은 포트 설정 화면입니다. PostgreSQL의 기본포트는 5432 포트입니다. 
가급적 변경하지 말고 next 눌러줍니다. 

<center><img src="/assets/images/infra/postgresql/psql10.png" width="800"></center>

다음은 locale을 설정하는 화면인데 저는 변경하지 않고 next를 눌러주겠습니다. 

<center><img src="/assets/images/infra/postgresql/psql11.png" width="800"></center>

설치 준비가 모두 끝났습니다. 설치해줍니다. 

<center><img src="/assets/images/infra/postgresql/psql12.png" width="800"></center>

next를 눌러줍니다. 

<center><img src="/assets/images/infra/postgresql/psql13.png" width="800"></center>

그러면 설치가 시작 됩니다. 


<center><img src="/assets/images/infra/postgresql/psql14.png" width="800"></center>

설치가 완료되면 위와 같은 화면이 뜹니다. 
Finish를 눌러 설치를 마치겠습니다. 

<center><img src="/assets/images/infra/postgresql/psql16.png" width="800"></center>

설치를 마쳤으면 시작을 누르고 sql shell(psql)을 실행하고 위와 같이 셋팅을 해줍니다. 
기본적으로 아무것도 입력하지 않고 엔터를 누르면 기본값이 설정되며, 마지막으로 비밀번호를 설정해줍니다.

<center><img src="/assets/images/infra/postgresql/psql15.png" width="800"></center>

그후 시작을 누르고 pgadmin4를 실행하면 위와 같이 비밀번호를 설정하라고 뜨는데, 
자신이 원하는 비밀번호를 입력합니다. 
저는 또 1234로 설정하겠습니다. 

<center><img src="/assets/images/infra/postgresql/psql17.png" width="800"></center>

그리고나서 위와 같이 데이터베이스를 연결해줍니다. 
Name은 자기가 원하는 이름으로 설정해줍니다.

<center><img src="/assets/images/infra/postgresql/psql18.png" width="800"></center>

그리고 나머지 정보들도 입력해줍니다.

<center><img src="/assets/images/infra/postgresql/psql19.png" width="800"></center>

그러면 위와 같이 연결되는 것을 알 수 있습니다. 

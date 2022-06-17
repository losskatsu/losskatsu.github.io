---
title: "[Django] 장고 inspectdb로 DB테이블을 models.py로 만들기"
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

# 장고 inspectdb로 DB테이블을 models.py로 만들기

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


## 1. DB 테이블 장고로 불러오기

본 예제는 맥OS 환경에서 실행했습니다.

장고의 models.py를 이용해 데이터베이스에 테이블을 생성할 수 있지만 
대부분으 경우 데이터베이스의 테이블이 사전에 존재하는 경우가 많습니다. 
따라서 이번 실습에서는 반대로 이미 존재하는 데이터베이스 테이블을 장고의 models.py로 만들어보겠습니다.

```bash
$ python manage.py inspectdb

# This is an auto-generated Django model module.
# You'll have to do the following manually to clean this up:
#   * Rearrange models' order
#   * Make sure each model has one field with primary_key=True
#   * Make sure each ForeignKey and OneToOneField has `on_delete` set to the desired behavior
#   * Remove `managed = False` lines if you wish to allow Django to create, modify, and delete the table
# Feel free to rename the models, but don't rename db_table values or field names.
from django.db import models


class AuthGroup(models.Model):
    name = models.CharField(unique=True, max_length=150)

    class Meta:
        managed = False
        db_table = 'auth_group'
(생략)
```

위와 같이 ```inpectdb``` 커맨드 이용하면 기존에 연동되어 있는 데이터베이스으 테이블을 파이썬 models.pyㄹ 만들어줍니다. 
우리느 위 결과를 출력만 하는것이 목적이 아니라 models.py로 저장하는 것이 목적이므로 다음과 같이 입력해줍니다. 


```bash
$ python manage.py inspectdb > models.py
```

위와 같은 커맨드를 입력하면 다음고 같이 models.py가 생성된 것을 알 수 있습니다. 

<center><img src="/assets/images/infra/django-inspectdb/inspectdb01.png" width="800"></center>


```bash
$  python manage.py migrate

Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  No migrations to apply.
```

그리고 디비를 한번씨 건드릴때마다 위 코드와 같이 ```migrate```명령어를 입력해줍니다. 

```bash
$ python manage.py runserver

Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
June 02, 2022 - 04:30:59
Django version 4.0.2, using settings 'dbcontest.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

그리고 최종적을 서버가 잘 올라가는지 확인해줍니다. 




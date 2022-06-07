---
title: "[Infra] MsSQL과 장고(django) 연결하기"
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

# MsSQL과 장고(django) 연결하기

### 참고 링크  

* [MySQL 윈도우에 설치하기](https://losskatsu.github.io/it-infra/mysql-install-win/)
* [MySQL 간단 정리, 우분투, 맥에 설치 하기](https://losskatsu.github.io/it-infra/mysql-index/)
* [맥 OS에 MySQL 설치](https://losskatsu.github.io/it-infra/mysql-install-mac/)

* [파이썬, MySQL 연동](https://losskatsu.github.io/programming/py-db-conn/)
* [데이터베이스에서 널(null)과 공백의 차이](https://losskatsu.github.io/it-infra/db-null/)

* [(1)MySQL에 데이터베이스, 테이블 생성하기](https://losskatsu.github.io/it-infra/mysql-create-db/)
* [(2)장고, MsSQL 연결하기](https://losskatsu.github.io/it-infra/mssql-django-conn/)
* [(2)장고, MySQL 연결하기](https://losskatsu.github.io/it-infra/mysql-django-conn/)
* [(3)장고 inpectdb로 DB 데이터 model.py로 만들기](https://losskatsu.github.io/it-infra/django-inspectdb/)
* [(4)장고로 MySQL에 있는 데이터 웹상에서 보여주기](https://losskatsu.github.io/it-infra/django-read-data/)
* [(5)장고로 MySQL에 데이터 insert 하기](https://losskatsu.github.io/it-infra/django-post-data/)
* [(6)장고로 MySQL에 데이터 수정(put) 하기](https://losskatsu.github.io/it-infra/django-put-data/)
* [(7)장고로 MySQL에 데이터 삭제(delete) 하기](https://losskatsu.github.io/it-infra/django-del-data/)


## 1. 장고 프로젝트 생성하기

본 예제는 윈도우 11 환경에서 실행했습니다. 

먼저 테스트에 사용할 장고 프로젝트를 생성하겠습니다. 
아나콘다 프롬프트를 열고 자신의 가상환경을 실행하고 
자신이 프로젝트를 생성하고 싶은 폴더로 이동해 프로젝트를 생성해줍니다. 

```bash
(py3_9_7)$ django-admin startproject dbcontest
```

프로젝트를 생성했으면 mssql과 장고를 연동하기 위해 필요한 라이브러리인 ```mssql-django```를 다음과 같이 설치해줍니다.

```bash
(py3_9_7)$ pip install mssql-django
```

## 2. setting.py 수정

저는 IDE로 인텔리제이를 사용하므로 
인텔리제이를 실행해서 해당 장고 프로젝트를 열어줍니다. 
이때 터미널은 기본 cmd로 설정해도 ```conda``` 명령어가 먹히므로 ```conda activate py3_9_7```커맨드를 사용하면 
가상환경을 활성화 할 수 있습니다. 

본격적으로 mssql과 장고를 연동하기 위해 ```setting.py```를 다음과 같은 코드로 수정합니다. 

```python
DATABASES = {
    'default': {
        'ENGINE': 'mssql',
        'NAME': 'LIVING_PARADISE',
        'USER': 'erp_test',
        'PASSWORD': '1234',
        'HOST': '10.1.55.202',
        'PORT': '1433',
    }
}
```

참고로 위 코드에서 Mssql의 기본 포트는 1433 입니다. 

## 3. 연동 확인

MsSQL과 장고가 연동되었는지 확인해보기 위해 다음과 같이 migrate를 해봅니다.

```bash
(py3_9_7)$ python manage.py migrate

Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  ...(중략)
```

그리고 장고가 잘 실행되는지 봅시다. 

```bash
(py3_9_7)$ python manage.py runserver

Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
May 31, 2022 - 09:25:46
Django version 4.0.4, using settings 'dbcontest.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
```

<center><img src="/assets/images/infra/mssql-django/django-mssql01.png " width="800"></center>

그리고 실제로 MsSQL 테이블이 생성되었는지 MsSQL을 실행해 확인해봅니다.

<center><img src="/assets/images/infra/mssql-django/django-mssql02.png " width="800"></center>

위 그림과 같이 잘 연동된 것을 볼 수 있습니다.

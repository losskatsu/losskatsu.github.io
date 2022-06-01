---
title: "[Infra] MySQL과 장고(django) 연결하기"
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

# MySQL과 장고(django) 연결하기

### 참고 링크  

* [MySQL 윈도우에 설치하기](https://losskatsu.github.io/it-infra/mysql-install-win/)
* [MySQL 간단 정리, 우분투, 맥에 설치 하기](https://losskatsu.github.io/it-infra/mysql-index/)
* [파이썬, MySQL 연동](https://losskatsu.github.io/programming/py-db-conn/)
* [데이터베이스에서 널(null)과 공백의 차이](https://losskatsu.github.io/it-infra/db-null/)

## 1. 장고 프로젝트 생성하기

본 예제는 맥OS 환경에서 실행했습니다. 

먼저 테스트를 진행할 장고 프로젝트르 생성하겠습니다.

터미널을 열고 파이썬 가상환경을 실행한 후 다음과 같이 장고 프로젝트를 생성합니다. 

```bash
$ django-admin startproject dbcontest
```

장고와 mysql 데이터베이스르 연결하려면 ```mysqlclient```이 필요합니다. 
다음과 같이 ```mysqlclient```를 설치해줍니다. 

```bash
$ django-admin startproject dbcontest
```

프로젝트르 생성했으면 인텔리제이를 실행하고 다음과 같이 setting.py를 수정해줍니다. 

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'MYTEST',
        'USER': 'root',
        'PASSWORD': '1234',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```

위 코드에서 NAME: MYTEST는 데이터베이스 이름을 의미합니다. 
MySQL의 기본 포트는 3306입니다. 

그리고나서 연결이 되는지 다음과 같이 장고 서버를 실행해봅니다.

```bash
$ python manage.py runserver
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).

You have 18 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python manage.py migrate' to apply them.
June 01, 2022 - 04:06:21
Django version 4.0.2, using settings 'dbcontest.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```


<center><img src="/assets/images/infra/mysql-django-conn/mysql-django-con01.png" width="800"></center>

위 코드를 실행하면 장고 서버 실행이 제대로 되는 것을 알 수 있습니다. 
만약 DB연결이 제대로 되지 않으면 ```runserver``` 명령어가 먹히지 않습니다. 
컨트롤 C를 눌러 일다 서버를 내리고 migrate 시켜줍시다. 

장고 서버가 잘 실행되었으므로 migrate 시켜주겠습니다. 
다음 커맨드를 입력합니다.

```bash
$ python manage.py migrate 

Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
...(생략)
```

그리고 나서 서버가 잘 실행 되는지 봅니다. 

```bash
$ python manage.py runserver 

Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
June 01, 2022 - 04:07:14
Django version 4.0.2, using settings 'dbcontest.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```


<center><img src="/assets/images/infra/mysql-django-conn/mysql-django-con01.png" width="800"></center>


장고가 이렇게 실행이 잘되는 것을 볼 수 있는데, 
MySQL 워크벤치를 실행해 디비가 연결되었는지 확인해보겠습니다. 

<center><img src="/assets/images/infra/mysql-django-conn/mysql-django-con02.png" width="800"></center>

위 스크린샷은 장고와 연결하기 전인 기존 MySQL 입니다. 우클릭을 해서 refresh all을 클릭하면 다음 스크린샷과 같이 장고와 관련된 디비가 추가 됩니다.

<center><img src="/assets/images/infra/mysql-django-conn/mysql-django-con03.png" width="800"></center>

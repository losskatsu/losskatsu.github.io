---
title: "[Infra] MySQL 맥 OS에 설치하기" 
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

# MySQL 맥 OS에 설치하기

### 참고 링크  

* [MySQL 윈도우에 설치하기](https://losskatsu.github.io/it-infra/mysql-install-win/)
* [MySQL 간단 정리, 우분투, 맥에 설치 하기](https://losskatsu.github.io/it-infra/mysql-index/)
* [파이썬, MySQL 연동](https://losskatsu.github.io/programming/py-db-conn/)
* [데이터베이스에서 널(null)과 공백의 차이](https://losskatsu.github.io/it-infra/db-null/)

## 1. MySQL 다운로드 받기

터미널을 실행시킨 다음 커맨드르 입력합니다.

```bash
$ brew install mysql

Running `brew update --preinstall`...
==> Auto-updated Homebrew!
Updated 1 tap (homebrew/core).
==> New Formulae
...(중략)
We've installed your MySQL database without a root password. To secure it run:
    mysql_secure_installation

MySQL is configured to only allow connections from localhost by default

To connect run:
    mysql -uroot

To restart mysql after an upgrade:
  brew services restart mysql
Or, if you don't want/need a background service you can just run:
  /usr/local/opt/mysql/bin/mysqld_safe --datadir=/usr/local/var/mysql
```

설치르 했으면 버전을 확인합니다.

```bash
$ mysql -V
mysql  Ver 8.0.29 for macos12.2 on x86_64 (Homebrew)
```

MySQL을 실행해보겠습니다.

```bash
$ % mysql.server start
Starting MySQL
.. SUCCESS!
```

위 처럼 SUCCESS가 뜨면 잘 실행이 된 것입니다. 

## 2. 설정하기

설치를 마쳤으면 설정을해보겠습니다

```bash
$ mysql_secure_installation

Securing the MySQL server deployment.

Connecting to MySQL using a blank password.

VALIDATE PASSWORD COMPONENT can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD component?

Press y|Y for Yes, any other key for No: N
```

위 
## 2. 설정하기ㅊㅓ럼 
## 2. 설정하기


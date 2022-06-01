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

그리고 다음과 같이 ```mysqlclient```를 설치해줍니다. 

```bash
$ django-admin startproject dbcontest
```


프로젝트르 생성했으면 인텔리제이를 실행하고 다음과 같

<center><img src="/assets/images/infra/mysql-jango-conn/mysql-django-con01.png" width="800"></center>

<center><img src="/assets/images/infra/mysql-jango-conn/mysql-django-con02.png" width="800"></center>

<center><img src="/assets/images/infra/mysql-jango-conn/mysql-django-con03.png" width="800"></center>

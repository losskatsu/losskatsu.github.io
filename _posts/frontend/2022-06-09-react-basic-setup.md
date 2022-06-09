---
title: "[리액트react] 장고(Django)연동을 위한 기본 리액트 프로젝트 생성" 
categories:
  - frontend
tags:
  - frontend
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---


# 리액트(react) 장고(Django)연동을 위한 기본 리액트 프로젝트 생성


### 참고 링크  

* [MySQL 윈도우에 설치하기](https://losskatsu.github.io/it-infra/mysql-install-win/)
* [MySQL 간단 정리, 우분투, 맥에 설치 하기](https://losskatsu.github.io/it-infra/mysql-index/)
* [맥 OS에 MySQL 설치](https://losskatsu.github.io/it-infra/mysql-install-mac/)

* [파이썬, MySQL 연동](https://losskatsu.github.io/programming/py-db-conn/)
* [데이터베이스에서 널(null)과 공백의 차이](https://losskatsu.github.io/it-infra/db-null/)

* 백엔드
* [(1-1)MySQL에 데이터베이스, 테이블 생성하기](https://losskatsu.github.io/it-infra/mysql-create-db/)
* [(1-2)장고, MsSQL 연결하기](https://losskatsu.github.io/it-infra/mssql-django-conn/)
* [(1-2)장고, MySQL 연결하기](https://losskatsu.github.io/it-infra/mysql-django-conn/)
* [(1-3)장고 inpectdb로 DB 데이터 model.py로 만들기](https://losskatsu.github.io/it-infra/django-inspectdb/)
* [(1-4)장고로 MySQL에 있는 데이터 웹상에서 보여주기](https://losskatsu.github.io/it-infra/django-read-data/)
* [(1-5)장고로 MySQL에 데이터 insert 하기](https://losskatsu.github.io/it-infra/django-post-data/)
* [(1-6)장고로 MySQL에 데이터 수정(put) 하기](https://losskatsu.github.io/it-infra/django-put-data/)

* 프론트엔드
* [(2-1)기본 리액트 프로젝트 생성](https://losskatsu.github.io/frontend/react-basic-setup/)

## 1. 사전 준비 사항

지금부터 만들 앱은 파이썬 장고(django)에 연동할 프론트를 리액트로 만드는 실습입니다.

먼저 프로젝트를 생성하겠습니다. 프로젝트 이름은 ```myapp01```로 하고 리액트 프로젝트를 다음과 같이 생성합니다. 

```bash
$ npm create react-app myapp01

Creating a new React app in /Users/cheolwon/Documents/test/nodejs/myapp01.

Installing packages. This might take a couple of minutes.
Installing react, react-dom, and react-scripts with cra-template...
...(중략)...
We suggest that you begin by typing:

  cd myapp01
  npm start

Happy hacking!
npm notice 
npm notice New minor version of npm available! 8.6.0 -> 8.12.1
npm notice Changelog: https://github.com/npm/cli/releases/tag/v8.12.1
npm notice Run npm install -g npm@8.12.1 to update!
npm notice 
```

프로젝트를 생성했으면 라우터 기능을 사용하기 위해 
프로젝트 디렉토리 내로 이동해 ```react-router-dom```을 설치해줍니다.

```bash
$ cd myapp01
$ npm add react-router-dom

added 3 packages, and audited 1423 packages in 3s

190 packages are looking for funding
  run `npm fund` for details

6 high severity vulnerabilities

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.
```

설치를 마쳤으면 인텔리제이를 이용해 프로젝트 디렉터리를 오픈합니다. 

## 2. 

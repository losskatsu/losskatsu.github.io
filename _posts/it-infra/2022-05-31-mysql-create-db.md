---
title: "[Infra] MySQL 데이터베이스, 테이블 생성하기"
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

# MySQL 데이터베이스, 테이블 생성하기

### 참고 링크  

* [MySQL 윈도우에 설치하기](https://losskatsu.github.io/it-infra/mysql-install-win/)
* [MySQL 간단 정리, 우분투, 맥에 설치 하기](https://losskatsu.github.io/it-infra/mysql-index/)
* [파이썬, MySQL 연동](https://losskatsu.github.io/programming/py-db-conn/)
* [데이터베이스에서 널(null)과 공백의 차이](https://losskatsu.github.io/it-infra/db-null/)

## 1. 데이터베이스 생성하기

테이블을 만들기 전에 먼저 데이터베이스를 생성해보겠습니다. 
다음과 같은 커맨드로 ```MYTEST```라는 데이터베이스를 생성해보겠습니다.  

```bash
CREATE DATABASE MYTEST;
```

<center><img src="/assets/images/infra/mysql-mac/mysql_mac06.png" width="800"></center>


## 2. 테이블 생성하기 

다음으로 다음과 같이 ```test01```이라는 테이블을 생성해보겠습니다. 

```bash
CREATE TABLE MYTEST.test01(
    id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP, 
    updated_at TIMESTAMP NULL DEFAULT NULL ON UPDATE CURRENT_TIMESTAMP, 
    PRIMARY KEY (id), 
    UNIQUE KEY email (email)
);
```

<center><img src="/assets/images/infra/mysql-mac/mysql_mac07.png" width="800"></center>

위와 같이 만들어진 테이블을 조회해보면 다음과 같이 아무 데이터도 없는 것을 확인할 수 있습니다. 

<center><img src="/assets/images/infra/mysql-mac/mysql_mac08.png" width="800"></center>

## 3. 데이터를 테이블에 insert하기 

다음으로 앞서 만든 test01 테이블에 데이터를 추가해보겠습니다. 
다음과 같이 INSERT INTO를 이용해 데이터를 삽입합니다. 

```bash
INSERT INTO MYTEST.test01(name, email) 
VALUES('Cheolwon', 'abcd@email.com');
```

<center><img src="/assets/images/infra/mysql-mac/mysql_mac09.png" width="800"></center>

위 코드에서 두개의 필드값만 입력하는 이유는 나머지 컬럼은 모두 자동으로 채워지기 때문입니다. 

<center><img src="/assets/images/infra/mysql-mac/mysql_mac10.png" width="800"></center>

테이블을 확인해보면 데이터가 잘 추가된 것을 볼 수 있습니다. 

```bash
INSERT INTO MYTEST.test01(name, email) 
VALUES('Soomin', 'efgh@email.com');
```

데이터를 하나 더 넣어보겠습니다. 

<center><img src="/assets/images/infra/mysql-mac/mysql_mac11.png" width="800"></center>

<center><img src="/assets/images/infra/mysql-mac/mysql_mac12.png" width="800"></center>

데이터가 잘 추가된 것을 볼 수 있습니다. 

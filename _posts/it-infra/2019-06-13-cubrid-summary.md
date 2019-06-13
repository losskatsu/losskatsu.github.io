---
title: "[Infra] 큐브리드(cubrid) 요약 " 
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

# 큐브리드(cubrid) 요약

## JDBC 드라이버

CUBRID JDBC 드라이버(cubrid_jdbc.jar)를 사용하면 Java로 작성된 응용 프로그램에서 CUBRID 데이터베이스에 접속할 수 있다. 
CUBRID JDBC 드라이버는 <CUBRID 설치 디렉터리> /jdbc 디렉터리에 위치한다. 

-------------------------------------------------------------

## JDBC 연결설정

```bash
jdbc:cubrid:<host>:<port>:<db-name>:[user-id]:[password]:[?<property> [& <property>] ... ]
```

* host: CUBRID 브로커가 동작하고 있는 서버 IP주소 또는 호스트 이름
* port: CUBRID 브로커의 포트 번호(기본값: 33000)
* db-name: 접속할 데이터베이스 이름 
* user_id: 데이터베이스에 접속할 사용자 ID
* passwordP: 데이터베이스에 접속할 사용자 암호
* <property>
  
    * altHosts: HA환경에서 장애 시 fail-over할 하나 이상의 standby 브로커의 호스트IP와 접속 포트
  
    * rcTime: 첫 번째로 접속했던 브로커에 장애가 발생한 이후 altHosts 에 명시한 브로커로 접속한다(failover). 이후, rcTime만큼 시간이 경과할 때마다 원래의 브로커에 재접속 시도(기본값 600초)
  
    * connectTimeout: 데이터베이스 접속에 대한 타임아웃 시간을 초 단위로 설정한다. 기본값은 30초. 이 값이 0인 경우 무한대기.
  
    * queryTimeout: 질의 수행에 대한 타임아웃 시간을 초 단위로 설정한다(기본값: 0, 무제한). 최대값은 2,000,000이다.
  
    * charSet: 접속하고자 하는 DB의 문자셋(charSet).

-------------------------------------------------------------

## Cubrid 구조

Cubrid는 JDBC 드라이버 - 브로커 - 데이터베이스 서버의 3계층(3-tier)구조를 사용한다. 

-------------------------------------------------------------

## High Availability  

High Availity(HA)란, 하드웨어, 스포트웨어, 네트워크 등 장애가 발생해도 지속적인 서비스를 제공하는 기능이다. 
이 기능은 하루 24시간 1년 내내 서비스를 제공해야 하는 네트워킹 컴퓨팅 부분에서 필수적인 요소이다. 
HA 시스템은 두 대 이상의 서버 시스템으로 구성하여 시스템 구성 요소 중의 한 요소에 장애가 발생해 서비스를 중단 없이 제공할 수 있다.

-------------------------------------------------------------

## 다중화 

CUBRID의 HA 기능은 shared-nothing 구조이다.

* Shared Disk: 하나의 스토리지를 공유하며 대개는 전용 스토리지 기기 이용.
* Shared Nothing: 스토리지 간 통신을 통해 데이터 정합성 확보. 데이터송신측을 master, 데이터수신측을 slave라고 함. 

-------------------------------------------------------------

## 브로커 모드 

* RW: Read Write
* RO: Read Only
* SO: Slave Only
* PHRO: Preferred Host Read Only
  
  

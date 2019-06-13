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
  

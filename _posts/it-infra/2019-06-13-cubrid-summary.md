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
  * rcTime: 첫 번째로 접속했던 브로커에 장애가 발생한 이후 altHosts 에 명시한 브로커로 접속한다(failover). 이후, rcTime만큼 시간이 경과할 때마다 원래의 브로커에 재접속 시도(기본값 600초)
  * connectTimeout: 데이터베이스 접속에 대한 타임아웃 시간을 초 단위로 설정한다. 기본값은 30초. 이 값이 0인 경우 무한대기.
  * queryTimeout: 질의 수행에 대한 타임아웃 시간을 초 단위로 설정한다(기본값: 0, 무제한). 최대값은 2,000,000이다.
  * charSet: 접속하고자 하는 DB의 문자셋(charSet).
  * zeroDateTimeBehavior: JDBC에서는 java.sql.Date 형 객체에 날짜와 시간 값이 모두 0인 값을 허용하지 않으므로 이 값을 출력해야 할 때 어떻게 처리할 것인지를 정하는 속성. 기본 동작은 exception 이다. 
  * logFile: 디버깅용 로그 파일 이름(기본값: cubrid_jdbc.log).
  * logOnException: 디버깅용 예외 처리 로깅 여부(기본값: false)
  * logSlowQueries: 디버깅용 슬로우 쿼리 로깅 여부(기본값: false)
  * useLazyConnection: 이 값이 true이면 사용자의 연결 요청 시 브로커 연결 없이 성공을 반환(기본값: false)하고, prepare나 execute 등의 함수를 호출할 때 브로커에 연결한다. 이 값을 true로 설정하면 많은 응용 클라이언트가 동시에 재시작되면서 연결 풀(connection pool)을 생성할 때 접속이 지연되거나 실패하는 현상을 피할 수 있다.

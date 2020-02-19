---
title: "[Infra] 아파치 서버 에러 로그 확인 " 
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

# 아파치 서버(Apache Server) 에러 로그(Error log) 확인

### 참고링크
* [아파치, 톰캣, 엔진엑스 차이](https://losskatsu.github.io/it-infra/webserver/)
* [아파치 서버 에러 로그 확인](https://losskatsu.github.io/it-infra/apache-error-log/)
* [SSL, CRS 인증 관련 정리](https://losskatsu.github.io/it-infra/ssl-auth/)



디폴트 에러 로그 경로
<br />

RHEL/REDhat/CentOS/Fedora : /var/log/httpd/error_log

Debian/Ubuntu : /var/log/apache2/error.log

FreeBSD : /var/log/httpd-error.log
<br />

만약 설정을 바꿨다면 httpd.conf 파일 참조. 
httpd.conf위치는 후보는 아래와 같다.

```bash
$ grep ErrorLog /usr/local/etc/apache22/httpd.conf
$ grep ErrorLog /etc/apache2/apache2.conf
$ grep ErrorLog /etc/httpd/conf/httpd.conf
```

만약 장고(Django)를 사용한다면 Django 디폴트 로그 설정은 파일로 기록되지 않는다. 
장고에서 에러 관련 작업은 settings.py 파일에서 작업함. 

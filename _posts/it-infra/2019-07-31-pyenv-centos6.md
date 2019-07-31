---
title: "[Infra] 예전 운영체제(CentOS 6)에 파이썬 가상환경 설치하기 " 
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

# CentOS 6에 파이썬 가상환경 설치하기 

Centos 6.7에서 파이썬 3 버전을 사용해야 할 일이 생겼다. 
그래서 나는 예전에 기록해 두었던 곳을 참조했다. 

링크: [pyenv를 통한 파이썬(python) 가상환경 구축](https://losskatsu.github.io/programming/pyenv/)

위 링크에 따라 가장 첫 줄부터 실행하게 되었는데, 
(참고로 centos에서는 apt 명령어가 아니고 yum을 써야한다)
이게 왠일, 아래와 같은 에러가 나면서 curl 명령어가 먹히지 않았다. 

```bash
$ curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash

curl: (35) SSL connect error
```

찾아보니까 운영체제 버전이 낮거나, curl 버전이 낮으면 위와 같은 에러가 나타날수 있다고 한다. 
Centos 6.7이 예전버전인건 확실하니까(현재는 Centos 7.x),
curl 버전을 확인해 보았다. 

```bash
$ curl --version

curl 7.19.7 (x86_64-redhat-linux-gnu) libcurl/7.19.7 NSS/3.27.1 zlib/1.2.3 libidn/1.18 libssh2/1.4.2
Protocols: tftp ftp telnet dict ldap ldaps http file https ftps scp sftp
Features: GSS-Negotiate IDN IPv6 Largefile NTLM SSL libz
```

curl도 7.19.7 버전이므로 예전 버전이다. curl 최신 버전은 아래 링크에서 확인 가능하다.

링크: [http://curl.haxx.se/download](http://curl.haxx.se/download)

curl을 최신버전으로 업데이트 해봤지만 소용없었다. 

내 목적은 pyenv 설치인데, curl 을 사용할수 없으므로 다른 방법을 사용해야했다. 

---
title: "[Infra] 예전 운영체제(CentOS 6)에 파이썬 가상환경(pyenv) 설치하기 " 
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

# CentOS 6에 파이썬 가상환경(pyenv) 설치하기 

Centos 6.7에서 파이썬 3 버전을 사용해야 할 일이 생겼다. (참고로 Centos는 페도라(Fedora) 계열)
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

## git clone 을 이용해 pyenv 설치

```bash
$ git clone https://github.com/pyenv/pyenv.git ~/.pyenv

$ echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
$ echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
$ echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bashrc
```
위 코드에서 운영체제에 따라 ~/.bashrc가 될수도 있고, ~/.bash_profile 이 될 수도 있으니, 확인 후 실행하시길. 

링크: [https://github.com/pyenv/pyenv.git](https://github.com/pyenv/pyenv.git)

다행히 pyenv 설치를 완료했습니다. 여기까지 삽질하는데만 1시간은 더걸린거 같네요. 
pyenv를 입력했을 때 아래와 같이 출력되면 설치 성공입니다.

```bash
$ pyenv

pyenv 1.2.9
Usage: pyenv <command> [<args>]

Some useful pyenv commands are:
   commands    List all available pyenv commands
   local       Set or show the local application-specific Python version
   global      Set or show the global Python version
   shell       Set or show the shell-specific Python version
   install     Install a Python version using python-build
   uninstall   Uninstall a specific Python version
   rehash      Rehash pyenv shims (run this after installing executables)
   version     Show the current Python version and its origin
   versions    List all Python versions available to pyenv
   which       Display the full path to an executable
   whence      List all Python versions that contain the given executable

```

## python3 설치 전 사전 프로그램 설치

자신의 운영체제에 따라 사전에 설치해야할 프로그램이 다릅니다. 
사전 프로그램을 설치하지 않을 시 파이썬3가 설치되지 않을 수 있으니 아래 링크를 꼭 확인해 주세요

링크: [운영체제별 파이썬3 사전설치 프로그램](https://github.com/pyenv/pyenv/wiki/Common-build-problems)

제가 사용하는 서버 운영체제는 Centos 6.7이므로 아래와 같이 입력합니다.

```bash
$ sudo yum install zlib-devel bzip2 bzip2-devel readline-devel sqlite sqlite-devel openssl-devel xz xz-devel libffi-devel findutils
```

## python3 설치

pyenv를 이용해 설치할수 있는 파이썬 버전을 확인해봅시다.

```bash
$ pyenv install --list
```

저는 출력목록에서 가장 최신 버전인 3.7.4를 설치하려 했거든요. 하지만 설치되지 않았습니다. 
왜냐면 RHEL 6계열에서는 파이썬 3.7이 설치되지 않는다는 것...
아래 링크 중간쯤 보시면 아래와 같은 메시지가 있습니다.

> Note: Python 3.7.0 will not compile on RHEL6 because it requires OpenSSL 1.0.2 or 1.1 and RHEL6 provides 1.0.1e

링크: [파이썬7이 설치 안되는 이유](https://github.com/pyenv/pyenv/wiki/Common-build-problems)

어쩔수없이 저는 아쉬움을 뒤로하고 3.6.5를 설치했습니다.

```bash
$ pyenv install 3.6.5
```

다행히 설치를 성공했습니다. 아래 코드를 사용하면 
pyenv에 설치된 파이썬 목록을 볼 수 있습니다.

```bash
$ pyenv versions

* system
3.6.5
```

## 가상환경 실행, 해제, 삭제






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


## 삽질의 시작, curl이 안먹힘

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

2019년 7월 31일 기준으로 7.65.3이 최신이므로 해당 버전을 설치했다. 

```bash
$ wget http://curl.haxx.se/download/curl-7.65.3.tar.gz
$ tar xvfz curl-7.65.3.tar.gz
$ cd cur-7.65.3
$ ./configure
$ make
$ make install
```

하지만, curl을 최신버전으로 업데이트 해봤지만 소용없었다. 

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
저는 출력목록에서 가장 최신 버전인 3.7.4를 설치하려 했습니다.

```bash
$ pyenv install 3.7.4

ERROR: The Python ssl extension was not compiled. Missing the OpenSSL lib?
```

하지만 위와 같이 설치되지 않았습니다. 
아직 curl의 악몽이 끝나지 않은 것인가라고 생각하며 이리저리 삽질끝에 아래 링크를 발견하게 됬습니다.

링크: [pyenv ssl error](https://github.com/pyenv/pyenv/wiki/Common-build-problems)

위 링크에는 설치실패 메시지 별로 대응 방안이 써있는데요, 페이지 하단 쯤에 있는
ERROR: The Python ssl extension was not compiled. Missing the OpenSSL lib?
을 참고해 아래와 같은 명영어를 입력했습니다.

```bash
$ CFLAGS=-I/usr/include/openssl LDFLAGS=-L/usr/lib64 pyenv install -v 3.7.4

ERROR ~~bla bla ~~~~
```
하지만 그래도 설치되지 않았습니다..........
이번에도 삽질끝에 답을 찾았는데요. 
답은 바로 RHEL 6계열에서는 파이썬 3.7이 설치되지 않는다는 것이었습니다. 
아래 링크 중간쯤 보시면 아래와 같은 메시지가 있습니다.

링크: [파이썬7이 설치 안되는 이유](https://github.com/pyenv/pyenv/wiki/Common-build-problems)

> Note: Python 3.7.0 will not compile on RHEL6 because it requires OpenSSL 1.0.2 or 1.1 and RHEL6 provides 1.0.1e

어쩔수없이 저는 아쉬움을 뒤로하고 3.6.5를 설치했습니다.

```bash
$ CFLAGS=-I/usr/include/openssl LDFLAGS=-L/usr/lib64 pyenv install -v 3.6.5
```

다행히 설치를 성공했습니다. 아래 코드를 사용하면 
pyenv에 설치된 파이썬 목록을 볼 수 있습니다.

```bash
$ pyenv versions

* system
3.6.5
```

## 파이썬 가상환경 생성

파이썬 3.6.5버전을 설치했으므로 py3_6_5라는 이름의 가상환경을 만들겠습니다. 
예전에는 잘 됬는데 이번엔 아래와 같은 에러가 뜨네요.

```bash
$ pyenv virtualenv 3.6.5 py3_6_5

-bash: virtualenv: command not found
```

virtualenv 커맨드를 찾을 수가 없다라...제 느낌에는 설치가 되지 않은 것 같았습니다.
그래서 삽질끝에 virtualenv를 설치할수 있는 방법을 찾았습니다. 아래와 같은 명령어를 입력합시다.

```bash
git clone https://github.com/pyenv/pyenv-virtualenv.git ~/.pyenv/plugins/pyenv-virtualenv
```
위 명령어를 실행하기 전에 ~/.pyenv/plugins 폴더에 가봤는데요.
pyenv-vituralenv라는 폴더가 없더라구요. 그래서 설치해야겠다는 생각이 들었습니다. 


## 가상환경 실행, 해제, 삭제

가상환경 사용하기(접속하기)

```bash
$ pyenv activate py3_6_5
```

가상환경 해제하기 (빠져나오기)
```bash
$ source deactivate
```

가상환경이나 파이썬 삭제하기
```bash
$ pyenv uninstall py3_6_5
$ pyenv uninstall 3.6.5
```

## 가상환경 실행 후 라이브러리 설치하기


현재 설치된 라이브러리 리스트

```bash
$ pyenv activate py3_6_5
(py3_6_5)$ pip list
```


numpy를 설치해봅시다.

```bash
$ pyenv activate py3_6_5
(py3_6_5)$ pip install numpy
```

pandas 설치
```bash
(py3_6_5)$ pip install pandas
```

matplotlib 설치
```bash
(py3_6_5)$ pip install matplotlib
```

이렇게 약 2시간의 삽질끝에 환경을 구축했습니다..ㅠ

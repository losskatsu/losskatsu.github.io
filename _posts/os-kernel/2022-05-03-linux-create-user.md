---
title: "[리눅스] 유저 생성하기" 
categories:
  - os-kernel
tags:
  - os
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 리눅스 - 유저 생성하기


**참고링크**

* [프로세스란?](https://losskatsu.github.io/os-kernel/os-process/)
* [리다이렉션, 파이프 개념](https://losskatsu.github.io/os-kernel/linux-redirection/)
* [네임스페이스 개념](https://losskatsu.github.io/os-kernel/linux-namespace/)
* [분산시스템 개념(1)](https://losskatsu.github.io/os-kernel/dist-sys-concept01/)
* [분산시스템 개념(2)](https://losskatsu.github.io/os-kernel/dist-sys-concept02/)
* [프로그램, 바이너리, 프로세스, 스레드의 개념](https://losskatsu.github.io/os-kernel/process-thread/)



## 1. 유저 생성 및 홈 디렉토리 생성

루트로 로그인해서 다음과 같이 입력합니다.

```bash
# useradd -m -s /bin/bash 계정명
```
위 명령어에서 m은 홈 디렉토리를 생성하는 옵션이고, 
s /bin/bash은 쉘 환경을 설정해주는 옵션입니다.


그리고나서 만든 계정명(예를 들어 dlit)을 sudo 그룹에 넣으려면 /etc/sudoers 파일을 수정해야하는데,
이 파일은 read only 파일이므로 다음과 같이 수정해 줍니다.

```bash
$ sudo bash
$ chattr -i /etc/sudoers
$ chmod u+w /etc/sudoers
```

그리고나서 파일을 vim으로 열어줍니다.

```bash
$ sudo su
# vim /etc/sudoers
```


위 파일을 열었으면 sudo 및에 다음을 추가합니다.

```bash
dlit ALL=(ALL:ALL) ALL:ALL
```


## 2. 유저 삭제 및 홈 디렉토리 삭제

```bash
# userdel -r 계정명
```

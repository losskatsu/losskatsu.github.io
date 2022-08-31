---
title: "[리눅스] AWS 아마존 리눅스 유저 추가하고 password 접속 허용" 
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

# AWS 아마존 리눅스 유저 추가하고 password 접속 허용

**참고 링크**

* [운영체제와 커널의 차이](https://losskatsu.github.io/os-kernel/diff-kernel-os/)
* [bash란? #!/bin/bash의 의미 ](https://losskatsu.github.io/os-kernel/bash/)
* [bashrc와 bash_profile의 차이](https://losskatsu.github.io/os-kernel/bashrc/)
* [컴파일러와 인터프리터의 차이](https://losskatsu.github.io/os-kernel/compiler-interpreter/)
* [리다이렉션, 파이프의 개념](https://losskatsu.github.io/os-kernel/linux-redirection/)
* [크론탭(crontab)을 이용한 작업 스케쥴링](https://losskatsu.github.io/os-kernel/crontab/)
* [AWS EC2 유저 추가](https://losskatsu.github.io/os-kernel/aws-add-user/)


## 1. 서론?

처음에 AWS에 가입하고 EC2 인스턴스를 생성하게 되면 pem키를 생성하게 됩니다. 
그래서 EC2 인스턴스에 접속하려면 pem키를 이용해서 접속하게 되는데, 
이번 포스팅에서는 EC2 인스턴스에서 유저를 추가하고 pem키없이 패스워드 입력방식으로 접속할수 있게끔 작업해보겠습니다. 

## 2. pem 키를 이용한 초기 접속  






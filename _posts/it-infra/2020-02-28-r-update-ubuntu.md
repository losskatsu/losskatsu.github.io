---
title: "[Infra] 우분투에서 R 최신버전으로 업데이트" 
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

# 우분투에서 R 최신버전으로 업데이트

우분투에서 apt-get install r-base로 r을 설치하면 예전 버전이 설치됩니다. 
이는 패키지 이용에 문제가 될 수 있으므로 최신버전이 설치되도록 합시다. 

## 1. 우분투 버전 확인

```bash
$ cat /etc/issue
Ubuntu 18.04.4 LTS \n \l
```
또한 우분투는 버전마다 이름이 있는데요. 

[우분투 버전 확인 링크](https://ko.wikipedia.org/wiki/%EC%9A%B0%EB%B6%84%ED%88%AC_%EB%B2%84%EC%A0%84_%EC%97%AD%EC%82%AC) 

위 사이트로 가시면 버전별 이름을 알수 있는데요. 
제 버전인 18.04는 bionic beavor임을 알 수 있습니다. 

## 2. apt 리스트 수정

```bash
$ sudo nano /etc/apt/sources.list    
```

해당 파일로 들어가셔서 가장 아래에 다음과 같이 한 줄 추가해줍니다. 

```
deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran35/
```

여기서 bionic-cran35가 버전인데요. [https://cloud.r-project.org/bin/linux/ubuntu](https://cloud.r-project.org/bin/linux/ubuntu)에 들어가보시면 우분투 버전별로 디렉터리 이름 확인하실수 있습니다. 

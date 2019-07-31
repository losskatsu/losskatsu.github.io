---
title: "[Infra] 최신버전 curl 설치 " 
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

# 최신버전 curl 설치

아래 링크에서 가장 최신 버전 curl 확인

링크: [https://curl.haxx.se/download/](https://curl.haxx.se/download/)

2019년 7월 31일 기준으로 7.65.3이 최신이므로 해당 버전을 설치하겠습니다. 

```bash
$ wget http://curl.haxx.se/download/curl-7.65.3.tar.gz
$ tar xvfz curl-7.65.3.tar.gz
$ cd cur-7.65.3
$ ./configure
$ make
$ make install
```


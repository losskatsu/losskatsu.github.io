---
title: "[리눅스] 주요 디렉토리 정리" 
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

# 리눅스 - 주요 디렉토리 정리

## 요약 

쉘에 아래 코드를 입력하면 디렉토리별 설명을 간략히 볼 수 있다.

```bash
$ man hier
```

/ : 루트 디렉토리, 최상위 계층, 트리의 시작점.  

/bin : 실행 가능한 프로그램을 모아놓은 디렉토리.  

/boot : 부트 로더(boot loader)에 관한 정적 파일(static files)을 모아놓은 디렉토리. 

/dev : 물리 디바이스(physical devices) 관련 파일 모아놓은 디렉토리.  

/etc : 환경 설정(configuration) 파일 모아놓은 디렉토리  

/home : 유저들을 위한 홈 디렉토리.  

/lib : 부팅할 때 필요한 라이브러리나 루트 파일시스템에서 실행하기 위한 라이브러리가 저장되어 있는 디렉토리. 

/mnt : 마운트 할 때 사용하는 디렉토리 

/root : 루트 계정을 위한 홈 디렉토리. 

/sbin : /bin과 비슷하지만 노멀 유저는 실행할수 없다. 

/usr : 

/var  


## 파일 찾기

```bash
$ which
```


```bash
$ whereis
```

```bash
$ locate
```

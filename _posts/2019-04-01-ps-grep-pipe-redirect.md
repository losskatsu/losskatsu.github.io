---
title: "[리눅스] 프로세스 확인(ps), 파이프, 그렙(grep), 리다이렉션(>)" 
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

# [리눅스]프로세스 확인(ps), 파이프(|), 그렙(grep), 리다이렉션(>)

## ps - 현재 실행 중인 프로세스 확인 

```bash
$ ps -ef | grep apache
```

ps 옵션 | 설명 
--------|------
-e | 모든 프로세스 출력
-f | Full 포맷  

## 파이프(|) - 출력 결과를 필터링

## grep - 파일 패턴을 스캔

* 하위폴더 포함, 존재하는 모든 파일에서 원하는 단어를 찾아주는 명령어

```bash
$ grep -rni [검색어] [경로명 또는 파일명]
```

* r : 하위 디렉토리까지 검색
* n : 파일내 몇번째 라인인지 표시 
* i : 검색어 대소문자 구분없이 검색

* 예) 현재 디렉토리이하 abc라는 문자열 포함되는 경우 검색

```bash
$ grep -rni "abc" ./
```

## find - 하위폴더에 존재하는 파일 찾아줌

```bash
$ find [검색 디렉토리] -iname [파일명]
```

* -name : 대소문자 구분하여 파일명 검색
* -iname : 대소문자 구분하지 않고 파일명 검색 



## 리다이렉션(>) - 출력 결과를 파일로 저장 


기호 | 의미
-----|-----
\>  | 결과를 파일로 저장
\>> | 결과를 기존 파일에 데이터 추가
\<  | 파일 데이터를 입력  

예를 들어,

```bash
$ ls -al > abc.txt
```
라고 하면 ls -al을 입력 후 출력되는 결과물을 abc.txt라는 파일에 저장하라는 뜻. 

기호 | 의미
-----|-----
0  | 표준입력
1 | 표준출력
2  | 표준에러 

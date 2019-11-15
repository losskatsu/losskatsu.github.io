---
title: "[github] 깃헙(github) 기본 사용법 " 
categories:
  - programming
tags:
  - github
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 깃헙(github) 기본 사용법

참고: [소스트리를 이용해 깃헙 작업흐름 ](https://losskatsu.github.io/programming/git-path/)

깃헙 사이트 [github.com](github.com) 에 가서 가입 후 다음을 진행

## 1. Git 설치 

깃 설치 전 사전 설치 프로그램 설치 후 깃 설치.

```bash
// Fedora
$ yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel
$ yum install git-core

// Debian
$ apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev
$ apt-get install git
```

자세한 사항은 아래 링크 참조

[깃 설치하는 법](https://git-scm.com/book/ko/v1/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%84%A4%EC%B9%98)
<br />

## 2. 기본적인 사용법

깃 설치 후 가장 먼저 해야할일은 아이디와 이메일 주소 등록이다. 
예를들어 아이디가 abcde 이고, 이메일이 asdf@asdf.net 인 경우, 

```bash
$ git config --global user.name "abced"
$ git config --global user.email asdf@asdf.net
```

설정확인

```bash
$ git config --list
```

유저네임을 확인하고 싶다면

```bash
$ git config user.name
```

특정 폴더로 이동 후 해당 폴더를 버전 관리 하고 싶다면 그 폴더를 저장소로 만들자.

```bash
$ git init
```

이후 해당 폴더에서 ls -al 을 입력해보면 .git이라는 디렉터리가 생성되었음을 볼 수 있고, 
그 디렉터리 안에서 버전 관리가 되고 있다. 
그럼 해당 디렉터리 안에 있는 파일들을 인터넷 상에 있는 깃헙 저장소에 올려보자. 
만약 a.cpp, b.cpp, c.cpp이라는 파일을 올리고 싶다면 

```bash
$ git add  a.cpp   b.cpp   c.cpp
$ git commit -m "20190112"
```

이 때 -m 옵션은 해당 커밋에 대한 메시지이다. 
커밋을 했으니 인터넷 어디에 올릴 것인지 등록해야한다. 
만약 내가 올리고자 하는 저장소 주소가 https://github.com/abc/abc.git 라면

```bash
$ git remote add origin https:github.com/abc/abc.git
$ git push -u origin master
```

여기서 origin 이라는 것은 단축이름이다. 딱히 의미가 있는건 아니다. 
본인이 짓고 싶은 이름으로 지으면 됨. 여기까지가 깃헙 저장소에 파일 올리는 법.

## 3. 깃 리모트를 변경하고 싶을때

기존 리포지토리 remote 제거

```bash
$ git remote remove origin
```

새로운 리포지토리 remote 추가(예: https://github.com/abc/def.git)

```bash
$ git remote add origin https://github.com/abc/def.git
```

현재 리포지토리 확인법

```bash
$ git remote -v
```

## 4. 저장소에 잘못올린 파일을 지우고 싶을때

a.cpp라는 파일을 지우고 

```bash
$ git rm --cached a.cpp
$ git commit -m "itsmistake"
$ git push origin master
```

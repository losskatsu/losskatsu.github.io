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


## 3. 공개키 설정

```bash
$ gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
```

위 코드는 인터넷에서 보고 친건데, 
나 같은 경우 저렇게 하고 다음 단계를 진행할 경우 마지막 단계인 apt-get update할때 공개키가 없어서 업데이트 안된다고 했다. 
즉, 아래와 같은 에러가 났는데, 

```bash
$ sudo apt-get update
받기:4 https://cloud.r-project.org/bin/linux/ubuntu bionic-cran35/ InRelease [3,626 B]
오류:4 https://cloud.r-project.org/bin/linux/ubuntu bionic-cran35/ InRelease   
  다음 서명들은 공개키가 없기 때문에 인증할 수 없습니다: NO_PUBKEY 51716619E084DAB9
```
그래서 대충 오류메시지 보고 눈치껏 51716619E084DAB9 이걸 써야하나 싶어서 아래와 같이 쳤더니 되더라

```bash
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 51716619E084DAB9
```

### 4. Add it to keyring

```bash
$ gpg -a --export E084DAB9 | sudo apt-key add -
```

좀 웃겼던게 위에서는 E084DAB9 대신에 51716619E084DAB9 이거 썻으니까, 
이번에도 51716619E084DAB9 쓰는 건줄 알았는데 아니다. 그냥 바로 위 코드 치세요. 

### 5. 마무리


```bash
$ sudo apt-get update
$ sudo apt-get upgrade
```

### 6. 확인

```bash
$ R
R version 3.6.2 (2019-12-12)
```

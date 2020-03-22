---
title: "R 마크다운(markdown)으로 pdf 저장하기" 
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

# R 마크다운(markdown)으로 한글 pdf 저장하기

## 사전준비물 - latex 설치

R의 결과물을 pdf파일로 저장하기 위해선 우선 latex가 설치되어있어야 합니다. 
[latex설치 링크](http://wiki.ktug.org/wiki/wiki.php/%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0Windows/tlinstall)로 가시면 
latex를 설치하실수 있습니다. 
기본적인 latex는 영문만 지원하므로, latex로 한글을 출력하기 위해선 kotex를 설치하셔야 합니다. 
[kotex설치 참조 링크](http://www.ktug.org/xe/index.php?mid=Install)로 가시면 설치하실 수 있습니다. 
latex가 꽤 무거운 프로그램이다보니 설치 시간이 다소 걸릴 수 있습니다. 
latex및 kotex를 설치하셨다면 다음 단계로 가시죠. 

## R 패키지 설치

R을 실행한 후 rmarkdown이라는 패키지를 설치해 줍시다. 

```R
install.packages("rmarkdown")
```



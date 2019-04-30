---
title: "[Excel] 엑셀 두 셀 간 시간차 구하기" 
categories:
  - programming
tags:
  - programming
  - java
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

* 엑셀 두 셀 간 시간차 구하기

예를들어, 
<br /> 

A = 2019-04-21 10:34:45, B = 2019-04-21 10:34:51 
<br />

이라고 하면,

* 시간 차이 : =INT((B - A)*24)
* 분 차이 : =(B - A)*1440
* 초 차이 : =(B - A)*86400 


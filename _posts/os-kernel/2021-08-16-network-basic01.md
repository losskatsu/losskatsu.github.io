---
title: "네트워크 기초(1) - OSI 7계층, 물리 계층" 
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

# 네트워크 기초(1) - OSI 7계층, 물리 계층



## 1. 서론, 옛날 그 시절

예전에는 같은 회사의 컴퓨터끼리만 통신이 가능했던 시절이 있습니다. 
예를 들어, 삼성 컴퓨터랑 LG 컴퓨터는 서로 통신을 할 수 없는 것입니다. 
따라서 이러한 문제를 해결하기 위해, 서로다른 컴퓨터 회사들의 컴퓨터들이 자유롭게 통신할 수 있도록 
ISO(International Organization for Standardization, 국제표준화기구)에서 OSI 모델이라는 표준 규격을 만들었습니다. 

계층 | 이름 | 설명
-----|-------|-------------------
7계층 | 응용 계층(Application) | 애플리케이션 서비스 제공
6계층 | 표현 계층(Presentation) | 문자코드, 압축, 암호화
5계층 | 세션 계층(Session) | 통신 방식 결정
4계층 | 전송 계층(Transport) | 신뢰성 있는 통신 구현
3계층 | 네트워크 계층(Network) | 다른 네트워크와 통신하기 위한 IP주소 결정
2계층 | 데이터링크 계층(Data Link) | 물리주소 결정
1계층 | 물리 계층(Physical Layer) | 물리적인 연결과 전기 신호 변환

위 표가 바로 그 유명한 OSI 7 계층 입니다. 



참고도서: 모두의 네트워크, 길벗, 2018

---
title: "[운영체제] 시스템 성능 구조와 최적화(네트워크)" 
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

# 시스템 성능 구조와 최적화 - 네트워크

네트워크 분석은 하드웨어와 소프트웨어에 걸쳐 있다. 


네트워크는 혼잡 가능성이 있기 때문에 낮은 성능의 원인으로 자주 지적 받곤 한다. 

* 인터페이스: 물리적 네트워크 커넥터를 의미
* 패킷(packet): IP 수준의 라우팅 가능한 메시지를 의미
* 프레임(frame): 물리적인 네트워크 수준의 메시지를 의미. 
* 대역폭(bandwidth): 최대 데이터 전송 비율
* 스루풋: 두 네트워크 끝점 사이의 현재 데이터 전송 비율
* 지연시간: 어떤 메시지가 두 끝점 사이를 왕복하는데 걸린 시간 또는 connection맺는데 걸린 시간. 


네트워크 인터페이스: 네트워크 연결을 위한 운영체제의 끝점. 
인터페이스는 시스템 관리자가 설정하고 관리하는 추상적인 요소임. 





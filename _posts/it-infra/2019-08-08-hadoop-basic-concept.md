---
title: "빅데이터 처리, 분석을 위한 하둡(hadoop) 기본개념" 
categories:
  - it-infra
tags:
  - it-infra
  - big-data
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 하둡(hadoop) 기본개념

빅데이터 시스템에서 가장 중요한 부분은 데이터 수집. 
수집 용도로 많이 쓰이는 오픈소스는 Flume, Chukwa 등. 
메세징 기반으로 구성된 Kafka를 사용하기도 함. 
하둡은 대용량 데이터의 배치 프로세싱에 적합. 
만약 데이터의 실시간 액세스를 원한다면 하둡은 적합하지 않음. 

* 하둡의 구성
    1. HDFS(Hadoop Distributed File System)이라는 분산 파일 시스템
    2. MapReduce 라고 부르는 분산 처리 시스템

참고: [파일시스템](https://losskatsu.github.io/os-kernel/os-linux-structure/)

처리된 데이터를 기존 관계형 데이터베이스(MySQL, 오라클 등)에 넣어주길 원한다면 [Sqoop](https://losskatsu.github.io/it-infra/sqoop/)을 이용.




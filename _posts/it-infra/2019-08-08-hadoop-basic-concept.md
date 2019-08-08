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

HDFS, MapReduce 모두 마스터/슬레이브 구조. 

구분 | HDFS | MapReduce
--|------|----------
마스터 | 네임노드 | 데이터노드
슬레이브 | 잡트래커 | 태스크트래커

HDFS 자체는 독립적으로 분산 파일 시스템으로 쓰일 수 있찌만, 
MapReduce 프레임워크의 경우 처리할 입력 데이터를 HDFS에서 읽어들이고, 
처리된 데이터를 다시 HDFS에 씀. 즉 MapReduce는 데이터의 읽기, 쓰기를 위해 HDFS를 필요로 함. 

하나의 HDFS에는 하나의 네임 스페이스 제공. 즉, 모든 사용자가 하나의 동일 루트에서 시작하는 파일 시스템이라는 뜻. 
파일 시스템이라는 용어를 사용해서 뭔가 새로운 파일 시스템이라고 생각할 수 있지만, 그건 아님. 
기존 운영체제의 파일 시스템을 그대로 사용함. 
즉, 데이터 노드를 설치하기 위해 따로 파일 시스템을 설치할 필요는 없고, 특정 디렉터리를 
데이터노드가 블록을 저장할 장소로 정하기만 하면 데이터노드는 그 디렉토리를 자기 블록 데이터들을 저장하는데 사용함. 






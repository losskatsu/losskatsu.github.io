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

**참고사항** <br />
[스쿱(sqoop)에 대해 알아보자](https://losskatsu.github.io/it-infra/sqoop/) <br />
[엘라스틱서치에 대해 알아보자](https://losskatsu.github.io/it-infra/es-basic/)
[하둡 홈페이지](http://hadoop.apache.org/)


하둡(hadoop)은 대용량 데이터를 분산처리 해주는 아파치 톱 레벨 오픈소스 프로젝트이며,  자바로 작성된 프레임워크입니다. 
빅데이터 시스템에서 가장 중요한 부분은 데이터 수집인데요. 
수집 용도로 많이 쓰이는 오픈소스는 Flume, Chukwa 등. 
메세징 기반으로 구성된 Kafka를 사용하기도 함. 
하둡은 대용량 데이터의 배치 프로세싱에 적합. 
만약 데이터의 실시간 액세스를 원한다면 하둡은 적합하지 않음. 

## 하둡의 구성 

* 하둡의 구성
    1. HDFS(Hadoop Distributed File System)이라는 분산 파일 시스템
    2. MapReduce 라고 부르는 분산 처리 시스템

참고: [파일시스템](https://losskatsu.github.io/os-kernel/os-linux-structure/)

하둡의 분산파일시스템인 HDFS와 분산 처리 시스템인 MapReduce는 물리적으로 같은 서버들에 공존하는 것이 일반적임. 
두 시스템 모두 하나의 마스터와 다중 슬레이브 구조를 갖는데, 
다중 슬레이브의 경우 각 서버마다 HDFS 슬레이브와 MapReduce 슬레이브가 같이 놓인다는 것이다. 
처리된 데이터를 기존 관계형 데이터베이스(MySQL, 오라클 등)에 넣어주길 원한다면 [Sqoop](https://losskatsu.github.io/it-infra/sqoop/)을 이용.

## 데이터가 있는 곳으로 코드를 이동

대부분의 경우 테이터의 크기가 소스코드보다 훨씬 크기 때문에 코드가 있는 곳으로 데이터를 복사해오는 것보다 
데이터가 있는 곳으로 코드를 복사해가는 것이 효율적이다. 
따라서 처리하고자 하는 데이터를 갖고 있는 서버를 골라 그 서버에 코드를 보내고 코드를 실행한다. 

## 병렬처리를 위한 데이터 모델

* 데이터 = 레코드의 집합
* 각 레코드는 키, 값(value)를 가짐.

HDFS, MapReduce 모두 마스터/슬레이브 구조. 

구분 | HDFS | MapReduce
--|------|----------
마스터 | 네임노드 | 잡트래커
슬레이브 | 데이터노드 | 태스크트래커

HDFS 자체는 독립적으로 분산 파일 시스템으로 쓰일 수 있찌만, 
MapReduce 프레임워크의 경우 처리할 입력 데이터를 HDFS에서 읽어들이고, 
처리된 데이터를 다시 HDFS에 씀. 즉 MapReduce는 데이터의 읽기, 쓰기를 위해 HDFS를 필요로 함. 

하나의 HDFS에는 하나의 네임 스페이스 제공. 즉, 모든 사용자가 하나의 동일 루트에서 시작하는 파일 시스템이라는 뜻. 
파일 시스템이라는 용어를 사용해서 뭔가 새로운 파일 시스템이라고 생각할 수 있지만, 그건 아님. 
기존 운영체제의 파일 시스템을 그대로 사용함. 
즉, 데이터 노드를 설치하기 위해 따로 파일 시스템을 설치할 필요는 없고, 특정 디렉터리를 
데이터노드가 블록을 저장할 장소로 정하기만 하면 데이터노드는 그 디렉토리를 자기 블록 데이터들을 저장하는데 사용함. 

하둡은 오프라인 배치 처리에 적합한 프레임워크이므로 실시간 처리에는 적합하지 않음. 

하둡을 사용하면 하드웨어 고장에 대해서도 유연하게 대처가능하다. 
그 이유는 데이터블록을 보통 3군데에 저장하며 저장시 같은 랙(Rack)에 있는 서버를 두 개에 저장하고 
다른 하나는 다른 랙에 있는  서버에 저장하는 방식을 택하기 때문이다. 
3군데는 복제본 개수(Replication Factor)라고 하며 이는 설정에서 바꿀 수 있다. 
만약 네임노드(마스터)가 특정 데이터노드의 문제 발생을 알아채면 바로 해당 데이터노드에 있는 데이터 블록들을 다른 데이터노드로 복제함. 
즉, 언제나 정해진 복제본 개수를 준수한다. 

* 랙(Rack 혹은 캐비넷): 데이터 센터 내에서 여러 장비들을 적재하기 위한 표준 프레임을 말한다. 폭은 19 또는 23인치 높이(U)는 42 또는 44U이며 1U = 1.75인치(4.45cm)에 해당한다. 보통 랙에는 서버들이 놓이지만 맨 윗단이나 중간에 랙 내의 서버들을 연결하기 위한 네트워크 스위치를 넣는다. 

## HDFS 환경설정

* conf 디렉토리 하위의 hdfs-site.xml 파일에서 HDFS 환경설정 가능.
* HDFS 파일 블록 크기 설정: dfs.block.size
* HDFS 복제본 갯수 설정: dfs.replication

## 1. 맵리듀스(MapReduce)

데이터를 처리하는데 있어 맵과 리듀스라는 두개의 작업을 사용함. 
맵, 리듀스를 사용해서 한 데이터를 다른 데이터셋으로 변환하게 되는데 
이를 레코드 레벨에서 생각하면 한 레코드에서 다른 레코드로 변환한다는 것이고, 
이 의미는 최종적으로 한 형태의 키/값 쌍이 다른 형태의 키/값 쌍으로 변환 한다는 의미임. 

이 처리는 레코드 별로 이루어지고 그렇기 때문에 원칙적으로 처리하는 레코드만 보고 작업하면 되므로 병렬성이 높고 
따라서 다수의 서버에서 실행하기 쉽다는 장점이 있음. 
개발자는 맵과 리듀스의 두 개의 함수만 구현하고 처리할 입력 데이터가 HDFS 상의 어디에 있는지와 
처리된 데이터가 어디 저장될지만 지정해주면 나머지는 프레임워크가 병렬로 처리해주게 된다. 


## 하둡 명령어 정리

```bash
//파일 내용 나타내기
$ hdfs dfs -cat FILE

//파일과 디렉터리에 대한 그룹 변경
$ hdfs dfs -chgrp GROUP PATH 

//파일과 디렉터리 권한 변경 
$ hdfs dfs -chmod MODE PATH

//파일과 디렉터리 소유자 변경
$ hdfs dfs -chown PATH 

//로컬 파일시스템으로 부터 파일 복사
$ hdfs dfs -copyFromLocal LOCALSRC DST 

//파일들을 로컬 파일 시스템으로 복사
$ hdfs dfs -copyToLocal SRC LOCALDST

//LOCALSRC를 HDFS에 복사후 해당파일은 삭제됨.
$ hdfs dfs -moveFromLocal LOCALSRC DST 

//PATH에 있는 모든 파일과 디렉토리에 대한 이름, 사용된 바이트 수, 파일 개수, 하위 디렉터리 갯수 출력
$ hdfs dfs -count PATH 

//SRC로부터 DST로 파일 복사
$ hdfs dfs -cp SRC DST 

//파일 크기 출력
$ hdfs dfs -du PATH 

//휴지통 비우기 
$ hdfs dfs -expunge 

//리눅스의 ls와 동일
$ hdfs dfs -ls PATH 

//디렉터리 생성. 리눅스의 mkdir과 동일
$ hdfs dfs -mkdir PATH 

//파일 통계 정보
$ hdfs dfs -stat PATH 
```

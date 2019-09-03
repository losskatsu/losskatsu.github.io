---
title: "[Infra] mysql 정리 " 
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

# mysql 정리

## mysql MMM 구조

MMM이란 Multi-Master replication Manager for MySQL의 줄임말로, 
기본적으로 한쪽이 마스터, 다른쪽이 슬레이브이지만 
이슈발생시 슬레이브가 마스터가 될 수 있는 이중화 구조 중 하나.



## mysql 인덱스(index)

### 책의 찾아보기와 비유

책의 마지막에 있는 "찾아보기"가 인덱스에 비유된다면 책의 내용은 데이터 파일에 해당한다고 볼 수 있다. 

* 찾아보기 : 페이지번호 = 인덱스 : 데이터파일에 저장된 레코드 주소
* DBMS도 데이터베이스 테이블의 모든 데이터를 검색해서 원하는 결과를 가져오려면 시간이 오래걸림. 
* 시간이 오래걸리므로, 칼럼값과 해당레코드가 저장된 주소를 키-값쌍(Key-Value pair)으로 인덱스를 만듦.
* 찾아보기와 인덱스의 공통점 = 정렬

### 자료구조와 비유

* 인덱스   
SortedList와 같은 자료구조, 저장되는 값을 항상 정렬된 상태로 유지하는 자료구조, 데이터가 저장 될때마다 항상 값을 정렬해야 하므로, 
저장하는 과정이 복잡하고 느리지만, 이미 정렬돼 있어서 아주 빨리 원하는 값을 찾아올 수 있음. 
즉, INSERT, UPDATE, DELETE 문장의 처리는 느리지만 
SELECT 문장은 매우 빠르게 처리할 수 있다. 결국, INSERT, UPDATE, DELETE 성능을 희생하는 대신 데이터 읽기 속도를 높이는 기능. 
즉, 인덱스 하나를 추가할 지 말지는 데이터의 저장 속도를 어디까지 희생할 수 있는지, 읽기 속도를 얼마나 더 빠르게 만들어야 하는지에 
따라 결정되야 한다. 

* 데이터파일     
ArrayList와 같은 자료구조, 저장되는 순서대로 유지하는 자료구조

### 인덱스의 구분

* 프라이머리 키(Primary key)  
레코드를 대표하는 칼럼의 값으로 만들어진 인덱스를 의미. 이 칼럼은 테이블에서 해당 레코드를 식별할 수 있는 기준값이 되기 때문에 
이를 식별자라고 부른다. 프라이머리키는 NULL값과 중복을 허용하지 않는다. 

* 보조 키(Secondary key)


참고자료 : real mysql

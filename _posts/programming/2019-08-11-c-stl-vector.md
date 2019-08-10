---
title: "[C언어] C++ STL 벡터(vector) 사용법 정리" 
categories:
  - programming
tags:
  - programming
  - algorithm
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---


# C++ STL 벡터(vector) 사용법 정리

## 1. 관련 함수 정리

#### 반복자

* begin(): beginning iterator 반환
* end(): end iterator 반환 

#### 삽입

* push_back(element): 벡터 맨 뒤에 원소 추가

#### 삭제

* pop_back(): 벡터 맨 뒤의 원소 삭제

#### 조회

* [i] : i번째 원소 반환
* at(i) : i번째 원소 반환
* front() : 첫번째 원소 반환
* back() : 마지막 원소 반환

#### 기타

* empty() : 벡터가 비어있는지 여부 판단
* size() : 벡터 사이즈

## 2 벡터 사용 예

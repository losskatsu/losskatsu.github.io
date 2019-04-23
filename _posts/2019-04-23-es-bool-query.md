---
title: "[Infra] 엘라스틱서치(ElasticsSearch) 불(bool) 쿼리, query, bool, must, range " 
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

# 엘라스틱서치(ElasticsSearch) 불(bool) 쿼리

* 엘라스틱서치에는 아래와 같이 여러 종류의 쿼리가 존재함.
* 텀(term) 쿼리
* 매치(match) 쿼리
* 불(bool) 쿼리
* 문자열(string) 쿼리
* 접두어(prefix) 쿼리
* 범위(range) 쿼리
* 전체 매치(match_all) 쿼리
* 퍼지(fuzzy) 쿼리

코드를 보다가 

```elasticsearch
"query":{
  "bool":{
    "must":{
      [{"range":
```
라는 부분이 나와서 이게 뭔가 싶었다. 

엘라스틱 서치에는 다양한 종류의 쿼리가 있고, 내가 본 코드에는 
불 코드와 범위 쿼리가 사용된 듯 싶다. 



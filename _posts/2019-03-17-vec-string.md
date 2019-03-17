---
title: "[C++]벡터(vector), 문자열(string) 정리" 
categories:
  - Programming
tags:
  - Programming
  - Algorithm
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---


## [C++] 벡터(vector), 문자열(string) 정리

C++에서 알고리즘 문제를 풀때, 벡터와 문자열을 자주 사용하는데, 아주 기본적인 사항을 정리합니다. 

### 1. 라이브러리

```
#include <vector>
#include <string>
```
벡터와 문자열을 사용하기 위한 라이브러리 입니다. 


### 2. 벡터(vector)

벡터를 초기화할때는 첫 요소(element)를 정하는 것이 좋습니다. 

``` 
// 벡터 v1의 초기화
vector <int> v1 = {}; 
```
예를들어 위와 같이 벡터 v1을 초기화 했다고 했을때, 자신이 첫번째 요소로 5를 추가하고 싶어서

```
v1[0] = 5; // 컴파일 에러
v1.push_back(5); // 컴파일 성공
```
첫번째와 같이 v1[0]=5 라고 했을 경우, 컴파일 에러가 나게 됩니다. 
두번째 문장과 같이 push_back(5)를 사용해야 첫번째 요소를 5로 정할 수 있습니다. 
그럼 두번째 요소는 어떨까요?
두번째 요소부터는 v1[1]을 사용하던 push_back을 사용하던 문제없습니다.

```
v1[1] = 3; // 컴파일 성공
v1.push_back(3); // 컴파일 성공
```
다만 문제를 급박하게 풀언가나는 상황에선 헷갈릴 수 있으니,
아래와 같이 벡터의 첫 요소를 정하는 초기화를 추천드립니다.

```
vector <int> v1 = {0};
```

### 2. 문자열(string)

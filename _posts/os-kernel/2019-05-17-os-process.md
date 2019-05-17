---
title: "[OS] 프로세스(process)란 " 
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

# 프로세스(process)란?

예전 컴퓨터는 한번에 하나의 프로그램만 실행가능 했었다. 
그리고 실행중인 프로그램은 모든 시스템 자원을 사용했었다. 
시간이 흘러 현대의 컴퓨터는 여러 프로그램을 메모리에 올리고 동시에 실행이 가능하다. 
여기서 프로세스(process)라는 개념이 탄생하는데, 여러 프로그램 중 실행중인 프로그램을 프로세스라고 한다. 
현대 개발자는 프로세스는 작업 단위로 생각한다. 
그러므로 시스템은 프로세스의 집합이라고 생각할 수 있다. 
OS는 시스템 코드 뿐만 아니라 유저가 실행한 코드도 실행한다. 

## 프로세스 개념


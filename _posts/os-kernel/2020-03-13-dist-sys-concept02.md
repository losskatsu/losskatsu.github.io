---
title: "분산 처리 시스템의 개념 이해(2) RPC, 쓰레드" 
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

# 분산 시스템의 개념(2)

본 포스팅은 MIT 6.284 Distributed Systems을 참고하여 작성 되었습니다.

이 포스팅은 C++로 진행되지만, 여러분이 자바, 파이썬, C# 무엇을 쓰던 상관은 없습니다. 모든 언어가 필요한 기능을 제공하기 때문이죠. 
예를 들어, 쓰레드, 잠금(locking), 쓰레드간 동기화(synchronization) 같은 RPC(Remote Procedure call) 패키지를 제공합니다. 
이러한 패키지들은 메모리 관리나 가비지컬렉션을 제공하는데, 분산시스템에서 쓰레드와 가비지 컬렉션의 조합은 아주 중요합니다. 
왜냐하면 C++같은 non 가비지 컬랙션 랭기지에서 쓰레드를 사용하면 항상 복잡해지고(puzzle), 
마지막 쓰레드가 사용을 끝냈는지 확인을 하는 등 엄청나게 많은 예약(bookkeeping)이 필요하기 때문입니다. 
C++의 단점은 코딩을 하다가 컴파일 과정에서 엄청나게 많은 에러메시지를 토해내는데, 
C++의 에러메시지는 파고들만한 가치가 없습니다. 
그저 몇 번째 라인이 틀렸는지 확인하는 정도 입니다. 너무 복잡하기 때문이죠. 

## 쓰레드(Threads)

이 포스팅에서 쓰레드를 중요시 하는 이유는 동시성(concurrency)를 유지하는 도구이기 때문입니다. 
동시성은 분산 시스템에서 아주 중요한데, 
수많은 클라이언트가 서버에 동시에 요청하고, 심지어 서버들끼리도 동시에 요청하는 경우가 많기 때문입니다. 



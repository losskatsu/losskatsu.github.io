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


**참고링크**

* [프로세스란?](https://losskatsu.github.io/os-kernel/os-process/)
* [리다이렉션, 파이프 개념](https://losskatsu.github.io/os-kernel/linux-redirection/)
* [네임스페이스 개념](https://losskatsu.github.io/os-kernel/linux-namespace/)
* [분산시스템 개념(1)](https://losskatsu.github.io/os-kernel/dist-sys-concept01/)
* [분산시스템 개념(2)](https://losskatsu.github.io/os-kernel/dist-sys-concept02/)
* [프로그램, 바이너리, 프로세스, 스레드의 개념](https://losskatsu.github.io/os-kernel/process-thread/)



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
쓰레드가 무엇일까요? 
하나의 프로그램이 있고 하나의 주소공간(address space)가 있다고 합시다. 
하나의 프로그램카운터, 하나의 레지스터세트, 하나의 스택. 
이러한 것들이 쓰레드 프로그램의 하나의 현재실행상태를 묘사합니다. 
쓰레드는 여러개가 될 수 있는데, 이것들은 동시에 실행될 수 있습니다. 
분리된 프로그램 카운터, 분리된 레지스터세트, 분리된 스택들이 각각 분리된 쓰레드를 컨트롤 하고 실행합니다. 
이 각각의 쓰레드들은 하나의 프로그램에서 서로 다른 파트를 담당합니다. 

**쓰레드를 사용하는 이유1. I/O 동시성(concurrency)**

예전에는 어떤 쓰레드가 디스크에서 무엇인가 읽기 위해 기다린다고 했을 때, 
또다른 쓰레드는 계산을 준비하거나, 네트워크 메시지 전송을 기다렸었습니다. 
이러한 불편함 때문에 I/O 동시성이라는 개념이 생긴건데요. 
I/O 동시성을 활용하면,  각 쓰레드는  RPC 요청 메시지를 동시에 보낼수있습니다. 
즉, I/O 동시성이란 서로다른 활동이 중복(overlapping) 된다는 것이고, 하나의 활동이 진행중일때 다른 것이 기다릴 수도 있습니다. 

**쓰레드를 사용하는 이유2. Parallelism**

**쓰레드를 사용하는 이유3. Convenience** 

여러분은 마스터 서버를 통해 나머지 서버들이 잘 돌아가고 있는지 확인 가능합니다. 

**반례-Event-driven**
이러한 동시성과 반대되는 개념이 Event-driven
이것은 하나의 쓰레드와 하나의 루프를 가지고 있는데, 
이 루프에서 기다리고 있는건 사용자가 요청하는 인풋이나 트리거 이벤트입니다. 
주로 윈도우에서 사용자입력을 기다리는 형태로 많이 사용하는데요, 
이런 event-driven은 하나하나씩 처리합니다. 

**예**

오직 한번에 하나씩만 처리하는 싱글 머신을 상상해봅시다. 
만약 이 머신에 여러 프로세스를 실행한다고 했을 때, 
운영체제는 CPU를 두개의 프로그램을 번갈아가며 할당합니다. 

## 쓰레드 사용이 어려운점

쓰레드끼리 메모리를 공유할때 어려운 점이 발생한다. 


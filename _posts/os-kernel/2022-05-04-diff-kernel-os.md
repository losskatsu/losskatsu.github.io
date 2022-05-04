---
title: "[리눅스] 운영체제 vs 커널 차이" 
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

# [리눅스] 운영체제 vs 커널 차이

**참고 링크**

* [운영체제와 커널의 차이](https://losskatsu.github.io/os-kernel/diff-kernel-os/)
* [bash란? #!/bin/bash의 의미 ](https://losskatsu.github.io/os-kernel/bash/)
* [bashrc와 bash_profile의 차이](https://losskatsu.github.io/os-kernel/bashrc/)
* [컴파일러와 인터프리터의 차이](https://losskatsu.github.io/os-kernel/compiler-interpreter/)


## 1. 커널

커널(kernel)은 운영체제의 핵심 파트 입니다. 
즉, 커널은 운영체제의 일부분이라고 할 수 있습니다. 
커널은 여러분들이 컴퓨터를 켰을때, 
가장 먼저 메인 메모리에 올라가는 프로그램 입니다. 
커널은 여러분들이 컴퓨터를 켰을때 메모리에 올라가서 컴퓨터를 끌때까지 내려가지 않습니다. 
커널은 메모리에 항상 머무릅니다. 

<center><img src="/assets/images/os/kernel-vs-os/kernel-os01.png" width="800"></center>

커널은 응용소프트웨어와 하드웨어를 이어주는 브릿지(bridge) 역할을 합니다. 

커널은 운영체제의 핵심 파트라고 했는데, 커널없이는 운영체제가 실행 될 수 없습니다. 
커널이 담당하는 부분은 메모리 관리(memory management), 프로세스 관리(process management), 
테스크 관리(task management), 디스크 관리(disk management)가 있습니다. 

우리가 응용프로그램을 실행하면 커널은 충분한 메모리 공간이 있는지 체크합니다. 

## 2. 운영체제

운영체제(operating system)는 시스템 소프트웨어로 시스템 리소스를 관리합니다. 
운영체제가 담당하는 부분은 커널이 담당하는 부분에 추가적으로 protection, security도 담당합니다. 
뿐만아니라 운영체제는 프로그램 실행중 인터럽트 핸들링도 담당합니다.


## 3. 운영체제와 커널의 차이

커널은 소프트웨어와 하드웨어를 이어주는 인터페이스 인 반면, 
운영체제는 유저와 하드웨어를 이어주는 인터페이스라고 할 수 있습니다.

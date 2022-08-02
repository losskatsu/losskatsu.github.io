---
title: "[리눅스] 네임스페이스(namespace) 개념" 
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

# 리눅스 - 네임스페이스(namespace)의 개념


**참고링크**

* [프로세스란?](https://losskatsu.github.io/os-kernel/os-process/)
* [리다이렉션, 파이프 개념](https://losskatsu.github.io/os-kernel/linux-redirection/)
* [네임스페이스 개념](https://losskatsu.github.io/os-kernel/linux-namespace/)
* [분산시스템 개념(1)](https://losskatsu.github.io/os-kernel/dist-sys-concept01/)
* [분산시스템 개념(2)](https://losskatsu.github.io/os-kernel/dist-sys-concept02/)
* [프로그램, 바이너리, 프로세스, 스레드의 개념](https://losskatsu.github.io/os-kernel/process-thread/)



## 1. 네임스페이스?

### 1.1. 개념

네임스페이스는 최근 유행하는 도커(docker)와 같은 컨테이너(container) 기반의 가상화 기술의 기반이 되는 기능(feature)입니다. 
네임스페이스는 동일한 시스템에서 별개의 독립된 공간을 격리된 환경에서 운영하는 가상화 기술입니다. 
이는 아파트가 각 호실별로 격리된 주거환경을 제공하는 것과 비슷한 개념으로 생각하면 됩니다. 

## 1-2. 하이퍼바이저와의 차이

네임스페이스는 하이퍼바이저(hypervisor)와 비슷하다고 생각할 수 있지만 차이가 있습니다. 
하이버바이저의 경우 하드웨어(hardware) 자체를 가상화합니다. 
하이퍼바이저는 하드웨어를 물리적으로 구분해서 가상화 한다고 생각할 수 있습니다. 
따라서 하이퍼바이저 위에 올라가는 게스트 OS는 서로 물리적으로 구분된 공간에서 돌아갑니다. 
그러나 네임스페이스는 하드웨어를 분리하지는 않습니다. 
동일한 OS 및 커널(kernel)을 깔고 그 위에서 돌아갑니다. 


## 2. 네임스페이스 확인

### 2-1. 프로세스 네임스페이스 확인

먼저 ```/proc```디렉토리를 보겠습니다. 
```/proc``` 디렉토리는 프로세스 정보가 있는 디렉토리이며, 컴퓨터를 켜기 전에는 빈 디렉토리 이지만
부팅하면서 내용물이 채워지는 디렉토리 입니다. 

1번 프로세스의 네임스페이스를 확인해보겠습니다. 

```bash
$ cd /proc/1/ns
$ sudo ls -al
합계 0
dr-x--x--x 2 root root 0  8월  2 08:58 .
dr-xr-xr-x 9 root root 0  7월 30 17:57 ..
lrwxrwxrwx 1 root root 0  8월  2 08:59 cgroup -> 'cgroup:[4026531835]'
lrwxrwxrwx 1 root root 0  8월  2 08:59 ipc -> 'ipc:[4026531839]'
lrwxrwxrwx 1 root root 0  8월  2 08:59 mnt -> 'mnt:[4026531840]'
lrwxrwxrwx 1 root root 0  8월  2 08:59 net -> 'net:[4026531992]'
lrwxrwxrwx 1 root root 0  8월  2 08:59 pid -> 'pid:[4026531836]'
lrwxrwxrwx 1 root root 0  8월  2 08:59 pid_for_children -> 'pid:[4026531836]'
lrwxrwxrwx 1 root root 0  8월  2 08:59 user -> 'user:[4026531837]'
lrwxrwxrwx 1 root root 0  8월  2 08:59 uts -> 'uts:[4026531838]'
```

## 3. 네임스페이스의 종류

리눅스 네임스페이스는 크게 6가지로 나눌수 있습니다. 
네임스페이스는 unshare라는 명령어를 통해 네임스페이스를 구성할 수 있습니다. 

### 3.1 UTS namespace

hostname을 네임스페이스 별로 분할 격리 시켜줍니다. 
이는 리눅스 시스템 콜 중 하나인 uname에서 utsname이라는 구조체에 정의된 식별자 중 노드네임(nodename)을 isolate 하는 것입니다. 

아래는 /usr/include/linux/utsname.h 내부 코드 입니다.

```c
#define __NEW_UTS_LEN 64

struct new_utsname {
  char sysname[__NEW_UTS_LEN + 1];
  char nodename[__NEW_UTS_LEN + 1];
  char release[__NEW_UTS_LEN + 1];
  char version[__NEW_UTS_LEN + 1];
  char machine[__NEW_UTS_LEN + 1];
  char domainname[__NEW_UTS_LEN + 1];
};
```

UTS 네임스페이스 사용법은 아래와 같이 unshare에 -u 옵션을 써서 사용합니다.  

```bash
$ unshare -u /bin/bash
```

예를 들면 아래와 같이 사용합니다. 

```bash
user@testcomputer:~$ hostname
testcomputer
user@testcomputer:~$ sudo unshare -u /bin/bash
root@testcomputer:~# hostname newhost
root@testcomputer:~# hostname 
newhost
root@testcomputer:~# exit
exit
user@testcomputer:~$ hostname
testcomputer
```

### 3.2 IPC namespace

IPC는 프로세스간 데이터를 주고받는 경로를 의미합니다. 
IPC 네임스페이스는 IPC 리소스를 분할 격리 시켜줍니다. 즉, 프로세스간 통신을 격리시킵니다. 
semaphore, file locking, mutex 와 같은 것에 대한 접근 제어를 제공합니다. 

### 3.3 PID namespace

PID(process ID)를 분할 관리합니다. 
PID 네임스페이스를 이용하면 하나의 시스템에서 동일한 PID가 2개인것처럼보이게 프로세스를 만들 수 있습니다. 

### 3.4 NS namespace

파일 시스템의 마운트(mount)지점을 분할하여 격리합니다.

### 3.5 NET namespace

네트워크 인터페이스, iptables 등 네트워크 리소스와 관련된 정보를 분할합니다. 

### 3.6 USER namespace

user와 group ID를 분할하고 격리합니다. 



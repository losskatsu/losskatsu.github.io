---
title: "[운영체제] 시스템 성능 구조와 최적화(네트워크)" 
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

# 시스템 성능 구조와 최적화 - 네트워크

네트워크 분석은 하드웨어와 소프트웨어에 걸쳐 있다. 
네트워크는 혼잡 가능성이 있기 때문에 낮은 성능의 원인으로 자주 지적 받곤 한다. 
통신은 패킷이라고 하는 메시지를 전송하는 방식으로 이뤄지며, 
패킷은 보통 페이로드 데이터를 담는다.  
캡슐화는 메타 데이터를 페이로드의 앞부분과 끝 부분 뒤를 추가하는 것이다. 

* 인터페이스: 물리적 네트워크 커넥터를 의미
* 패킷(packet): IP 수준의 라우팅 가능한 메시지를 의미
* 프레임(frame): 물리적인 네트워크 수준의 메시지를 의미. 
* 대역폭(bandwidth): 최대 데이터 전송 비율
* 스루풋: 두 네트워크 끝점 사이의 현재 데이터 전송 비율
* 지연시간: 어떤 메시지가 두 끝점 사이를 왕복하는데 걸린 시간 또는 connection맺는데 걸린 시간. 
* 페이로드(payload): 사용에 있어 전송되는 데이터를 의미. 
* Maximum Transmission Unit(MTU): 최대 전송 유닛

네트워크 인터페이스: 네트워크 연결을 위한 운영체제의 끝점. 
인터페이스는 시스템 관리자가 설정하고 관리하는 추상적인 요소임. 


## netstat 

옵션 | 설명
----|------
기본 | 연결한 소켓 목록을 보여줌
-a | 모든 소켓의 정보 목록을 보여줌
-s | 네트워크 스택 통계를 보여줌
-i | 네트워크 인터페이스 통계를 보여줌
-r | 라우팅 테이블을 보여줌

<br />

결과창 | 설명
-------|-----
Iface | 네트워크 인터페이스
MTU | 최대전송 유닛
RX- | 수신
TX- | 송신 
OK | 전송에 성공한 패킷 수
ERR | 패킷 오류 수
DRP | 드롭한 패킷 수
OVR | 패킷 오버런(overrun) 수

<br />

좀 더 세부적인 내용은 아래 디렉토리 참조

```bash
$ cd /proc/net/snmp
$ cd /proc/net/netstat

$ grep ^Tcp /proc/net/snmp
```

## sar

시스템 활동 보고(system activity reporter)를 의미. 

옵션 | 설명
-----|-----
\-n DEV | 네트워크 인터페이스 통계
\-n EDEV | 네트워크 인터페이스 오류
\-n IP | IP 데이터그램 통계
\-n EIP | IP 오류 통계
\-n TCP | TCP 통계
\-n ETCP | TCP 오류 통계
\-n SOCK | 


## ping

ping 명령은 ICMP 메아리 요청 패킷을 보내서 네트워크 연결성을 테스트한다. 

```bash
$ ping www.naver.com
```

## tcpdump

tcpdump를 이용하면 네트워크 패킷을 캡처해 분석할 수 있다. 
이 도구는 패킷 요약을 STDOUT에 출력하거나 패킷 데이터를 나중에 분석할 수 있게 파일에 저장할 수 있다. 
보통 후자 쪽이 더 실용적이다. 
왜냐면 패킷 도착 속도가 너무 빨라서 실시간으로 요약 정보를 쫓아갈 수 없기 때문이다. 

```bash
$ tcpdump -i eth4 -w /tmp/out.tcpdump
$ tcpdump -n /tmp/out.tcpdump
$ tcpdump -enr /tmp/out.tcpdump -vvv -X
```

## DTrace

DTrace를 이용하면 네트워크 이벤트를 커널과 애플리케이션 내부에서 살펴볼 수 있다. 
소켓 연결, 소켓 I/O, TCP이벤트, 패킷 전송, 백로그 드롭, TCP 재전송 등 여러 자세한 부분을 살펴볼 수 있다. 

아래 예에서 dtrace는 기본으로 설치되지 않을 수 있음. 
우분투 기준 sudo apt install systemtap-sdt-dev 으로 설치. 
설치했는데 왜 -n 옵션


```bash
// connect()를 통한 외부 연결 횟수 세기
$ dtrace -n 'syscall::connect:entry { @[execname] = count(); }'

// accept()를 통해 들어오는 연결 횟수 세기
$ dtrace -n 'syscall::accept:return { @[execname] = count(); }'

// 이름이 ssh인 프로세스가 connect() 호출 할 때의 사용자 스택 트레이스
$ dtrace -n 'syscall::connect:entry /execname == "ssh"/ { ustack(); }'
 
```


참고: 시스템 성능 분석과 최적화, 브렌든 그래그

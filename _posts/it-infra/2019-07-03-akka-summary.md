---
title: "[Infra] 아카(Akka) 요약 " 
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

# 아카(Akka) 요약

## 정의

Akka는 오픈 소스 툴킷으로, JVM 상의 동시성과 분산 애플리케이션을 단순화하는 런타임이다. 
Akka는 동시성을 위한 여러 프로그래밍 모델을 지원하지만, Erlang으로부터 영향을 받아 actor 기반의 동시성이 두드러진다.
Akka의 주목적은 클라우드에 배포하거나 다중 코어 장치에서 실행할 애플리케이션을 더 쉽게 구축할 수 있게 해주고, 
다중 코어 또는 분산 시스템의 가용 계산 능력을 최대한 효율적으로 활용하는 것이다. 

## 아카의 3요소

### Actor

아카는 액터를 중심으로 한다. 아카가 제공하는 컴포넌트 대부분은 액터를 설정하거나, 액터를 네트워크에 연결하거나, 
액터를 스케줄링하거나, 액터의 클러스터를 만드는 등의 사용 방법을 지원한다.
즉, 액터는 설정과 메시지 브로커(message broker) 설치라는 부가 비용이 들지 않는 메시지 큐(message queue)와 상당히 비슷하다. 
액터는 프로그래밍 가능한 메시지 큐를 아주 작은 크기로 줄인 것과 같다. 
각 액터는 메시지를 받기 전까지는 아무 일도 수행하지 않는다. 
액터는 한번에 하나의 메시지를 받을 수 있으며, 메시지를 받을 떄마다 어떤 동작을 수행한다. 
액터가 다른 액터에게 메시지를 보낼 수도 있다. 
액터가 수행하는 모든 것은  비동기적으로(asynchronously) 실행된다. 

### ActorSystem

액터 모델을 구현하기 위한 클래스 중 하나. 스프링의 applicationContext와 같은 역할.

### ActorRef
Actor를 감싸고 있는 Wrapper라고 생각하면 편함. 실제로 여러 Actor들은 ActorRef 안에서 상호 메시지 교환. 



## receive 메소드

* Actor 클래스 내부에 receive 메소드가 존재함. 
* Actor는 receive를 통해 받은 메세지를 처리함.

## Props 객체

* Props는 actor 인스턴스를 만드는데 필요한 정보를 캡슐화 해놓음.


## akka.actor.ActorSystem

An actor system is a hierarchical group of actors which share common configuration, 
e.g. dispatchers, deployments, remote capabilities and addresses. 
It is also the entry point for creating or looking up actors.

## Actor System

Actors are objects which encapsulate state and behavior, 
they communicate exclusively by exchanging messages which are placed into the recipient’s mailbox. 

참고: https://doc.akka.io/docs/akka/current/general/actor-systems.html
참고: Akka 코딩 공작소

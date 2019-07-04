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

## 아카의 3요소

* Actor: 객체 지향 프로그래밍에서의 객체라고 생각하면 될듯?
* ActorSystem: 액터 모델을 구현하기 위한 클래스 중 하나. 스프링의 applicationContext와 같은 역할.
* ActorRef: Actor를 감싸고 있는 Wrapper라고 생각하면 편함. 실제로 여러 Actor들은 ActorRef 안에서 상호 메시지 교환. 

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


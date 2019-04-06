---
title: "[Java] 자바 스프링(spring) MVC 간단 정리" 
categories:
  - Programming
tags:
  - Programming
  - Java
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 자바 스프링(spring) MVC 간단 정리

참고자료 : 토비의 스프링 3.1 vol2, 3장 스프링 웹 기술과 스피링 MVC

> MVC는 프레젠테이션 계층의 구성요소를 정보를 담은 모델(M), 화면 출력 로직을 담은 뷰(V), 
그리고 제어 로직을 담은 컨트롤러(C)로 분리하고 이 세가지 요소가 서로 협력해서 하나의 
웹 요청을 처리 하고 응답하는 구조.


프레젠테이션 계층이란? 
위키백과에 따른면, 

> 프레젠테이션 계층(presentation layer)는 컴퓨터 네트워크의 OSI 모형 7계층 가운데 
6번째 계층으로, 네트워크의 데이터 번역자로서의 역할을 한다. 이따금 문맥 계층(syntax layer)이라고도 불린다.

MVC 아키텍처는 보통 프론트 컨트롤ㄹ러(front Controller) 패턴과 함께 사용된다. 
프론트 컨트롤러 패턴은 중앙집중형 컨트롤러를 프레젠테이션 계층의 제일 앞에 둬서 
서버로 들어오는 모든 요청을 먼저 받아서 처리하게 만든다. 
스프링이 제공하는 스프링 서블릿/MVC의 핵심은 DispatcherServlet이라는 프론트 컨트롤러다. 
이 DispatcherServlet은 MVC 아키텍처로 구성된 프레젠테이션 계층을 만들 수 있도록 설계되어 있다. 

> 자바 서블릿(Java Servelt)이란 자바를 사용하여 웹페이지를 동적으로 생성하는 서버측 프로그램 혹은 
그 사양을 말하며, 

프론트 컨트롤러의 역할
1. 프론트 컨틀롤러는 클라이언트가 보낸 요청을 받아서 공통적인 작업을 먼저 수행한 후에 
적절한 세부 컨트롤러로 작업을 위임해주고, 클라이언트에게 보낼 뷰를 선택해서 최종결과를 생성하는 등의 작업을 수행한다. 
2. 예외상황 발생 시 이를 처리하는 것도 프론트 컨트롤러의 역할이다. 

서버가 HTTP요청을 받기 시작해서 다시 HTTP로 결과를 응답해주기까지의 과정을 살펴보자.


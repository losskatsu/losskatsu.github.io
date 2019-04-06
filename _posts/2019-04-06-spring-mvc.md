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

(1) DispatcherServlet의 HTTP 요청 접수
자바 서버의 서블릿 컨테이너는 HTTP 프로토콜을 통해 들어오는 요청이 스프링의 DispatcherServelt에 할당된 것이라면 
HTTP 요청정보를 DispatcherServlet에 전달해준다. web.xml에는 보통 아래와 같이 
DispatcherServlet이 전달받을 URL의 패턴이 정의 되어 있다. 

```java
<servelt-mapping>
  <servelt-name>Spring MVC Dispatcher Servlet</servelt-name>
  <url-pattern>/app/*</url-pattern>
</servelt-mapping>
```
이 서블릿-매핑은 URL이 /app로 시작하는 모든 요청을 스프링의 프론트 컨트롤러인 
DispatcherServlet에게 할당해주는 것이다. 

(2) DispatcherServlet에서 컨트롤러로 HTTP 요청 위임
DispatcherServlet은 URL이나 마라미터 정보, HTTP 명령 등을 참고로 해서 
어떤 컨트롤러에게 작업을 위임할지 결정한다. 
어떤 컨트롤러/핸들러가 요청을 처리할지 결정했다면, 다음은 해당 컨트롤러 오브젝트의 
메소드 호출 후 실제로 웹 요청 처리 작업을 위임할 차례다. 
DispatcherServlet은 컨트롤러가 어떤 메소드를 가졌고 어떤 인터페이스를 구현했는지 전혀 알지 못한다. 
대신 컨트롤러의 종류에 따라 적절한 어댑터를 사용한다. 
각 어댑터는 자신이 담당하는 컨트롤러에 맞는 호출 방법을 이용해서컨트롤러에 작업 요청을 보내고 
결과를 돌려받아서 DispatcherServlet에게 다시 돌려주는 기능을 갖고 있다. 
이렇게 하면 DispatcherServlet이 동시에 여러 가지 타입의 컨트롤러를 사용할 수 있다. 
스프링 서블릿/MVC 확장 구조의 기본은 바로 어댑터를 통한 컨트롤러 호출 방식이다. 
어떤 어댑터를 사용할지는 DispatcherServlet 

(3)

(4)

(5)

(6)

(7)

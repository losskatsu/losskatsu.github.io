---
title: "[Infra] 아파치(Apache), 톰캣(Tomcat), 엔진엑스(Nginx) 차이" 
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

# 웹서버 아파치(Apache), 톰캣(Tomcat), 엔진엑스(Nginx) 차이

## 아파치(Apache)

아파치는 여러가지 프로젝트를 통해 오픈소스를 만들어내는 소프트웨어 단체 이름이다. 
따라서 아파치 서버란 이 단체에서 만든 http웹서버를 의미한다. 
즉 아파치 서버는 http요청을 처리할 수 있다. 
클라이언트가 GET, POST, DELETE 같은 메소드를 요청하면 그에 대한 결과값을 돌려준다. 

## 톰캣(Tomcat)

톰캣은 WAS(Web Application Server)이다. 
얼핏생각하면 아파치 서버와 같다고 생각할 수도 있지만, 둘은 목적이 서로 다르다. 
아파치 웹 서버는 정적인 데이터를 처리하는 서버이고, WAS는 동적 데이터를 처리하는 서버이다. 
즉, WAS는 DB와 연결되어 데이터를 주고 받는 것이다. 
웹사이트 주소를 보다보면 html이 아닌 http://~/asdf.jsp 라는 주소를 볼 때가 있는데 
웹 애플리케이션 서버는 이 JSP(Java Server Page)를 처리하는 프로그램이다. 
즉 Java로 만들어진 프로그램을 웹서버에서 돌려서 결과값을 클라이언트로 돌려주는 것이지.

클라이언트 - 웹서버 - WAS - DB

따라서 아파치와 톰캣은 목적이 다르기 때문에 둘을 연동하면 더욱 효과적이다. 


## 엔진엑스(Nginx)

엔진엑스는 아파치와 같은 웹서버이다. 
엔진엑스는 아파치의 단점을 보완하기 위해 만든 프로그램이다. 

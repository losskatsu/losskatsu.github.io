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

**참고링크**   

* [flask, nginx, uwsgi (1)개념](https://losskatsu.github.io/it-infra/flask-nginx-uwsgi-concept/)
* [flask, nginx, uwsgi (2)연동 실습](https://losskatsu.github.io/it-infra/flask-nginx-uwsgi/)  
* [AWS에 아파치 서버 설치하기](https://losskatsu.github.io/it-infra/aws-apache/)
* [아파치 서버 에러 로그 확인](https://losskatsu.github.io/it-infra/apache-error-log/)
* [커버로스 인증 개념](https://losskatsu.github.io/it-infra/kerberos/)
* [아파치, 톰캣, nginx 차이](https://losskatsu.github.io/it-infra/webserver/)
* [SSL, CRS 인증 관련 정리(대칭키, 공개키, 개인키)](https://losskatsu.github.io/it-infra/ssl-auth/)



## 아파치(Apache)

아파치는 여러가지 프로젝트를 통해 오픈소스를 만들어내는 소프트웨어 단체 이름입니다. 
따라서 아파치 서버란 이 단체에서 만든 http웹서버를 의미하는데요. 
즉 아파치 서버는 http요청을 처리할 수 있습니다. 
클라이언트가 GET, POST, DELETE 같은 메소드를 요청하면 그에 대한 결과값을 돌려줍니다. 

## 톰캣(Tomcat)

톰캣은 WAS(Web Application Server)입니다. 
얼핏생각하면 아파치 서버와 같다고 생각할 수도 있지만, 둘은 목적이 서로 다른데요. 
아파치 웹 서버는 정적인 데이터를 처리하는 서버이고, WAS는 동적 데이터를 처리하는 서버입니다. 
즉, WAS는 DB와 연결되어 데이터를 주고 받는 것입니다.. 
웹사이트 주소를 보다보면 html이 아닌 http://~/asdf.jsp 라는 주소를 볼 때가 있는데 
웹 애플리케이션 서버는 이 JSP(Java Server Page)를 처리하는 프로그램입니다. 
즉 Java로 만들어진 프로그램을 웹서버에서 돌려서 결과값을 클라이언트로 돌려줍니다.

클라이언트 - 웹서버 - WAS - DB

따라서 아파치와 톰캣은 목적이 다르기 때문에 둘을 연동하면 더욱 효과적입니다. 


## 엔진엑스(Nginx)

엔진엑스는 아파치와 같은 웹서버입니다. 
엔진엑스는 아파치의 단점을 보완하기 위해 만든 프로그램인데요. 
아파치는 C10K Problem이라고 해서 하나의 웹서버에 10,000개의 클라이언트 접속을 커버할 수 있는 문제를 해결하기 위해 
가벼움과 높은 성능을 추구하며 만들어졌습니다. 
아파치와의 차이점은 아파치는 쓰레드/프로세스 기반 구조이며, 각 요청당 쓰레드 하나가 처리합니다. 
한명의 클라이언트 당 하나의 쓰레드가 할당 되므로 사용자가 많아지면 시스템 자원 낭비가 심해진다는 단점이 있습니다. 
반면 엔진엑스는 비동기 기반 구조라 더 적은 리소스를 사용해서 요청을 처리할 수 있습니다. 

---
title: "[Infra] 리버스 프록시(reverse proxy) 개념" 
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

# 리버스 프록시(reverse proxy) 개념

**참고 링크**

* [flask, nginx, uwsgi (1)개념](https://losskatsu.github.io/it-infra/flask-nginx-uwsgi-concept/)
* [flask, nginx, uwsgi (2)연동 실습](https://losskatsu.github.io/it-infra/flask-nginx-uwsgi/)  
* [AWS에 아파치 서버 설치하기](https://losskatsu.github.io/it-infra/aws-apache/)
* [아파치 서버 에러 로그 확인](https://losskatsu.github.io/it-infra/apache-error-log/)
* [커버로스 인증 개념](https://losskatsu.github.io/it-infra/kerberos/)
* [아파치, 톰캣, nginx 차이](https://losskatsu.github.io/it-infra/webserver/)
* [SSL, CRS 인증 관련 정리(대칭키, 공개키, 개인키)](https://losskatsu.github.io/it-infra/ssl-auth/)


## 1. 프록시(proxy) 서버란?

프록시 서버란 무엇일까요? 
프록시 서버를 구글에 검색하면 이런 뜻이 나옵니다. 

> 프록시 서버(proxy server)는 클라이언트가 자신을 통해서 다른 네트워크 서비스에 간접적으로 접속할 수 있게 해 주는 컴퓨터 시스템이나 응용 프로그램을 가리킨다. 서버와 클라이언트 사이에 중계기로서 대리로 통신을 수행하는 것을 가리켜 '프록시', 그 중계 기능을 하는 것을 프록시 서버라고 부른다. 

프록시 서버는 크게 포워드 프록시 서버(forward proxy server)와 리버스 프록시 서버(reverse proxy server)로 나눠집니다. 

## 2. 포워드 프록시(forward) 서버란?

우리가 흔히 말하는 '프록시 서버'란 포워드 포록시 서버를 의미합니다. 
프록시 서버는 아래 그림처럼 클라이언트 앞에 놓여 있습니다.

<center><img src="/assets/images/infra/reverse_proxy/reverse_proxy01.PNG" width="800"></center>

위 그림을 보면 클라이언트가 인터넷 웹서버에 요청을 보내면 중간에서 그 요청을 프록시 서버가 가로챕니다. 
그리고나서 요청을 받은 프록시 서버는 웹서버에 다시 요청을 보내고 웹서버에게 받은 응답을 다시 클라이언트에게 전달합니다. 

## 3. 리버스 프록시(reverse proxy) 서버란?

리버스 프록시 서버는 아래 그림 처럼 웹서버 앞에 놓여 있습니다. 

<center><img src="/assets/images/infra/reverse_proxy/reverse_proxy02.PNG" width="800"></center>

## 4. 포워드 프록시 vs 리버스 프록시

위 그림만 봐서는 포워드 프록시 서버와 리버스 프록시 서버의 차이점이 거의 없는 것 같습니다. 
하지만 분명 차이가 있습니다. 
포워드 프록시 서버는 클라이언트 앞에 놓여져 있는 반면, 리버스 프록시 서버는 웹서버 앞에 놓여 있습니다. 

포워드 프록시 서버를 사용하면 클라이언트와 직접 통신하는 웹서버가 없다는 것을 알 수 있습니다. 
반면 리버스 프록시 서버를 사용하면 웹서버와 직접 통신하는 클라이언트가 없다는 것을 알 수 있습니다.

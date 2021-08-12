---
title: "[Infra] flask, nginx, uwsgi(1) 개념" 
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

# flask, nginx, uwsgi(1) 개념


**관련 내용 복습하기**   

* [flask, nginx, uwsgi (1)개념](https://losskatsu.github.io/it-infra/flask-nginx-uwsgi-concept/)
* [flask, nginx, uwsgi (2)연동 실습](https://losskatsu.github.io/it-infra/flask-nginx-uwsgi/)  
* [AWS에 아파치 서버 설치하기](https://losskatsu.github.io/it-infra/aws-apache/)
* [아파치 서버 에러 로그 확인](https://losskatsu.github.io/it-infra/apache-error-log/)
* [커버로스 인증 개념](https://losskatsu.github.io/it-infra/kerberos/)
* [아파치, 톰캣, nginx 차이](https://losskatsu.github.io/it-infra/webserver/)
* [SSL, CRS 인증 관련 정리(대칭키, 공개키, 개인키)](https://losskatsu.github.io/it-infra/ssl-auth/)

## 1. 전체 구조

flask, nginx, uwsgi의 전체 구조는 다음과 같습니다. 

<center><img src="/assets/images/infra/flask-concept/flask01.jpg" width="800"></center>

## 2. 사용자와 nginx

우선 사용자는 크롬과 같은 웹 브라저를 통해 웹서버로 HTTP 요청을 합니다. 
그 요청을 받는 웹서버를 nginx라고 가정하겠습니다. (아파치 서버를 사용할 수도 있습니다.)
nginx는 정적페이지를 담당합니다.

## 3. nginx와  uWSGI

nginx는 동적 페이지 요청을 하기 위해 장고 또는 플라스크에게 요청 해야하는데, 
문제는 nginx는 파이썬이라는 언어를 모른다는 것이 문제입니다. 
따라서 nginx는 장고 혹은 플라스크와 이어줄 중계인인 uWSGI에게 요청합니다. 
WSGI는 Web Server Gateway Interfece로 웹서버(nginx)와 웹 애플리케이션(Flask)의 중계 역할을 합니다. 

nginx와 uWSGI는 서로 유닉스 소켓으로 통신합니다. 물론 nginx와 uWSGI는 HTTP통신을 해도 되지만 
둘다 같은 서버내에 있으므로 HTTP 통신보다는 유닉스 소켓(unix socker) 통신을 하는 것이 오버헤드(overhead)가 적어 효율이 좋습니다. 

## 4. uWSGI와 웹애플리케이션(django or flask)

nginx에게 동적 페이지 요청을 받은 uWSGI는 웹 애플리케이션인 django 또는 flask에게 다시 요청합니다.

## 5. 웹 애플리케이션과 DB

웹 애플리케이션인 django 또는 flask가 DB를 봐야할 일이 있다면 DB를 참고해 작업을 수행합니다. 


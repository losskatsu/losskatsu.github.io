---
title: "[Infra] flask, nginx, uwsgi(2) 연동하기" 
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

# flask, nginx, uwsgi 연동하기(실습)

**관련 내용 복습하기**   

* [flask, nginx, uwsgi (1)개념](https://losskatsu.github.io/it-infra/flask-nginx-uwsgi-concept/)
* [flask, nginx, uwsgi (2)연동 실습](https://losskatsu.github.io/it-infra/flask-nginx-uwsgi/)  
* [AWS에 아파치 서버 설치하기](https://losskatsu.github.io/it-infra/aws-apache/)
* [아파치 서버 에러 로그 확인](https://losskatsu.github.io/it-infra/apache-error-log/)
* [커버로스 인증 개념](https://losskatsu.github.io/it-infra/kerberos/)
* [아파치, 톰캣, nginx 차이](https://losskatsu.github.io/it-infra/webserver/)
* [SSL, CRS 인증 관련 정리(대칭키, 공개키, 개인키)](https://losskatsu.github.io/it-infra/ssl-auth/)

이번 포스팅에서는 flask로 만든 웹 서버를 nginx, uwsgi와 연동해 봅니다.

## 1. flask 서버 만들기 

먼저 간단한 플라스크 서버를 만들어보겠습니다. 
플라스크가 설치되어 있는 파이썬 가상환경을 실행합니다. 

```bash
$ pyenv activate py3_8_5
```

```bash
$ cd work/test
```
먼저 work/test 디렉토리를 하나 생성하고 test 디렉토리로 이동합니다.
현재 경로는 /home/user/work/test 입니다. 

디렉토리로 이동했다면 다음과 같이 플라스크 서버를 만듭니다. 
파일 이름은 hello.py로 하겠습니다.

```python
# hello.py
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello World!"

@app.route("/meet")
def meet():
    return "Nice to meet you!"

if __name__ == '__main__':
    app.run(host='0.0.0.0')
```

서버를 만들었다면 실행해 줍니다. 

```bash
(py3_8_5)$ python hello.py
```

위와 같이 실행했을때 다음과 같이 출력된다면 성공입니다.

```bash
(py3_8_5)$ python hello.py
 * Serving Flask app 'hello' (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: off
 * Running on all addresses.
   WARNING: This is a development server. Do not use it in a production deployment.
 * Running on http://(사용자의 IP주소):5000/ (Press CTRL+C to quit)
```

그러면 크롬 브라우저를 열고 접속이 되는지 확인합니다. 
주소창에 http://(사용자의 IP주소):5000를 입력했을때 다음과 같은 화면이 출력되면 성공입니다.

```
Hello World!
```

그리고 이번에는 http://(사용자의 IP주소):5000/meet 에 접속합니다. 
접속했을 때 다음과 같은 화면이 나온다면 성공입니다. 

```
Nice to meet you!
```

이렇게 플라스크 서버를 만들었습니다.


## 2. nginx 설치 및 테스트


먼저 nginx 웹 서버를 설치합니다. 

```
(py3_8_5)$ sudo apt-get install nginx
```

nginx는 설치하면 바로 띄워집니다. 
다음과 같이 프로세스를 확인하면 nginx가 띄워진것을 볼 수 있습니다.

```
(py3_8_5)$ ps -ef | grep nginx
root      199783       1  0 07:37 ?        00:00:00 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
www-data  199784  199783  0 07:37 ?        00:00:00 nginx: worker process
www-data  199785  199783  0 07:37 ?        00:00:00 nginx: worker process
www-data  199786  199783  0 07:37 ?        00:00:00 nginx: worker process
www-data  199787  199783  0 07:37 ?        00:00:00 nginx: worker process
```

사이트 접속이 잘되는지 보겠습니다. 
크롬을 열고 사용자 ip 주소를 썼을 떄 다음과 같은 화면이 나오면 성공입니다. 
이때 주의애햐할 점은 앞서 플라스크 서버는 포트 5000에 접속하라고 직접입력했지만
이번에는 포트는 입력안하고 ip 주소만 입력합니다.(기본적으로 80포트에 접속하게 됩니다.) 

```
Welcome to nginx!

If you see this page, the nginx web server is successfully installed and working. Further configuration is required.

For online documentation and support please refer to nginx.org.
Commercial support is available at nginx.com.

Thank you for using nginx.
```

어쩄든 위와 같은 화면이 나오면 성공입니다. 


## 3. uwsgi 설치

이번에는 uwsgi를 설치합니다. 

```
(py3_8_5)$ pip install uwsgi
```

그리고 다음과 같은 work/test 디렉토리에 uwsgi.py라는 파이썬 파일을 만들어줍니다.

```python 
from hello import app

if __name__ == "__main__":
    app.run(host='0.0.0.0')
```

## 4. ini 파일 작성

uwsgi를 설치했다면 uwsgi 데몬으로 uwsgi 애플리케이션을 사용할 수 있도록 다음과 같은 ini 파일을 작성합니다. 
ini 파일은 다양한 장소에 생성할 수 있지만 저는 맨 처음 만들었던 플라스크 서버가 있는 work/test 디렉토리에 test.ini 라는 이름으로 만들겠습니다.  

**test.ini**

```
[uwsgi]

module = hello
callable = app

socket = /home/user/work/test/test.sock
chmod-socket = 666
vacuum = true

daemonize = /home/user/work/test/uwsgi.log

die-on-term = true
venv = /home/user/.pyenv/versions/3.8.5/envs/py3_8_5
```

위 파일을 보면 가장 마지막 줄에 venv 옵션이 있는데요. 
이것은 파이썬 가상환경을 의미합니다. 
따라서 가상환경에서 flask 개발을 하신분은 자신의 가상환경 위치를 적어줍니다. 
위와 같이 가상환경 경로 설정해주면 서버 가동하기전에 가상환경 안들어가고 전역 파이썬으로 서버 돌릴수 있습니다. 


# 5. nginx 설정 파일 수정

이번에는 nginx 설정 파일을 수정합니다. 
nginx 설정 파일은 /etc/nginx/sites-enabled/default 입니다. 루트 권한으로 열어주세요. 
열어보면 파일이 좀 긴데 주석을 제외하면 다음과 같습니다. 

```bash
(py3_8_5)$ sudo vim /etc/nginx/sites-enabled/default
server {
    listen 80 default_server;
    listen [::]:80 default_server;
    
    root /var/www/html;

    index index.html index.htm index.nginx-debian.html;
    server_name _;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

위 원본을 다음고 같이 바꿔줍니다.

```bash
(py3_8_5)$ sudo vim /etc/nginx/sites-enabled/default
server {
    listen 80 default_server;
    listen [::]:80 default_server;
    
    root /var/www/html;

    index index.html index.htm index.nginx-debian.html;
    server_name _;

    location / {
        try_files $uri @app;
    }

    location @app {
        include uwsgi_params;
        uwsgi_pass unix:/home/user/work/test/test.sock;
    }
}
```

## 6. nginx, uwsgi, 연동 테스트

이제 uwsgi를 이용해 test.ini를 실행해 줍니다. 

```bash
(py3_8_5)~work/test$ uwsgi --ini test.ini
[uWSGI] getting INI configuration from test.ini
```

그리고 다음과 같이 nginx를 재시작합니다.

```bash
(py3_8_5)~work/test$ sudo service nginx restart
```

그리고 나서 다시 크롬 브라우저의 주소창에 자신의 'ip주소'를 입력하고 다음 화면을 보면 성공입니다.

```
Hello World!
```

주의 해야할 점은 ip 주소만 입력해야합니다. (5000번 포트 입력하면 안됨)

위 출력이 잘되면 'ip주소/meet' 경로도 테스트 해 봅니다.

```
Nice to meet you!
```

위와 같은 출력창이 보이면 성공입니다.


## 7. 만약 502 BAD GATEWAY 에러가 난다면?

에러가 날 수도 있습니다. 예를 들어 위 과정을 모두 수행했는데 에러가 날 수도 있습니다. 
그럴때는 다음과 같이 합니다.  

가장 먼저 확인해야할 것은 에러 메시지 입니다. 다음과 같이 확인합시다. 
우선 uwsgi.log 파일을 확인해야합니다. 해당 파일이 있는 곳으로 이동하고 다음과 같이 입력합니다. 

```bash
$ tail -n 40 uwsgi.log
!!!!!!!!!!!!!! WARNING !!!!!!!!!!!!!!
no request plugin is loaded, you will not be able to manage requests.
you may need to install the package for your language of choice, or simply load it with --plugin.
!!!!!!!!!!! END OF WARNING !!!!!!!!!!
spawned uWSGI worker 1 (and the only) (pid: 51023, cores: 1)
-- unavailable modifier requested: 0 --
-- unavailable modifier requested: 0 --
-- unavailable modifier requested: 0 --
-- unavailable modifier requested: 0 --
-- unavailable modifier requested: 0 --
*** Starting uWSGI 2.0.18-debian (64bit) on [Mon Aug 16 05:20:06 2021] ***
compiled with version: 10.0.1 20200405 (experimental) [master revision 0be9efad938:fcb98e4978a:705510a708d3642c9c962beb663c476167e4e8a4] on 11 April 2020 11:15:55
os: Linux-5.4.0-80-generic #90-Ubuntu SMP Fri Jul 9 22:49:44 UTC 2021
nodename: poc-dlinfo-gpu01
machine: x86_64
clock source: unix
pcre jit disabled
detected number of CPU cores: 16
current working directory: /home/dlinfo/work/living_paradise/predict_product_demand
detected binary path: /usr/bin/uwsgi-core
your processes number limit is 514723
your memory page size is 4096 bytes
detected max file descriptor number: 1024
lock engine: pthread robust mutexes
thunder lock: disabled (you can enable it with --thunder-lock)
uwsgi socket 0 bound to UNIX address /home/dlinfo/work/living_paradise/predict_product_demand/main.sock fd 3
your server socket listen backlog is limited to 2000 connections
your mercy for graceful operations on workers is 60 seconds
mapped 187664 bytes (183 KB) for 3 cores
*** Operational MODE: threaded ***
*** no app loaded. going in full dynamic mode ***
*** uWSGI is running in multiple interpreter mode ***
!!!!!!!!!!!!!! WARNING !!!!!!!!!!!!!!
no request plugin is loaded, you will not be able to manage requests.
you may need to install the package for your language of choice, or simply load it with --plugin.
!!!!!!!!!!! END OF WARNING !!!!!!!!!!
spawned uWSGI master process (pid: 71869)
spawned uWSGI worker 1 (pid: 71872, cores: 3)
-- unavailable modifier requested: 0 --
-- unavailable modifier requested: 0 --
```

이런 에러가 난다면 우선 uwsgi-plugin-python3를 설치해야합니다. 

```bash
$ sudo apt-get install uwsgi-plugin-python3
```

위와 같이 설치했다면 이번에는 test.ini 파일을 고쳐줍니다. 

```
[uwsgi]

module = hello
callable = app

socket = /home/user/work/test/test.sock
chmod-socket = 666
vacuum = true

daemonize = /home/user/work/test/uwsgi.log

die-on-term = true
venv = /home/user/.pyenv/versions/3.8.5/envs/py3_8_5

plugins = python3
```

위에서 설치했으니까 ini파일에서 가장 마지막줄에 'plugins = python3'를 추가하는 것입니다.

```bash
$ uwsgi --ini test.ini
[uWSGI] getting INI configuration from test.ini
```

```bash
$ sudo service nginx restart
```

그리고 다시 시작해줍니다. 

---
title: "[Infra] nginx를 활용한 포트포워딩, 리버스 프록시" 
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

# nginx를 활용한 포트포워딩, 리버스 프록시

**관련 내용 복습하기**   

* [flask, nginx, uwsgi (1)개념](https://losskatsu.github.io/it-infra/flask-nginx-uwsgi-concept/)
* [flask, nginx, uwsgi (2)연동 실습](https://losskatsu.github.io/it-infra/flask-nginx-uwsgi/)  
* [AWS에 아파치 서버 설치하기](https://losskatsu.github.io/it-infra/aws-apache/)
* [아파치 서버 에러 로그 확인](https://losskatsu.github.io/it-infra/apache-error-log/)
* [커버로스 인증 개념](https://losskatsu.github.io/it-infra/kerberos/)
* [아파치, 톰캣, nginx 차이](https://losskatsu.github.io/it-infra/webserver/)
* [SSL, CRS 인증 관련 정리(대칭키, 공개키, 개인키)](https://losskatsu.github.io/it-infra/ssl-auth/)
* [리버스 프록시의 개념](https://losskatsu.github.io/it-infra/reverse-proxy/)
* [로드 밸런서의 개념](https://losskatsu.github.io/os-kernel/loadbalancer/)

## 1. nginx 설치

이번 포스팅에서는 nginx를 활용한 포트포워딩, [리버스 프록시](https://losskatsu.github.io/it-infra/reverse-proxy/) 관련 내용을 정리해보겠습니다. 
먼저 nginx를 활용하기 위해 nginx를 설치하겠습니다.  

```bash
ubuntu@k8s-master:~$ sudo apt update

Hit:1 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu jammy InRelease
Get:2 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]
Get:3 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu jammy-backports InRelease [109 kB]
Hit:4 https://download.docker.com/linux/ubuntu jammy InRelease
...(중략)
Fetched 2214 kB in 1s (1682 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
60 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

```bash
ubuntu@k8s-master:~$ sudo apt install nginx

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
...(생략)
```

```bash
ubuntu@k8s-master:~$ sudo systemctl status nginx

● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2023-08-26 03:05:01 UTC; 1min 24s ago
       Docs: man:nginx(8)
    Process: 20184 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
    Process: 20186 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
   Main PID: 20280 (nginx)
      Tasks: 3 (limit: 4667)
```

## 2. 포트포워딩

### 2-1. 수정해야 하는 파일

이번 절에서는 포트포워딩을 해보겠습니다. 

```bash
ubuntu@k8s-master:~$ sudo –i
root@k8s-master:~# cd /etc/nginx/sites-enabled/
root@k8s-master:/etc/nginx/sites-enabled# ls
default
```

포트포워딩을 하기 위해서는 `/etc/nginx/sites-enabled/` 경로에 있는 `default` 파일을 수정해야합니다. 
이를 위해 `/etc/nginx/sites-enabled/` 경로로 이동해서 `default` 파일을 확인합니다. 

```bash
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        # SSL configuration
        #
        # listen 443 ssl default_server;
        # listen [::]:443 ssl default_server;
        #
        # Note: You should disable gzip for SSL traffic.
        # See: https://bugs.debian.org/773332
        #
        # Read up on ssl_ciphers to ensure a secure configuration.
        # See: https://bugs.debian.org/765782
        #
        # Self signed certs generated by the ssl-cert package
        # Don't use them in a production server!
        #
        # include snippets/snakeoil.conf;

        root /var/www/html;

        # Add index.php to the list if you are using PHP
        index index.html index.htm index.nginx-debian.html;

        server_name _;

        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                try_files $uri $uri/ =404;
        }
```

파일을 확인하면 위와 같은데 주석을 뺴고 간단하게 보면 다음과 같습니다. 

```bash
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        root /var/www/html;

        server_name _;

        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                try_files $uri $uri/ =404;
        }
```

### 2-2. 포트포워딩 방법-1

포트포워딩을 해보겠습니다. 80번포트로 들어오는 트래픽을 `http://172.31.46.220:80`로 포트포워딩해보겠습니다. 
이를 위해 위 코드에서 `try_files $uri $uri/ =404;` 부분을 주석 처리하고, `proxy_pass http://172.31.46.220:80;` 구문을 추가하면 다음과 같습니다.  

```bash
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        # SSL configuration
        #
        # listen 443 ssl default_server;
        # listen [::]:443 ssl default_server;
        #
        # Note: You should disable gzip for SSL traffic.
        # See: https://bugs.debian.org/773332
        #
        # Read up on ssl_ciphers to ensure a secure configuration.
        # See: https://bugs.debian.org/765782
        #
        # Self signed certs generated by the ssl-cert package
        # Don't use them in a production server!
        #
        # include snippets/snakeoil.conf;

        root /var/www/html;

        # Add index.php to the list if you are using PHP
        index index.html index.htm index.nginx-debian.html;

        server_name _;

        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                #try_files $uri $uri/ =404;
                proxy_pass http://172.31.46.220:80;
        }
...(중략)
```


### 2-3. 포트포워딩 방법-2

이번에는 upstream을 활용한 방법을 보겠습니다. 

```bash
upstream nginx_ingress_controller{
    server 172.31.46.220:80;
}

server {
        listen 80 default_server;
        listen [::]:80 default_server;

        # SSL configuration
        #
        # listen 443 ssl default_server;
        # listen [::]:443 ssl default_server;
        #
        # Note: You should disable gzip for SSL traffic.
        # See: https://bugs.debian.org/773332
        #
        # Read up on ssl_ciphers to ensure a secure configuration.
        # See: https://bugs.debian.org/765782
        #
        # Self signed certs generated by the ssl-cert package
        # Don't use them in a production server!
        #
        # include snippets/snakeoil.conf;

        root /var/www/html;

        # Add index.php to the list if you are using PHP
        index index.html index.htm index.nginx-debian.html;

        server_name _;

        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                #try_files $uri $uri/ =404;
                proxy_pass http://nginx_ingress_controller;
        }
```

위와 같이 upstream을 활용하는 방법도 있습니다. 
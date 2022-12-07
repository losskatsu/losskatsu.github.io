---
title: "[Django]장고 POST로 MySQL에 데이터 삽입(insert)하기"
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

# 장고 POST로 MySQL에 데이터 삽입(insert)하기

**참고링크**

| 운영체제 | 프론트엔드 | 백엔드 | 데이터베이스| 인프라 |
|:------:|:------:|:------:|:------:|:------:|
|[리눅스구조](https://losskatsu.github.io/os-kernel/os-linux-structure) | [js필터](https://losskatsu.github.io/frontend/js-map-reduce-filter/) | [아파치에러로그](https://losskatsu.github.io/it-infra/apache-error-log/) | [행삭제](https://losskatsu.github.io/it-infra/sqldelete/) | [아파치스쿱](https://losskatsu.github.io/it-infra/sqoop/) |
|[프로세스](https://losskatsu.github.io/os-kernel/os-process/) | [헬로월드](https://losskatsu.github.io/frontend/react-helloworld/) | [웹서버개념](https://losskatsu.github.io/it-infra/webserver/) | [ES기초](https://losskatsu.github.io/it-infra/es-basic/) | [로그분석](https://losskatsu.github.io/it-infra/log-anal/) |
|[네임스페이스](https://losskatsu.github.io/os-kernel/linux-redirection/) |[프로젝트생성](https://losskatsu.github.io/frontend/react-basic-setup/) | [아파치설치](https://losskatsu.github.io/it-infra/aws-apache/) | [MySQL기초](https://losskatsu.github.io/it-infra/mysql-index/) | [beeline](https://losskatsu.github.io/it-infra/beeline/) |
|[디렉토리](https://losskatsu.github.io/os-kernel/linux-directory/) |[헤더생성](https://losskatsu.github.io/frontend/react-category/) | [flask연동](https://losskatsu.github.io/it-infra/flask-nginx-uwsgi/) | [큐브리드](https://losskatsu.github.io/it-infra/cubrid-summary/) | [하둡기초](https://losskatsu.github.io/it-infra/hadoop-basic-concept/) |
|[리다이렉션](https://losskatsu.github.io/os-kernel/linux-redirection/) |[async-get](https://losskatsu.github.io/frontend/react-request-api-django/) | [장고MsSQL연결](https://losskatsu.github.io/it-infra/mssql-django-conn/) | [null공백](https://losskatsu.github.io/it-infra/db-null/) |  [나이파이](https://losskatsu.github.io/it-infra/nifi/) |
|[쓰레드](https://losskatsu.github.io/os-kernel/process-thread/) | [async-post](https://losskatsu.github.io/frontend/react-request-post/) | [장고MySQL연결](https://losskatsu.github.io/it-infra/mysql-django-conn/) | [MySQL설치(win)](https://losskatsu.github.io/it-infra/mysql-install-win/) | [백본](https://losskatsu.github.io/it-infra/backbone/) |
|[라즈베리파이설치](https://losskatsu.github.io/os-kernel/raspberry-vminstall/) | [로그인페이지](https://losskatsu.github.io/frontend/react-request-post/) | [장고inpectdb](https://losskatsu.github.io/it-infra/django-inspectdb/) | [MySQL테이블생성](https://losskatsu.github.io/it-infra/mysql-create-db/) | [제플린](https://losskatsu.github.io/it-infra/backbone/) |
|[OSI7계층소개](https://losskatsu.github.io/os-kernel/network-basic01/) | | [장고read](https://losskatsu.github.io/it-infra/django-read-data/)  |  | [SSL인증](https://losskatsu.github.io/it-infra/ssl-auth/)|
|[OSI1계층](https://losskatsu.github.io/os-kernel/network-basic02/) | | [장고insert](https://losskatsu.github.io/it-infra/django-post-data/)  | | [커버로스](https://losskatsu.github.io/it-infra/kerberos/) |
|[OSI2계층](https://losskatsu.github.io/os-kernel/network-basic03/) | | [장고put](https://losskatsu.github.io/it-infra/django-put-data/)  | | [도커개념](https://losskatsu.github.io/it-infra/docker00/) |
|[OSI3계층](https://losskatsu.github.io/os-kernel/network-basic04/) | | [장고del](https://losskatsu.github.io/it-infra/django-del-data/) | | [도커설치](https://losskatsu.github.io/it-infra/docker01/) |
|[OSI4계층](https://losskatsu.github.io/os-kernel/network-basic05/) | | [flask한글요청](https://losskatsu.github.io/programming/py-flask-korean/) | |[도커기초](https://losskatsu.github.io/it-infra/docker02/)|
|[OSI5,6,7계층](https://losskatsu.github.io/os-kernel/network-basic05/) | |  | | [도커이미지](https://losskatsu.github.io/it-infra/docker03/) |
|[DNS서버](https://losskatsu.github.io/os-kernel/etc-host-dns/) | |  | | [컨테이너네트워크](https://losskatsu.github.io/it-infra/docker04/) |
|[DHCP](https://losskatsu.github.io/os-kernel/dhcp/) | | | | [도커API](https://losskatsu.github.io/it-infra/docker05/) |
|[bashrc](https://losskatsu.github.io/os-kernel/bashrc/) | | | | [도커컴포즈](https://losskatsu.github.io/it-infra/docker06/) |
|[bash](https://losskatsu.github.io/os-kernel/bash/) | | | | [도커볼륨](https://losskatsu.github.io/it-infra/docker07/) |
|[ifconfig](https://losskatsu.github.io/os-kernel/ifconfig/) | | | | [장고이미지](https://losskatsu.github.io/it-infra/docker08/) |
|[소켓프로그래밍](https://losskatsu.github.io/os-kernel/network-socket/) | | | | [도커postgre](https://losskatsu.github.io/it-infra/docker09/) |
|[리눅스유저생성](https://losskatsu.github.io/os-kernel/linux-create-user/) | | | | [도커이미지삭제](https://losskatsu.github.io/it-infra/docker10/)|
|[netstat포트열기](https://losskatsu.github.io/os-kernel/port-open/) | | | |[도커Redis](https://losskatsu.github.io/it-infra/docker11/) |
|[컴파일러](https://losskatsu.github.io/os-kernel/compiler-interpreter/) | | | |[k8s구조](https://losskatsu.github.io/it-infra/kubernetes01/) |
|[운영체제vs커널](https://losskatsu.github.io/os-kernel/diff-kernel-os/) | | | | [k8s설치](https://losskatsu.github.io/it-infra/kubernetes02/) |
|[작업스케쥴링](https://losskatsu.github.io/os-kernel/crontab/) | | | |[k8s서비스배포](https://losskatsu.github.io/it-infra/kubernetes03/) |
|[디스크추가](https://losskatsu.github.io/os-kernel/add-harddisk/) | | | |[POD네트워크](https://losskatsu.github.io/it-infra/kubernetes04/) |
|[aws유저추가](https://losskatsu.github.io/os-kernel/aws-add-user/) | | | | [퍼시스턴트볼륨](https://losskatsu.github.io/it-infra/kubernetes05/)|
|[기초명령어](https://losskatsu.github.io/it-infra/ps-grep-pipe-redirect/) | | | | [k8s에러](https://losskatsu.github.io/it-infra/kubernetes06/)|
|[포트번호](https://losskatsu.github.io/it-infra/port/) | | | | |

## 참고 링크  

### DB

* [MySQL 윈도우에 설치하기](https://losskatsu.github.io/it-infra/mysql-install-win/)
* [MySQL 간단 정리, 우분투, 맥에 설치 하기](https://losskatsu.github.io/it-infra/mysql-index/)
* [맥 OS에 MySQL 설치](https://losskatsu.github.io/it-infra/mysql-install-mac/)
* [파이썬, MySQL 연동](https://losskatsu.github.io/programming/py-db-conn/)
* [데이터베이스에서 널(null)과 공백의 차이](https://losskatsu.github.io/it-infra/db-null/)

### 백엔드  

* [(1-1)MySQL에 데이터베이스, 테이블 생성하기](https://losskatsu.github.io/it-infra/mysql-create-db/)
* [(1-2)장고, MsSQL 연결하기](https://losskatsu.github.io/it-infra/mssql-django-conn/)
* [(1-2)장고, MySQL 연결하기](https://losskatsu.github.io/it-infra/mysql-django-conn/)
* [(1-3)장고 inpectdb로 DB 데이터 model.py로 만들기](https://losskatsu.github.io/it-infra/django-inspectdb/)
* [(1-4)장고로 MySQL에 있는 데이터 웹상에서 보여주기(SELECT)](https://losskatsu.github.io/it-infra/django-read-data/)
* [(1-5)장고로 MySQL에 데이터 삽입 하기(POST)](https://losskatsu.github.io/it-infra/django-post-data/)
* [(1-6)장고로 MySQL에 데이터 수정(put) 하기](https://losskatsu.github.io/it-infra/django-put-data/)

### 프론트엔드  

* [(2-1)기본 리액트 프로젝트 생성](https://losskatsu.github.io/frontend/react-basic-setup/)
* [(2-2)리액트 카테고리 레이어 헤더 만들기](https://losskatsu.github.io/frontend/react-category/)
* [(2-3)장고 API 서버에 요청해서 자료 받아오기(GET)](https://losskatsu.github.io/frontend/react-request-api-django/)
* [(2-4)장고 API 서버에 요청해서 자료 받아오기(GET)](https://losskatsu.github.io/frontend/react-request-post/)



## 1. 실습 준비

본 예제는 맥OS 환경에서 실행했습니다.
실습 준비는 [이전 포스팅](https://losskatsu.github.io/it-infra/django-read-data/)을 참고해주세요. 

이번 실습에서는 POST 방식을 이용해 장고에서 MySQL로 데이터를 insert 해보겠습니다. 


## 2. json 파일 보내서 DB insert 하기

### 2.1. test01/view.py 파일 수정

먼저 test01/view.py를 수정해보겠습니다. 

```python
from rest_framework import status

@api_view(['POST'])
def postMember(request):
    reqData = request.data
    serializer = TestDataSerializer(data=reqData)
    if serializer.is_valid():
        serializer.save()
        return Response(serializer.data, status=status.HTTP_201_CREATED)
    return Response(serializer.errors, status=status.HTTP_400_BAD_REQUEST)
```

```GET```메소드를 쓸때와는 다르게 ```POST```메소드를 사용할 때는 
```status```모듈을 ```import```해줍니다. 
위 코드처럼 ```request.data```가 우리가 삽입할 데이터가 되며, 이는 json형식입니다. 
이후 테스트를할 때 json 형식의 데이터를 전달하게 되는데 이 json데이터가 ```request.data```가 되는 것입니다. 
그리고 ```.save()```메소드를 사용하면 해당 데이터베이스 테이블에 저장할 수 있습니다. 

<center><img src="/assets/images/infra/django-post-data/django-post-data01.png" width="800"></center>

### 2.3. test01/urls.py 파일 수정 

이번에는 ```test01/urls.py```파일을 수정하겠습니다. 

```python
    path('postMember/', views.postMember, name="postMember"),
```

위 코드에 나와있는 ```postMember/```경로로 json 데이터를 던지면 데이터베이슬 insert해줍니다.

<center><img src="/assets/images/infra/django-post-data/django-post-data02.png" width="800"></center>

### 2.4. 서버 가동

그럼 POST가 잘되는지 테스트하기 위 서버를 올려보겠습니다. 
먼저 아래 코드처럼 migrate를 해주고...

```python
$ python manage.py makemigrations

No changes detected

$ python manage.py migrate       

Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions, test01
Running migrations:
  No migrations to apply
```

그리고나서 서버를 올려줍니다. 

```python
 python manage.py runserver     
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
June 03, 2022 - 06:50:12
Django version 4.0.2, using settings 'dbcontest.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.

```

### 2-5. POST 해보기

그리고나서 웹 브라우저를 열고 주소창에 ```http://127.0.0.1:8000/test/postMember/```를 입력하면 다음과 같이 
POST 할수있는 창이 뜹니다. 

<center><img src="/assets/images/infra/django-post-data/django-post-data03.png" width="800"></center>

빈칸에 내가 데이터베이스 테이블에 삽입하고 싶은 데이터를 json형식으로 아래와 같이 입력합니다. 

<center><img src="/assets/images/infra/django-post-data/django-post-data04.png" width="800"></center>

입력했으면 POST 버튼을 눌러줍니다. 

<center><img src="/assets/images/infra/django-post-data/django-post-data05.png" width="800"></center>

POST 요청이 잘 먹힌 것을 볼 수 있습니다. 
그러면 실제로 데이터베이스에 테이블이 있는지 확인해보겠습니다. 
[MySQL 워크벤치](https://losskatsu.github.io/it-infra/mysql-create-db/)를 실행해 확인해봅니다. 

<center><img src="/assets/images/infra/django-post-data/django-post-data06.png" width="800"></center>

원래는 위와 같은 테이블이었는데, 

<center><img src="/assets/images/infra/django-post-data/django-post-data07.png" width="800"></center>

포스트 요청을 하고난 후에는 위와 같이 데이터가 추가된 것을 볼 수 있습니다. 


## 3. json 보내서 해당 조건에 맞는 데이터 긁어오기(select)



### 3.1. 가지고올 데이터베이스 테이블 예제

이번 실습은 json을 전달해서 해당 조건에 맞는 데이터를 긁어오는 실습을 해보겠습니다. 
참고로 이번 실습에 쓰일 DB는 지금까지 사용한 DB와는 다른 DB입니다. 

<center><img src="/assets/images/infra/django-post-data/django-post-data08.png" width="800"></center>

위와 같은 테이블에서 ```pt_code```와 ```std_dt``` 컬럼명에 맞는 데이터를 긁어와 보겠습니다. 

### 3.2. test01/view.py 파일 수정

POST 형식으로 JSON보내서 데이터 가져오려면 다음과 같이 ```views.py```파일을 작성해야 합니다.

```python
from rest_framework.response import Response
from rest_framework.decorators import api_view
from .models import SaleForecast
from .serializers import SaleForecastSerializer

@api_view(['POST'])
def getPredData(request):
  reqData = request.data
  ptcode = reqData['pt_code']
  stddt = reqData['std_dt']
  datas = SaleForecast.objects.filter(pt_code=ptcode, std_dt=stddt)
  serializer = SaleForecastSerializer(datas, many=True)
  return Response(serializer.data)
```

위 코드를 보면 ```POST```형식으로 요청을 받는 것을 알 수 있고, 
클라이언트로부터 받은 json 데이터는 request에 해당하는데, 
```request.data```를 입력하면 json형식으로 정리할 수 있습니다. 
그리고 request받은 데이터에서 ```pt_code```에 해당하는 값을 ```ptcode```라고 저장하고 
```std_dt```에 해당하는 값을 ```stddt```라고 저장합니다. 
그리고 해당 ```ptcode```와 ```stddt```에 맞는 데이터를 가지고 오기 위해 
```filter``` 메소드를 이용해 가져오고 serialize 시켜줍니다. 

<center><img src="/assets/images/infra/django-post-data/django-post-data09.png" width="800"></center>


### 3.3. test01/urls.py 파일 수정

요청을 보내기 위해 적당한 주소를 설정해줍니다. 

```python
path('pred/', views.getPredData, name="pred"),
```


### 3.4. 서버 가동

```python
$ python manage.py makemigrations

Migrations for 'test01':
  test01\migrations\0001_initial.py
    - Create model SaleForecast

$ python manage.py migrate        
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions, test01
Running migrations:
  Applying test01.0001_initial... OK
```


```python
$ python manage.py runserver

Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
June 07, 2022 - 11:22:48
Django version 4.0.4, using settings 'dbcontest.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
```

### 3.5. POST 형식으로 데이터 가져오는 예(1)

웹 브라우저를 열고 ```http://127.0.0.1:8000/lipaco/pred/```를 입력하면 다음과 같은 화면이 나타납니다.

<center><img src="/assets/images/infra/django-post-data/django-post-data10.png" width="800"></center>

POST 형식으로 보내기 위해 위와 같이 데이터를 보내면 다음과 같이 요청값을 받을 수 있습니다.

<center><img src="/assets/images/infra/django-post-data/django-post-data11.png" width="800"></center>



## 4. POST 형식으로 데이터 가져오기(2)

### 4.1. dbcontest/test01/views.py 파일 수정

다음 코드는 json파일로 name과 email을 보내면 해당 조건에 맞는 자료를 디비 테이블에서 가져오는 코드입니다. 

```python
@api_view(['POST'])
def getMembers(request):
    reqData = request.data
    name = reqData['name']
    email = reqData['email']
    print("name is : ", name)
    print("email is : ", email)
    data = Test01.objects.filter(name=name, email=email)
    serializer = TestDataSerializer(data, many=True)
    print(serializer.data)
    return Response(serializer.data)
```

<center><img src="/assets/images/infra/django-post-data/django-post-data12.png" width="800"></center>


### 4.2. dbcontest/test01/urls.py 파일 수정 

그리고 해당 요청을 받기 위한 url을 설정해줍니다. 

```python
from django.urls import path
from . import views

urlpatterns = [
    path('test01datas/', views.getTestDatas, name="test01datas"),
    path('test01data/<str:name>', views.getTestData, name="test01data"),
    path('postMember/', views.postMember, name="postMember"),
    path('putMember/<str:pk>', views.putMember, name="putMember"),
    path('delMember/<str:pk>', views.delMember, name="delMember"),
    path('getMembers/', views.getMembers, name="getMembers"),
]
```

<center><img src="/assets/images/infra/django-post-data/django-post-data12.png" width="800"></center>


### 4.3. 서버 가동

```python
$ python manage.py runserver

Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
June 18, 2022 - 01:57:54
Django version 4.0.2, using settings 'dbcontest.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

### 4.4. 실제로 요청해보기 

웹 브라우저를 열고 다음 url에 접속합니다. 

'http://127.0.0.1:8000/test/getMembers/'

그리고 다음과 같이 요청을 보내보겠습니다. 

<center><img src="/assets/images/infra/django-post-data/django-post-data13.png" width="800"></center>


그리고 POST 버튼을 누르면 다음과 같이 결과를 얻을 수 있습니다. 

<center><img src="/assets/images/infra/django-post-data/django-post-data13.png" width="800"></center>


---
title: "[Django] 장고로 MySQL에 있는 데이터 웹상에서 보여주기"
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

# 장고로 MySQL에 있는 데이터 웹상에서 보여주기

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
* [(1-4)장고로 MySQL에 있는 데이터 웹상에서 보여주기](https://losskatsu.github.io/it-infra/django-read-data/)
* [(1-5)장고로 MySQL에 데이터 insert 하기](https://losskatsu.github.io/it-infra/django-post-data/)
* [(1-6)장고로 MySQL에 데이터 수정(put) 하기](https://losskatsu.github.io/it-infra/django-put-data/)

### 프론트엔드  

* [(2-1)기본 리액트 프로젝트 생성](https://losskatsu.github.io/frontend/react-basic-setup/)
* [(2-2)리액트 카테고리 레이어 헤더 만들기](https://losskatsu.github.io/frontend/react-category/)
* [(2-3)장고 API 서버에 요청해서 자료 받아오기(GET)](https://losskatsu.github.io/frontend/react-request-api-django/)
* [(2-4)장고 API 서버에 요청해서 자료 받아오기(GET)](https://losskatsu.github.io/frontend/react-request-post/)



## 1. 실습 준비

### 1.1. rest_framework 설치

본 예제는 맥OS 환경에서 실행했습니다.

이번 실습에서는 장고의 API 기능을 사용할 것이므로 다음과 같이 ```djangorestframework```을 설치해줍니다. 

```bash
$ pip install djangorestframework
```

### 1.2. 테스트 프로젝트 생성

이번 실습을 위해 간단한 App을 생성해보겠습니다. 

```bash
$ python manage.py startapp test01
```

### 1.3. settings.py 수정 

이제 ```test01```이라느 앱을 생성했고, 앞서 ```djangorestframework```도 설치했으니 다음고 같이 
```settings.py```파일에 ```INSTALLED_APPS```부분에 추가해줍니다. 

```bash
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    'test01',
    'rest_framework',
]
```

<center><img src="/assets/images/infra/django-read-data/django-read-data01.png" width="800"></center>


### 1.4. models.py 위치 이동

[앞선 포스팅](https://losskatsu.github.io/it-infra/django-inspectdb/)에서 
만들어 최상위 폴더에 두었던 models.py를 ```test01/models.py```로 이동시킵니다. 
당연히 기존에 존재하던 ```test01/models.py```는 삭제됩니다. 

## 2. 특정 테이블의 데이터 모두 읽어들이기

### 2.1. test01/serializers.py 파일 생성

```test01``` 앱 내부에 ```serializer.py``` 파일을 생성하고 다음고 같이 코드를 작성해줍니다. 
이때 serializers란 데이터 직렬화를 의미하는데, 
쉽게 말하면 DB에서 불러온 데이터를 json으로 보여주기 위해 가공하는 기능을 한다고 보면 됩니다. 

```bash
from rest_framework.serializers import ModelSerializer
from .models import Test01

class TestDataSerializer(ModelSerializer):
    class Meta:
        model = Test01
        fields = '__all__'
```

위 코드에서 두번쨰 줄을 보면 ```.models```는 현재 폴더(test01) 내부에 있는 ```models.py```를 의미합니다. 
그리고 ```Test01```은 ```models.py```에 존재하는 테이블 클래스 의미합니다. 

<center><img src="/assets/images/infra/django-read-data/django-read-data02.png" width="800"></center>



### 2.2. test01/views.py 파일 수정

이제 화면단을 만들어보겠습니다. 
```test01``` 디렉토리 내에 있는 ```views.py```을 다음과 같이 수정합니다. 

```python
from rest_framework.response import Response
from rest_framework.decorators import api_view
from .models import Test01
from .serializers import TestDataSerializer


@api_view(['GET'])
def getTestDatas(request):
    datas = Test01.objects.all()
    serializer = TestDataSerializer(datas, many=True)
    return Response(serializer.data)
```

위 코드를 보면 네번째 줄에서 앞서만든 ```serializers```를 불러오는 것을 볼 수 있습니다. 
```@api_view```는 데코레이션으 의미하며 get 메소드를 사용하는 것을 볼 수 있습니다. 
```Test01.objects.all()```은 Test01 테이블에 있는 데이터를 모두 읽어들이겠다는 의미입니다. 
이렇게 데이터르 읽어오고 ```serializer```를 이용해 데이터 직렬화를 통해 마지막으로 
```Response```를 이용해 결과를 보여줍니다. 

<center><img src="/assets/images/infra/django-read-data/django-read-data03.png" width="800"></center>


### 2.3. test01/urls.py 파일 만들기

지금까지 필요한 model과 view를 만들었으니 라우팅을 설정해주겠습니다. 
```test01``` 디렉토리에 ```urls.py```파일을 생성하고 다음과 같이 작성해줍니다. 

```python
from django.urls import path
from . import views

urlpatterns = [
    path('test01datas/', views.getTestDatas, name="test01datas"),
]
```

위 코드에서 ```views.getTestDatas```는 앞서 제가 만든 함수입니다. 


<center><img src="/assets/images/infra/django-read-data/django-read-data04.png" width="800"></center>


### 2.4. urls.py 파일 수정

이번에는 상위폴더에 있는 urls.py를 다음과 같이 수정해보겠습니다.

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('test/', include('test01.urls')),
]
```

위 코드에서 주의해야하 점은 두번째 줄에 ```import include```를 반드시 포함시켜야한다는 점입니다. 
그리고 path에서 앞서 생성한 ```test01.urls```를 추가해줍니다.


<center><img src="/assets/images/infra/django-read-data/django-read-data05.png" width="800"></center>



### 2.5. 실행!

이제 모든 준비가 끝났습니다. 먼저 ```makemigrations```을 해주고...

```bash
$ python manage.py makemigrations

Migrations for 'test01':
  test01/migrations/0001_initial.py
    - Create model AuthGroup
    - Create model AuthGroupPermissions
    - Create model AuthPermission
    - Create model AuthUser
(..생략)
```

다음으로 ```migrate```를 해줍니다. 

```bash
$ python manage.py migrate       

Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions, test01
Running migrations:
  Applying test01.0001_initial... OK
```

그리고 서버를 실행하고

```bash
$ python manage.py runserver     

Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
June 02, 2022 - 05:26:39
Django version 4.0.2, using settings 'dbcontest.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

웹 브라우저로 가서 주소창에 ```http://127.0.0.1:8000/test/test01datas/```를 입력하면

<center><img src="/assets/images/infra/django-read-data/django-read-data06.png" width="800"></center>

위와 같이 test01 테이블에 존재하는 데이터를 읽어오는 것을 볼 수 있습니다.


## 3. 특정 조건의 데이터만 읽어들이기


앞선 실습에서는 특정 테이블의 데이터를 모두 가지고 오는 경우를 보았습니다. 
그렇다면 이번에는 특정 조건을 만족하는 데이터만 골라서 가지고 오는 경우를 보겠습니다. 

### 3.1. test01/views.py 파일 수정 

먼저 ```test01/views.py```에 다음과 같은 함수를 추가해줍니다.

```python
@api_view(['GET'])
def getTestData(request, name):
    data = Test01.objects.get(name=name)
    serializer = TestDataSerializer(data, many=False)
    return Response(serializer.data)
```

위 함수에서 앞선 실습과 다른 부분은 우선 함수의 입력값부터 request 뿐만 아니라 name도 받습니다. 
이 ```name```은 자신이 원하는 변수 이름으로 설정할 수 있습니다. 
그리고 ```Test01.objects.all```이 아닌 ```Test01.objects.get```을 사용한다는 것입니다. 
```name=name```에서 앞의 ```name```은 test01 테이블의 ```name``` 컬럼을 의미하는 것이며 
뒤의 ```name```은 우리가 요청 값으로 전달하는 name입니다. 
즉, 우리는 test01 테이블에서 ```name```필드값이 ```name```인 데이터를 가지고 오겠다는 것입니다. 
그리고 serializer에서 우리는 하나의 레코드만 가지고 올 것이믈 ```many=False```를 설정해줍니다.

<center><img src="/assets/images/infra/django-read-data/django-read-data07.png" width="800"></center>

### 3.2. test01/urls.py 파일 수정 

다음을 url을 설정합니다. ```test01/urls.py```파일에 다음과 같이 추가해줍니다. 

```python
path('test01data/<str:name>', views.getTestData, name="test01data"),
```

위 코드처럼 ```urls.py```파일에서 꺽쇠를 사용하면 해당 부분으 변수로 받겠다는 의미입니다. 그리고
```<str:name>```은 우리가 전달할 ```name```을 의미합니다. 
참고로 우리가 보내 ```name```은 문자열이므로 ```str```을 써야 작동하지 만약 ```<int:name>```이라고 작성하면 작동안합니다. 

<center><img src="/assets/images/infra/django-read-data/django-read-data08.png" width="800"></center>


### 3.3. 결과 확인

잘되는지 한번확인해보겠니다. 다음과같이 먼저 migrate를 해줍니다. 
변동사항은 없지만 습관처러 하는게 좋습니다. 

```python
$ python manage.py makemigrations

No changes detected
```
```python
$ python manage.py migrate

Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions, test01
Running migrations:
  No migrations to apply.
```

그리고 서버를 올립니다.

```python
$ python manage.py runserver

Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
June 03, 2022 - 03:50:47
Django version 4.0.2, using settings 'dbcontest.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

브라우저 주소창에 ```http://127.0.0.1:8000/test/test01data/cheolwon```라고 입력해줍니다. 
이는 test01 테이블의 ```name```컬럼값이 ```cheolwon```인 데이터를 가져 오라는 말입니다.

<center><img src="/assets/images/infra/django-read-data/django-read-data09.png" width="800"></center>

결과르 보면 제대로 불러오는 것을 볼 수 있습니다. 







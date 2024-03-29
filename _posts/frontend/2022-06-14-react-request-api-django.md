---
title: "[리액트react] async 리액트에서 장고 API 요청해서 자료 받아오기(GET) " 
categories:
  - frontend
tags:
  - frontend
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---


# 리액트(react) async 장고 API 서버에 요청해서 자료 받아오기(GET)

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

## 1. 사전 준비 사항

지금부터 만들 앱은 파이썬 장고(django)에 연동할 프론트를 리액트로 만드는 실습입니다.
본 포스팅은 [이전 포스팅](https://losskatsu.github.io/frontend/react-basic-setup/)에서 이어지는 포스팅 입니다.

이번 실습에서 ```axios```를 사용하기 위해 ```axios```를 설치해주겠습니다. 
```axios```를 활용하면 GET, PUT, POST, DELETE와 같은 API 요청이 가능합니다. 

```bash
$ cd myapp01
$ npm add axios

added 2 packages, and audited 1438 packages in 3s

191 packages are looking for funding
  run `npm fund` for details

6 high severity vulnerabilities

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.
```

## 2. 장고 API 서버 가동

인텔리제이를 실행하고 이전 포스팅에서 만들었던 장고 API(dbcontest 프로젝트)를 가동시킵니다. 

```bash
dbcontest$  python manage.py runserver

Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
June 14, 2022 - 09:42:58
Django version 4.0.2, using settings 'dbcontest.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

실제 개발 화면은 다음과 같습니다.   

<center><img src="/assets/images/frontend/react/react-request-django/react-request-django01.png" width="800"></center>


그리고 웹 브라우저를 열고 다음 url로 접근해봅니다.  

'http://127.0.0.1:8000/test/test01data/Cheolwon' 


그러면 다음 화면이 나옵니다.  

<center><img src="/assets/images/frontend/react/react-request-django/react-request-django02.png" width="800"></center>


따라서 지금부터는 위 스크린샷에 나오는 자료를 리액트로 요청해서 받아서 처리해보겠습니다. 
실습을 하는 동안 장고 서버는 내리지 말아주세요. 
우리가 받아와야 실습을 하는 동안 장고 서버는 내리지 말아주세요. 

```python
{
    "id": 1,
    "name": "Cheolwon",
    "email": "abcd@email.com",
    "created_at": "2022-05-30T20:25:49Z",
    "updated_at": null
}
```  


## 3. src/pages/Find.js 파일 수정 

기존에는 다음과 같았던 ```src/pages/Find.js``` 파일을....

```react
const Find = () => {
  return(
    <div>
      <h1>친구찾기</h1>
      <p>보고싶은 친구를 찾아보아요</p>
    </div>
  );
};

export default Find;
```

<center><img src="/assets/images/frontend/react/react-request-django/react-request-django03.png" width="800"></center>

다음과 같이 수정하겠습니다.

```react
import React, {useState} from 'react';
import axios from 'axios';

const Find = () => {
  const [data, setData] = useState(null);
  const onClick = async () => {
    try{
      const response = await axios.get(
        'http://127.0.0.1:8000/test/test01data/Cheolwon',
      );
      setData(response.data);
    } catch (e) {
      console.log(e)
    }
  };

  return(
    <div>
      <h1>친구찾기</h1>
      <p>보고싶은 친구를 찾아보아요</p>
      <button onClick={onClick}>불러오기</button>
      {data && <textarea rows={15} value={JSON.stringify(data, null, 2)} readOnly={true}/>}
    </div>
  );
};

export default Find;
```

그리고나서 리액트를 실행하고 버튼을 눌러보면 다음과 같은 접근 권한 에러가 나는 것을 알 수 있습니다.


<center><img src="/assets/images/frontend/react/react-request-django/react-request-django04.png" width="800"></center>



## 4. 장고 접근 권한 해결 

### 4.1. django-cors-headers 설치

장고에서 리액트 요청을 받을 수 있도록 장고 프로젝트를 수정해보겠습니다. 
먼저 장고를 프로젝트를 열고 다음을 설치합니다. 

```bash
$ pip install django-cors-headers
```

그리고 ```dbcontest/settings.py``` 파일을 다음과 같이 수정합니다. 


### 4.2. dbcontest/settings.py 수정

 ```dbcontest/settings.py``` 파일에서 ```INSTALLED_APPS```에서 ```'corsheaders',```를 추가합니다. 
 
 ```python
 INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    'test01',
    'rest_framework',
    'corsheaders',
]
```

<center><img src="/assets/images/frontend/react/react-request-django/react-request-django05.png" width="800"></center>



그리고 ```MIDDLEWARE```에 다음 두줄을 추가합니다.

```python
'corsheaders.middleware.CorsMiddleware',
'django.middleware.common.CommonMiddleware',
```

그러면 ```MIDDLEWARE```은 다음과 같이 됩니다. 미들웨어에 추가할 때는 
corsheaders는 가급적 위에 있어야 합니다. 

```python
MIDDLEWARE = [
    'corsheaders.middleware.CorsMiddleware',
    'django.middleware.common.CommonMiddleware',

    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]
```

<center><img src="/assets/images/frontend/react/react-request-django/react-request-django06.png" width="800"></center>


그리고 특정 클라이언트로부터 요청을 받을 수 있게 ```CORS_ALLOWED_ORIGINS```을 작성합니다. 
```CORS_ALLOWED_ORIGINS```는 원래는 없으므로 파일 가장 하단에 다음과 같이 만들어줍니다. 

```python
CORS_ALLOWED_ORIGINS = [
    "http://localhost:3000",
    "http://127.0.0.1:3000"
]
```

<center><img src="/assets/images/frontend/react/react-request-django/react-request-django07.png" width="800"></center>

참고로 만약 모든 클라이언트로부터 접근을 허용하고 싶다면 다음 코드를 추가합니다.

```python
CORS_ALLOW_ALL_ORIGINS = True
```


## 5. 다시 리액트로 확인 

다시 웹 브라우저에서 다음 리액트 앱에 접근합니다.

'http://localhost:3000/find'

그리고 불러오기를 누르면 다음과 같은 화면이 출력됩니다. 

<center><img src="/assets/images/frontend/react/react-request-django/react-request-django08.png" width="800"></center>


## 6. 좀 더 예쁘게 가져오기 

이전에는 텍스트 영역에 json 내용을 통째로 넣었는데 이번에는 좀 더 예쁘게 넣어보겠습니다. 


```src/pages/Find.js``` 파일을 다음과 같이 수정합니다. 

```react
import React, {useState} from 'react';
import axios from 'axios';

const Find = () => {
  const [data, setData] = useState(null);
  const onClick = async () => {
    try{
      const response = await axios.get(
        'http://127.0.0.1:8000/test/test01data/Cheolwon',
      );
      setData(response.data);
    } catch (e) {
      console.log(e)
    }
  };

  return(
    <div>
      <h1>친구찾기</h1>
      <p>보고싶은 친구를 찾아보아요</p>
      <button onClick={onClick}>불러오기</button>
      {data && <textarea rows={15} value={JSON.stringify(data, null, 2)} readOnly={true}/>}
      <br /><br /><br />

      <button onClick={onClick}>예쁘게 불러오기</button>
      <br /><br />
      {data && <li>{JSON.stringify(data, ['id', 'name', 'email'], 2)}</li>}
      {data && <li>{JSON.stringify(data, ['id'], 2)}</li>}
      {data && <li>{JSON.stringify(data, ['name'], 2)}</li>}
      {data && <li>{JSON.stringify(data, ['email'], 2)}</li>}
      {data && <li>id: {data.id}</li>}
      {data && <li>name: {data.name}</li>}
      {data && <li>email: {data.email}</li>}
    </div>
  );
};

export default Find;
```

이는 화면으로 보면 다음과 같습니다. 

<center><img src="/assets/images/frontend/react/react-request-django/react-request-django09.png" width="800"></center>

그리고 웹 브라우저에서 '예쁘게 불러오기'를 클릭하면 다음과 같습니다. 

<center><img src="/assets/images/frontend/react/react-request-django/react-request-django10.png" width="800"></center>

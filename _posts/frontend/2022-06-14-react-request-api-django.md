---
title: "[리액트react] async 리액트에서 장고 API 서버에 요청해서 자료 받아오기 " 
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


# 리액트(react) async 장고 API 서버에 요청해서 자료 받아오기


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

```http://127.0.0.1:8000/test/test01data/Cheolwon```

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

```http://localhost:3000/find```

그리고 불러오기를 누르면 다음과 같은 화면이 출력됩니다. 

<center><img src="/assets/images/frontend/react/react-request-django/react-request-django08.png" width="800"></center>





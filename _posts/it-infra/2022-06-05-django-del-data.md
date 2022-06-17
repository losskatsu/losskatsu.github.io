---
title: "[Django]장고로 MySQL에 데이터 삭제(delete)하기"
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

# 장고로 MySQL에 데이터 삭제(delete)하기

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

본 예제는 맥OS 환경에서 실행했습니다.
실습 준비는 [이전 포스팅](https://losskatsu.github.io/it-infra/django-read-data/)을 참고해주세요. 

이번 실습에서는 DELETE 방식을 이용해 장고에서 MySQL로 기존에 존재하는 데이터를 삭제해 해보겠습니다. 


## 2. test01/views.py 수정

먼저 ```test01/views.py``` 파일에 다음 코드를 추가해줍니다. 

```python
@api_view(['DELETE'])
def delMember(request, pk):
    data = Test01.objects.get(id=pk)
    data.delete()
    return Response(status=status.HTTP_204_NO_CONTENT)
```

삭제 코드는 위와 같이 간단합니다. 

<center><img src="/assets/images/infra/django-del-data/django-del-data01.png" width="800"></center>

위 사진은 해당 코드가 추가된 모습입닏.

## 3. test01/urls.py 수정

이번에는 url을 추가해보겠습니다. 

```python
path('delMember/<str:pk>', views.delMember, name="delMember"),
```

위 코드를 추가하며 다음 그림고 같이 됩니다.

<center><img src="/assets/images/infra/django-del-data/django-del-data02.png" width="800"></center>

## 4. 서버 가동

이제 테스트르 위해 서버를 가동해보겠습니다. 먼저 migrate를 해줍니다.

```python
$ python manage.py makemigrations

No changes detected

$ python manage.py migrate       
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions, test01
Running migrations:
  No migrations to apply.

```

그리고 다음과 같이 장고 서버를 올려줍니다.


```python
$ python manage.py runserver     

Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
June 05, 2022 - 04:24:17
Django version 4.0.2, using settings 'dbcontest.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.

```

## 5. 삭제 요청 보내보기

웹 브라우저를 실행하고 다음 주소로 이동합니다. 

```http://127.0.0.1:8000/test/delMember/3```

그러면 다음과 같은 화면이 나옵니다. 

<center><img src="/assets/images/infra/django-del-data/django-del-data03.png" width="800"></center>

위 화면에서 우측 상단에 있는 ```DELETE```버튼을 누르면 다음고 같이 삭제 할거냐는 알람이 뜨는데 삭제해줍니다. 

<center><img src="/assets/images/infra/django-del-data/django-del-data04.png" width="800"></center>

그러면 다음 화면과 같이 잘 삭제 된것을 볼 수 있습니다.

<center><img src="/assets/images/infra/django-del-data/django-del-data05.png" width="800"></center>

데이터베이스로 가서 확인해도 잘 삭제된 것을 볼 수 있습니다. 

<center><img src="/assets/images/infra/django-del-data/django-del-data06.png" width="800"></center>




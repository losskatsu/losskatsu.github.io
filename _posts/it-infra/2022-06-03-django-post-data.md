---
title: "[Django]장고로 MySQL에 데이터 삽입(insert)하기"
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

# 장고로 MySQL에 데이터 삽입(insert)하기

### 참고 링크  

* [MySQL 윈도우에 설치하기](https://losskatsu.github.io/it-infra/mysql-install-win/)
* [MySQL 간단 정리, 우분투, 맥에 설치 하기](https://losskatsu.github.io/it-infra/mysql-index/)
* [맥 OS에 MySQL 설치](https://losskatsu.github.io/it-infra/mysql-install-mac/)

* [파이썬, MySQL 연동](https://losskatsu.github.io/programming/py-db-conn/)
* [데이터베이스에서 널(null)과 공백의 차이](https://losskatsu.github.io/it-infra/db-null/)

* [(1)MySQL에 데이터베이스, 테이블 생성하기](https://losskatsu.github.io/it-infra/mysql-create-db/)
* [(2)장고, MsSQL 연결하기](https://losskatsu.github.io/it-infra/mssql-django-conn/)
* [(2)장고, MySQL 연결하기](https://losskatsu.github.io/it-infra/mysql-django-conn/)
* [(3)장고 inpectdb로 DB 데이터 model.py로 만들기](https://losskatsu.github.io/it-infra/django-inspectdb/)
* [(4)장고로 MySQL에 있는 데이터 웹상에서 보여주기](https://losskatsu.github.io/it-infra/django-read-data/)
* [(5)장고로 MySQL에 데이터 insert 하기](https://losskatsu.github.io/it-infra/django-post-data/)
* [(6)장고로 MySQL에 데이터 수정(put) 하기](https://losskatsu.github.io/it-infra/django-put-data/)
* [(7)장고로 MySQL에 데이터 삭제(delete) 하기](https://losskatsu.github.io/it-infra/django-del-data/)



## 1. 실습 준비

본 예제는 맥OS 환경에서 실행했습니다.
실습 준비는 [이전 포스팅](https://losskatsu.github.io/it-infra/django-read-data/)을 참고해주세요. 

이번 실습에서는 POST 방식을 이용해 장고에서 MySQL로 데이터를 insert 해보겠습니다. 

## 2. test01/view.py 파일 수정

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

## 3. test01/urls.py 파일 수정 

이번에는 ```test01/urls.py```파일을 수정하겠습니다. 

```python
    path('postMember/', views.postMember, name="postMember"),
```

위 코드에 나와있는 ```postMember/```경로로 json 데이터를 던지면 데이터베이슬 insert해줍니다.

<center><img src="/assets/images/infra/django-post-data/django-post-data02.png" width="800"></center>

## 4. 서버 가동

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

## 5. POST 해보기

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







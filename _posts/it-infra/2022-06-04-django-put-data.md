---
title: "[Django]장고로 MySQL에 데이터 수정(put)하기"
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

# 장고로 MySQL에 데이터 수정(put)하기

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


## 1. 실습 준비

본 예제는 맥OS 환경에서 실행했습니다.
실습 준비는 [이전 포스팅](https://losskatsu.github.io/it-infra/django-read-data/)을 참고해주세요. 

이번 실습에서는 PUT 방식을 이용해 장고에서 MySQL로 기존에 존재하는 데이터를 수정해 해보겠습니다. 


## 2. test01/views.py



```python
@api_view(['PUT'])
def putMember(request, pk):
    reqData = request.data
    data = Test01.objects.get(id=pk)
    serializer = TestDataSerializer(instance=data, data=reqData)
    if serializer.is_valid():
        serializer.save()
        return Response(serializer.data)
    return Response(serializer.errors, status=status.HTTP_400_BAD_REQUEST)
```


<center><img src="/assets/images/infra/django-put-data/django-put-data01.png" width="800"></center>


## 3. test01/urls.py

```python
path('putMember/<str:pk>', views.putMember, name="putMember"),
```


<center><img src="/assets/images/infra/django-put-data/django-put-data02.png" width="800"></center>


## 4. 서버 가동


```python
$ python manage.py makemigrations

No changes detected

$ python manage.py migrate       

Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions, test01
Running migrations:
  No migrations to apply.
```

```python
$ python manage.py runserver     

Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
June 04, 2022 - 06:31:32
Django version 4.0.2, using settings 'dbcontest.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```



## 5. 데이터 수정해보기

<center><img src="/assets/images/infra/django-put-data/django-put-data06.png" width="800"></center>

```http://127.0.0.1:8000/test/putMember/3```

<center><img src="/assets/images/infra/django-put-data/django-put-data03.png" width="800"></center>

<center><img src="/assets/images/infra/django-put-data/django-put-data04.png" width="800"></center>

<center><img src="/assets/images/infra/django-put-data/django-put-data05.png" width="800"></center>

## 6. MySQL에 데이터 수정되었는지 확인 

<center><img src="/assets/images/infra/django-put-data/django-put-data06.png" width="800"></center>

<center><img src="/assets/images/infra/django-put-data/django-put-data07.png" width="800"></center>

## 7. 데이터 불러와서 확인

웹 브라우저에서 다음 주소로 API를 요청해 데이터가 잘 수정되었는지 확인해보겠습니다. 

```http://127.0.0.1:8000/test/test01datas/```

<center><img src="/assets/images/infra/django-put-data/django-put-data08.png" width="800"></center>

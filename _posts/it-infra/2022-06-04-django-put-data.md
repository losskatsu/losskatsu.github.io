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


## 2. test01/views.py 수정

먼저 test01 앱에 존재하는 ```views.py```파일에 다음 코드를 추가합니다. 


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

데이터를 수정할 때는 위 코드와 같이 ```PUT```메소드를 사용합니다. 
```reqData```는 내가 수정을 원해서 서버에 전달하는 json데이터를 의미하며 
```data```는 기존에 DB에 존재하는 데이터를 불러온 것을 의미합니다. 
요청시 ```pk```도 함께 전달하므로 해당 pk에 해당하는 데이터를 불러오는 것입니다. 
이 때 ```pk```는 데이터베이스 상의 ```id```컬럼이라는 것을 볼 수 있습니다. 
나머지 부분은 [이전 포스팅에서의 POST 메소드](https://losskatsu.github.io/it-infra/django-post-data/)와 비슷합니다.

<center><img src="/assets/images/infra/django-put-data/django-put-data01.png" width="800"></center>

따라서 전체 코드는 위와 같이 됩니다.


## 3. test01/urls.py

다음으로 test01 앱의 ```urls.py```파일에 다음 코드를 추가합니다.

```python
path('putMember/<str:pk>', views.putMember, name="putMember"),
```

위 코드를 추가하면 전체 코드는 아래와 같이 됩니다.

<center><img src="/assets/images/infra/django-put-data/django-put-data02.png" width="800"></center>


## 4. 서버 가동

이제 테스트르 위해 서버를 가동해보겠습니다. 
먼저 migrate를 해줍니다.

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
June 04, 2022 - 06:31:32
Django version 4.0.2, using settings 'dbcontest.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```



## 5. 데이터 수정해보기

우리는 기존 MySQL에 있는 데이터중 id가 3에 해당하는 hoshiumi 데이터를 수정해보겠습니다. 
다음 데이터를 보면 이름 첫문자가 소문자인데 이를 대문자로 수정하겠습니다.

<center><img src="/assets/images/infra/django-put-data/django-put-data06.png" width="800"></center>

데이터 수정을 위해 웹 브라우저를 열고 ```http://127.0.0.1:8000/test/putMember/3```에 접속합니다. 
주소의 마지막 ```3```은 id가 3이라는 것을 의마하며 이는 ```id=3```에 해당하는 데이터를 수정하겠다는 말입니다.

<center><img src="/assets/images/infra/django-put-data/django-put-data03.png" width="800"></center>

접속을 하면 위와 같은 창이 나오는데 수정을 원하는 데이터를 작성해봅시다.

<center><img src="/assets/images/infra/django-put-data/django-put-data04.png" width="800"></center>

수정할 데이터를 위와 같이 json 데이터 형태로 작성하고 ```PUT``` 버튼을 눌러줍니다.

<center><img src="/assets/images/infra/django-put-data/django-put-data05.png" width="800"></center>

요청이 제대로 간 것을 볼 수 있습니다.

## 6. MySQL에 데이터 수정되었는지 확인 

그렇다면 MySQL 데이터베이스 상에 있는 데이터가 수정되었는지 확인해보겠습니다. 

<center><img src="/assets/images/infra/django-put-data/django-put-data06.png" width="800"></center>

기존에는 위와 같으 데이터가 

<center><img src="/assets/images/infra/django-put-data/django-put-data07.png" width="800"></center>

이렇게 변한 것을 볼 수 있습니다. hoshiumi의 첫문자가 대문자로 바뀌어 Hoshiumi가 된 것을 볼 수 있습니다.

## 7. 데이터 불러와서 확인

웹 브라우저에서 다음 주소로 API를 요청해 데이터가 잘 수정되었는지 확인해보겠습니다. 

```http://127.0.0.1:8000/test/test01datas/```

<center><img src="/assets/images/infra/django-put-data/django-put-data08.png" width="800"></center>

---
title: "[리액트react] async 리액트에서 장고 API 요청해서 자료 받아오기(POST) " 
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


# 리액트(react) async 장고 API 서버에 요청해서 자료 받아오기(POST)


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
* [(1-5)장고 POST로 MySQL에 데이터 insert 하기](https://losskatsu.github.io/it-infra/django-post-data/)
* [(1-6)장고로 MySQL에 데이터 수정(put) 하기](https://losskatsu.github.io/it-infra/django-put-data/)
* [(1-7)장고로 MySQL에 데이터 삭제(delete) 하기](https://losskatsu.github.io/it-infra/django-del-data/)


### 프론트엔드  

* [(2-1)기본 리액트 프로젝트 생성](https://losskatsu.github.io/frontend/react-basic-setup/)
* [(2-2)리액트 카테고리 레이어 헤더 만들기](https://losskatsu.github.io/frontend/react-category/)
* [(2-3)장고 API 서버에 요청해서 자료 받아오기(GET)](https://losskatsu.github.io/frontend/react-request-api-django/)
* [(2-4)장고 API 서버에 요청해서 자료 받아오기(POST)](https://losskatsu.github.io/frontend/react-request-post/)

## 1. 사전 준비 사항

지금부터 만들 앱은 파이썬 장고(django)에 연동할 프론트를 리액트로 만드는 실습입니다.
본 포스팅은 [이전 포스팅](https://losskatsu.github.io/frontend/react-basic-setup/)에서 이어지는 포스팅 입니다.

이번 실습에서느 react에서 입력한 값을 POST 형식으로 장고 API에 요청해 받는 일을 해보겠습니다. 


## 2. 미리 작성된 JSON을 POST 형식으로 요청해서 결과 받아와서 보여주기

## 2-1. src/pages/Search.js 파일 생성

먼저 ```src/pages/Search.js``` 파일을 생성만 하고 넘어가겠습니다. 


## 2-2. src/components/Categories.js 파일 수정

먼저 메인 화면에서 '친구 탐색' 이라는 탭을 새로 추가해보겠습니다.

```react
const categories = [
  {
    name: 'home',
    text: '홈'
  },
  {
    name: 'find',
    text: '친구찾기'
  },
  {
    name: 'search',
    text: '친구탐색'
  }
];
```

<center><img src="/assets/images/frontend/react/react-request-post/react-request-post03.png" width="800"></center>

## 2-3. src/App.js 파일 수정

이번에는 App.js에서도 라우팅을 해주겠습니다. 

```react
import {Route, Routes} from 'react-router-dom';
import Home from './pages/Home.js';
import Find from './pages/Find.js';
import Search from './pages/Search.js';
import Categories from './components/Categories.js';

const App = () => {
  return(
    <Routes>
      <Route element={<Categories />}>
        <Route path="/" element={<Home />} />
        <Route path="/find" element={<Find />} />
        <Route path="/Search" element={<Search />} />
      </Route>
    </Routes>
  );
};

export default App;
```

<center><img src="/assets/images/frontend/react/react-request-post/react-request-post04.png" width="800"></center>


## 2-4. src/pages/Search.js 파일 

이번에는 본격적으로 ```src/pages/Search.js``` 파일에 다음과 같이 코드를 작성합니다. 

```react
import React, {useState} from 'react';
import axios from 'axios';

const Search = () => {
  const [data, setData] = useState(null);
  const reqData = JSON.stringify({
    'name': 'Cheolwon',
    'email': 'abcd@email.com'
  });
  const url = 'http://127.0.0.1:8000/test/getMembers/' ;
  const onClick = async () => {
    try{
      const response = await axios.post(url, reqData,{
        headers: {
          // Overwrite Axios's automatically set Content-Type
          'Content-Type': 'application/json'
        }
      });
      setData(response.data);
    } catch (e) {
      console.log(e)
    }
  };

  return(
    <div>
      <h1>친구탐색</h1>
      <p>보고싶은 친구를 탐색해보아요</p>
      <form>
         이름 : <input type = "text" placeholder="이름을 입력하세요" name = "name" /><br /><br />
         이메일: <input type = "text" placeholder="이메일을 입력하세요" name = "email" /><br /><br />
        <button type="submit" onClick={onClick}>탐색!</button>
      </form>
      <button type="submit" onClick={onClick}>탐색 테스트</button>
      {data && <textarea rows={15} value={JSON.stringify(data, null, 2)} readOnly={true}/>}
      {data && <li>{JSON.stringify(data, ['id', 'name', 'email'], 2)}</li>}
      {data && <li>{JSON.stringify(data, ['id'], 2)}</li>}
      {data && <li>{JSON.stringify(data, ['name'], 2)}</li>}
      {data && <li>{JSON.stringify(data, ['email'], 2)}</li>}
      {data && <li>id: {data[0].id}</li>}
      {data && <li>name: {data[0].name}</li>}
      {data && <li>email: {data[0].email}</li>}

    </div>
  );
};

export default Search;
```

<center><img src="/assets/images/frontend/react/react-request-post/react-request-post01.png" width="800"></center>

<center><img src="/assets/images/frontend/react/react-request-post/react-request-post02.png" width="800"></center>

파일이 길기 때문에 나눠서 살펴보겠습니다. 

```react
import React, {useState} from 'react';
import axios from 'axios';
```

가장 처음은 라이브러리 불러오는 부분인데 별거 없습니다. 

```react
  const [data, setData] = useState(null);
  const reqData = JSON.stringify({
    'name': 'Cheolwon',
    'email': 'abcd@email.com'
  });
  const url = 'http://127.0.0.1:8000/test/getMembers/' ;
```

위 코드에서 ```data```는 나중에 응답값을 넣을 변수입니다. 
그리고 ```reqData```는 POST형식으로 리퀘스트 보낼 데이터 입니다. 
그냥 딕셔너리 형태로 보내면 안되고 꼭 앞에 ```JSON.stringify```를 써서 JSON형식으로 변환하도록 합시다. 
그리고 ```url```은 요청 보낼 주소입니다. 

```react
  const onClick = async () => {
    try{
      const response = await axios.post(url, reqData,{
        headers: {
          // Overwrite Axios's automatically set Content-Type
          'Content-Type': 'application/json'
        }
      });
      setData(response.data);
    } catch (e) {
      console.log(e)
    }
  };
```

다음으로 ```onClick``` 이벤트를 작성해주는데 이때 중요한 점은 
post형식으로 보낼때 헤더를 작성해주는 것입니다. 
헤더를 ```application/json```으로 작성해줍니다. 

```react
return(
    <div>
      <h1>친구탐색</h1>
      <p>보고싶은 친구를 탐색해보아요</p>
      <form>
         이름 : <input type = "text" placeholder="이름을 입력하세요" name = "name" /><br /><br />
         이메일: <input type = "text" placeholder="이메일을 입력하세요" name = "email" /><br /><br />
        <button type="submit" onClick={onClick}>탐색!</button>
      </form>
      <button type="submit" onClick={onClick}>탐색 테스트</button>
      {data && <textarea rows={15} value={JSON.stringify(data, null, 2)} readOnly={true}/>}
      {data && <li>{JSON.stringify(data, ['id', 'name', 'email'], 2)}</li>}
      {data && <li>{JSON.stringify(data, ['id'], 2)}</li>}
      {data && <li>{JSON.stringify(data, ['name'], 2)}</li>}
      {data && <li>{JSON.stringify(data, ['email'], 2)}</li>}
      {data && <li>id: {data[0].id}</li>}
      {data && <li>name: {data[0].name}</li>}
      {data && <li>email: {data[0].email}</li>}

    </div>
  );
};
```

위 코드는 결과를 보여주는 화면단인데, 중요한 것은 다음 세줄 입니다. 

```react
{data && <li>id: {data[0].id}</li>}
{data && <li>name: {data[0].name}</li>}
{data && <li>email: {data[0].email}</li>}
```

위 코드에서 왜 [이전 포스팅](https://losskatsu.github.io/frontend/react-request-api-django/)에서와 같이 ```data.id```가 아니라 
왜 ```data[0].id```일까요? 그것은 이후 결과를 보면 알 수 있습니다.

<center><img src="/assets/images/frontend/react/react-request-post/react-request-post05.png" width="800"></center>

잠시 미리 결과를 보면 응답값은 JSON이 아니라 배열입니다. 
이 말은 배열 안에 JSON이 여러개 담겨져 있다는 것이니, 배열의 몇번째 JSON인지 인덱스를 지정해줘야한다는 것입니다. 
그래서 ```data.id```가 아니라 ```data[0].id```라고 쓰는 것입니다.


### 2.5. 테스트

리액트에서 ```npm start```로 서버켜고 다음과 같이 search 화면을 봅니다. 

<center><img src="/assets/images/frontend/react/react-request-post/react-request-post06.png" width="800"></center>


그리고 탐색 테스트를 누르면 다음과 같은 화면을 볼 수 있습니다. 

<center><img src="/assets/images/frontend/react/react-request-post/react-request-post06.png" width="800"></center>

이러면 일단 성공입니다.  










---
title: "[리액트react] 장고(Django)연동을 위한 기본 리액트 프로젝트 생성" 
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


# 리액트(react) 장고(Django)연동을 위한 기본 리액트 프로젝트 생성


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

먼저 프로젝트를 생성하겠습니다. 프로젝트 이름은 ```myapp01```로 하고 리액트 프로젝트를 다음과 같이 생성합니다. 

```bash
$ npm create react-app myapp01

Creating a new React app in /Users/cheolwon/Documents/test/nodejs/myapp01.

Installing packages. This might take a couple of minutes.
Installing react, react-dom, and react-scripts with cra-template...
...(중략)...
We suggest that you begin by typing:

  cd myapp01
  npm start

Happy hacking!
npm notice 
npm notice New minor version of npm available! 8.6.0 -> 8.12.1
npm notice Changelog: https://github.com/npm/cli/releases/tag/v8.12.1
npm notice Run npm install -g npm@8.12.1 to update!
npm notice 
```

프로젝트를 생성했으면 라우터 기능을 사용하기 위해 
프로젝트 디렉토리 내로 이동해 ```react-router-dom```을 설치해줍니다.

```bash
$ cd myapp01
$ npm add react-router-dom

added 3 packages, and audited 1423 packages in 3s

190 packages are looking for funding
  run `npm fund` for details

6 high severity vulnerabilities

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.
```

설치를 마쳤으면 인텔리제이를 이용해 프로젝트 디렉터리를 오픈합니다. 

## 2. src/index.js 파일 수정

먼저 src 디렉토리의 ```index.js```파일에 다음과 같이 router 관련 라이브러리를 추가하고 본문을 수정해줍니다. 

```react
import {BrowserRouter} from 'react-router-dom';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
```

그러면 전체 코드는 다음과 같이 됩니다. 

```react
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';
import {BrowserRouter} from 'react-router-dom';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();
```

<center><img src="/assets/images/frontend/react/react-django-conn01/react-basic-setup01.png" width="800"></center>

## 3. src/index.css 파일 수정

다음으로 ```index.css```파일을 수정하겠습니다. 
해당 파일의 내용을 다 지우고 다음과 같이 심플하게 적용해줍니다. 
저는 배경색만 지정해주겠습니다.

```css
body {
  background: #e9ecef;
}
```

전체코드도 다음과 같이 동일한 모습입니다.

<center><img src="/assets/images/frontend/react/react-django-conn01/react-basic-setup02.png" width="800"></center>

## 4. src/pages/Home.js 파일 생성 및 코드 작성

다음으로 src 하위에 pages라는 디렉터리를 만들겠습니다. 
pages는 이름그대로 하나의 웹 페이지를 모아놓는 디렉토리입니다. 
그리고 pages 내부에 Home.js 파일을 생성하고 다음과 같이 코드를 작성해줍니다. 

```react
const Home = () => {
  return(
    <div>
      <h1>홈</h1>
      <p>홈페이지에 오신 것을 환영합니다.</p>
    </div>
  );
};

export default Home;
```

전체 코드도 다음 그림과 같이 동일합니다.

<center><img src="/assets/images/frontend/react/react-django-conn01/react-basic-setup03.png" width="800"></center>

## 5. src/pages/Find.js 파일 생성 및 코드 작성

이번에는 pages 내부에 Find.js 파일을 생성하고 다음과 같이 코드를 작성해줍니다. 

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

간단한 코드이므로 전체 코드도 다음 스크린샷과 같이 동일합니다. 

<center><img src="/assets/images/frontend/react/react-django-conn01/react-basic-setup04.png" width="800"></center>

## 6. src/App.js 파일 수정

다음으로 src 내부에 있는 App.js 파일을 수정해주겠습니다. 
기존에 있던 기본 코드를 모두 지우고 다음과 같이 작성해줍니다.

```react
import {Route, Routes} from 'react-router-dom';
import Home from './pages/Home.js';
import Find from './pages/Find.js';

const App = () => {
  return(
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/find" element={<Find />} />
    </Routes>
  );
};

export default App;
```

전체 코드는 다음과 같습니다. 

<center><img src="/assets/images/frontend/react/react-django-conn01/react-basic-setup05.png" width="800"></center>

## 7. src/App.css 파일 수정

다음으로 App.css 파일도 수정해줍니다.
App.css에 있던 기존 코드를 모두 삭제해줍니다. 
그러면 다음 그림과 같이 아무 코드도 존재하지 않게 됩니다. 


<center><img src="/assets/images/frontend/react/react-django-conn01/react-basic-setup06.png" width="800"></center>


## 8. 리액트 앱 가동

준비가 되었으면 리액트 앱을 가동해보겠습니다. 

```bash
$ npm start

> myapp01@0.1.0 start
> react-scripts start

You can now view myapp01 in the browser.

  Local:            http://localhost:3000
  On Your Network:  http://172.30.1.49:3000

Note that the development build is not optimized.
To create a production build, use npm run build.

webpack compiled successfully
```

## 9. 확인

웹 브라우저 주소 창에 다음 주소를 입력해봅니다.

```http://localhost:3000```

그러면 다음과 같은 홈 화면이 나옵니다.

<center><img src="/assets/images/frontend/react/react-django-conn01/react-basic-setup07.png" width="800"></center>


다음으로 주소창에 다음 주소를 입력해봅시다.

```http://localhost:3000/find```

그러면 다음과 같은 창이 나올 것입니다. 

<center><img src="/assets/images/frontend/react/react-django-conn01/react-basic-setup08.png" width="800"></center>


오늘 실습은 여기까지입니다. 


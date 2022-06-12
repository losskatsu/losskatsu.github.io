---
title: "[리액트react] 리액트 카테고리 레이어 헤더 만들기" 
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


# 리액트(react) 카테고리 레이어 헤더 만들기


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

이번 실습에서 카테고리 레이어를 만들기 위해 ```styled-components```를 설치해주겠습니다. 

```bash
$ cd myapp01
$ npm add styled-components

added 13 packages, and audited 1436 packages in 7s

191 packages are looking for funding
  run `npm fund` for details

6 high severity vulnerabilities

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.
```

## 2. src/components/Categories.js 파일 생성

이번 실습에서는 홈페이지 상단 카테고리를 만들어보겠습니다.

src 디렉터리 하단에 ```components``` 디렉토리를 만들고 ```Categories.js```라는 파일을 생성하고 다음과 같은 코드를 입력합니다. 

```react
import styled from 'styled-components';
import {NavLink} from 'react-router-dom';
import {Outlet} from 'react-router-dom';


const categories = [
  {
    name: 'home',
    text: '홈'
  },
  {
    name: 'find',
    text: '친구찾기'
  }
];

const CategoriesBlock = styled.div`
  display: flex;
  padding: 1rem;
  width: 768px;
  margin: 0 auto;
  @media screen and (max-width: 768px) {
    width: 100%;
    overflow-x: auto;
  }
`;

const Category = styled(NavLink)`
  font-size: 1.125rem;
  cursor: pointer;
  white-space: pre;
  text-decoration: none;
  color: inherit;
  padding-bottom: 0.25rem;

  &:hover{
    color: #495057;
  }

  &+&{
    margin-left: 1rem;
  }
`;

const Categories = () => {
  return(
    <div>
      <header>
        <CategoriesBlock>
          {categories.map(c => (
            <Category
              key={c.name}
              to={c.name==='home'?'/':`/${c.name}`}
            >
              {c.text}
            </Category>
          ))}
        </CategoriesBlock>
      </header>
      <main>
        <Outlet />
      </main>
    </div>
  );
};

export default Categories;
```

코드가 길기 때문에 잘라서 나누어 보겠습니다. 

<center><img src="/assets/images/frontend/react/react-category/react-category01.png" width="800"></center>

### 2.1. 라이브러리 불러오는 부분

```react
import styled from 'styled-components';
import {NavLink} from 'react-router-dom';
import {Outlet} from 'react-router-dom';
```

먼저 라이브러리를 불러오는 부분입니다. 카테고리 부분을 예쁘게 하기 위해서는 'styled-components'의 ```styled```를 사용하면 좋습니다. 
그리고 ```NavLink```는 카테고리를 클릭했을 때 다른 주소로 넘어가는 라우팅 역할을 하는 친구입니다. 이 친구 이후 컴포넌트에서 ``to``로 사용할 수 있습니다. 
그리고 ```Outlet```은 ```body```부분에 사용하는 친구입니다. 

### 2.2. 카테고리 종류

다음으로 카테고리 메뉴를 만들어보겠습니다. 

```react

const categories = [
  {
    name: 'home',
    text: '홈'
  },
  {
    name: 'find',
    text: '친구찾기'
  }
];
```

위 코드를 보면 ```caterories```라는 배열은 ```home```과 ```text```로 구성된 딕셔너리의 조합입니다. 
```name```은 세부 url을 의미하며 ```text```는 홈페이지 화면에서 표시될 내용입니다. 

### 2.3. 카테고리 영역 블락(block)

이 영역은 홈페이지 상단의 카테고리 블락을 어떻게 스타일링 할 것인지를 정합니다.

```react
const CategoriesBlock = styled.div`
  display: flex;
  padding: 1rem;
  width: 768px;
  margin: 0 auto;
  @media screen and (max-width: 768px) {
    width: 100%;
    overflow-x: auto;
  }
`;
```

위 코드를 보면 앞서 임포트한 ```styled```를 이용해 ```styled.div```를 통해 카테고리 영역 스타일링을 합니다. 
이때 주의할 것은 styled.div 다음 영역을 그래이브(backquote) 키로 감싸주어야 합니다. 

### 2.4. 카테고리 버튼 영역 스타일

```react
const Category = styled(NavLink)`
  font-size: 1.125rem;
  cursor: pointer;
  white-space: pre;
  text-decoration: none;
  color: inherit;
  padding-bottom: 0.25rem;

  &:hover{
    color: #495057;
  }

  &+&{
    margin-left: 1rem;
  }
`;

```

### 2.5. 카테고리 컴포넌트

본격적은 카테로기 컴포넌트 메인 코드를 작성하면 다음과 같습니다. 

```react
const Categories = () => {
  return(
    <div>
      <header>
        <CategoriesBlock>
          {categories.map(c => (
            <Category
              key={c.name}
              to={c.name==='home'?'/':`/${c.name}`}
            >
              {c.text}
            </Category>
          ))}
        </CategoriesBlock>
      </header>
      <main>
        <Outlet />
      </main>
    </div>
  );
};

export default Categories;
```

```header``` 부분에는 위에서 작성한 카테로그 영역 스타일링한 ```CategoriesBlock```을 이용해 스타일로 감싸주고 
카테고리 텍스트 영역을 작성해주는데 이때 ```key```와 ```to```는 위에서 불로온 ```NavLink```를 이용한 것입니다. 
그리고 본문에 해당하는 ```main```에서는 위에서 불러온 ```Outlet```을 사용합니다. 

## 3. src/App.js 파일 수정 

마지막으로 ```App.js```파일을 수정해보겠습니다. 

```react
import {Route, Routes} from 'react-router-dom';
import Home from './pages/Home.js';
import Find from './pages/Find.js';
import Categories from './components/Categories.js';

const App = () => {
  return(
    <Routes>
      <Route element={<Categories />}>
        <Route path="/" element={<Home />} />
        <Route path="/find" element={<Find />} />
      </Route>
    </Routes>
  );
};

export default App;
```

```App.js```파일에서는 앞서 만든 ```Categories.js```파일을 import 해주고 
```Categories``` 영역으로 세부 주소에 해당하는 화면을 덮어줍니다. 

<center><img src="/assets/images/frontend/react/react-category/react-category02.png" width="800"></center>

## 4. 서버 가동

```
$ npm start
You can now view myapp01 in the browser.

  Local:            http://localhost:3000
  On Your Network:  http://192.168.11.135:3000

Note that the development build is not optimized.
To create a production build, use npm run build.

webpack compiled successfully
```

<center><img src="/assets/images/frontend/react/react-category/react-category03.png" width="800"></center>

위 화면 처럼 친구찾기 버튼을 누르면 해당 페이지로 이동하는 것을 볼 수 있습니다. 

<center><img src="/assets/images/frontend/react/react-category/react-category04.png" width="800"></center>




---
title: "[리액트react] 프로젝트 초기 세팅, 불필요한 코드 지우기 " 
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

# 리액트(react) 프로젝트 초기 세팅, 불필요한 코드 지우기


## 참고 링크  

* [nodejs 윈도우에 설치하기](https://losskatsu.github.io/programming/nodejs-install-win/)
* [vscode 윈도우에 설치하기](https://losskatsu.github.io/programming/vscode-install-win/)

## 1. 프로젝트 생성

먼저 프로젝트를 생성합니다.

```react
$ yarn create react-app 프로젝트명
```

터미널에 위 코드를 입력하면 리액트 프로젝트가 생성됩니다. 

```react
$ cd 프로젝트명
$ yarn start
```

그리고 위와 같이 프로젝트명 폴더로 이동해서 yarn start를 입력하면 브라우저 창에서 리액트 마크가 돌아가는 모습을 볼 수 있는데, 
사실 이와 같은 기본 코드에는 불필요한 코드가 많아서 
이번 포스팅에서는 불필요한 코드를 지우는 작업을 해보겠습니다. 


## 2. 불필요한 파일 삭제 및 index.html 코드 정리

<center><img src="/assets/images/frontend/react/react-helloworld/react-helloworld01.png" width="800"></center>

먼저 위와 같은 그림에서 좌측 파일 목록의 파일을 제외한 나머지 파일은 불필요하므로 모두 삭제해줍니다. 
그리고 오른쪽 그림은 public 폴더의 index.html 파일인데, 해당 파일에서 노란색으로 표시한 줄을 모두 삭제해줍니다.

<center><img src="/assets/images/frontend/react/react-helloworld/react-helloworld02.png" width="800"></center>

그러면 위와 같이 정리되는 것을 알 수 있습니다.


## 3. src/App.css 파일 정리

<center><img src="/assets/images/frontend/react/react-helloworld/react-helloworld03.png" width="800"></center>

다음으로는 src 폴더 내부의 App.css 파일을 수정합니다. 위 그림과 같이 기존 코드를 모두 삭제하고 위 파일 내용처럼 정리해줍니다.


## 4. src/App.js 파일 정리

<center><img src="/assets/images/frontend/react/react-helloworld/react-helloworld04.png" width="800"></center>

이번에는 src 폴더내부의 App.js 파일을 수정하겠습니다. 위 그림과 같이 간단하게 수정해줍니다.

## 5. src/index.css 파일 정리

<center><img src="/assets/images/frontend/react/react-helloworld/react-helloworld05.png" width="800"></center>

이번에는 src 폴더 내부의 index.css 파일을 정리해줍니다. 위 그림에 표시된 부분을 모두 삭제해줍니다.

<center><img src="/assets/images/frontend/react/react-helloworld/react-helloworld06.png" width="800"></center>

그러면 위와 같은 코드만 남습니다.

## 6. 실행

그리고 터미널에 yarn start 명령어를 입력하면 제대로 실행되는 것을 알 수 있습니다.


## 7. 참고 

참고로 필요하다면 react-router-dom을 추가하면 좋습니다.

```react
프로젝트명$ yarn add react-router-dom
```


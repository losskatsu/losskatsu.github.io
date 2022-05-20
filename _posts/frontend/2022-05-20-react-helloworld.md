---
title: "[리액트react] 시작하기 hello world" 
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


# 리액트(react) 시작하기 hello world! 

## 1. 사전 준비 사항

리액트를 시작하기 위해서는 다음 3가지가 준비되어 있어야 합니다. 

* node.js 설치
* npm 또는 yarn 설치
* 텍스트편집기(vs code, intellij 등)

### 1.1. node.js 설치 버전 확인

```bash
$ node -v
v18.0.0
```

### 1.2. npm 버전 확인

```bash
$ npm -v
8.6.0
```


## 2. 프로젝트 생성

저는 test 디렉토리 안에 hello-react라는 프로젝트를 생성하겠습니다.
프로젝트를 생성하면 hello-react라는 폴더가 생깁니다. 
이를 위해 먼저 test 디렉토리로 이동해서 ```npm create react-app hello-react```를 실행합니다. 
시간이 프로젝트를 생성하는데 시간이 조금 걸립니다. 

```bash
$ cd test
$ npm create react-app hello-react
Creating a new React app in /Users/cheolwon/Documents/test/nodejs/hello-react.

Installing packages. This might take a couple of minutes.
Installing react, react-dom, and react-scripts with cra-template...
...(중략)
We suggest that you begin by typing:

  cd hello-react
  npm start

Happy hacking!
npm notice 
npm notice New minor version of npm available! 8.6.0 -> 8.10.0
npm notice Changelog: https://github.com/npm/cli/releases/tag/v8.10.0
npm notice Run npm install -g npm@8.10.0 to update!
npm notice 
```

## 3. 프로젝트 실행

프로젝트를 생성하면 hello-react 디렉토리가 생성된 것을 알 수 있습니다.

```bash
$ ls -al
total 0
drwxr-xr-x  10 cheolwon  staff   320B  5 20 14:49 hello-react/
```

그리고 hello-react 디렉토리로 이동해 ```npm start``` 를 입력하면 화면이 뜹니다!

```bash
$ cd hello-react
$ npm start
Compiled successfully!

You can now view hello-react in the browser.

  Local:            http://localhost:3000
  On Your Network:  http://192.168.35.239:3000

Note that the development build is not optimized.
To create a production build, use npm run build.

webpack compiled successfully
```


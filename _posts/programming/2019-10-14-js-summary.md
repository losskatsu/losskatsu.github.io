---
title: "[Javascript] 자바스크립트 기초 간단 정리" 
categories:
  - programming
tags:
  - programming
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 자바스크립트 기초 간단 정리

## 1. 개발 초기

자바스크립트는 웹브라우저에서 실행되는 웹 클라이언트 애플리케이션 개발을 목적으로 만들었습니다. 
자바스크립트는 모든 웹 브라우저에서 실행할 수 있는 유일한 프로그래밍 언어인데요. 
자바스크립트는 혼자서는 아무것도 할수 없었던 프로그래밍 언어였습니다. 
그저 웹 브러우저 화면에서 뭔가를 움직이게 하는 정도가 전부였구요. 
시간이 흘러, 2004년에 자바스크립트로만 만든 웹페이지가 데스크톱에서 사용하는 
애플리케이션 형태를 띈 구글 지도(Google Maps)가 등장했습니다. 
최근에는 Nodejs가 등장하면서 자바스크립트로도 웹서버를 개발할 수 있게 되었습니다. 
즉, 자바스크립트 프로그래밍 언어만 알아도 웹 개발을 모두 할 수 있게 된 것이죠. 

* 동기: 처리의 흐름이 순차적으로 진행되는 것.
* 비동기: 처리의 흐름이 순차적으로 진행되지 않고 섞이는 것.

## 2. 프로그래밍 환경

* 아톰(Atom) 에디터 설치: [https://atom.io](https://atom.io)
* Node.js 설치(LTS버전 설치 권장): [https://nodejs.org/en/](https://nodejs.org/en/)

```bash
// node 설치 확인
> node -v
```
## 3. 표준 내장 객체

자바스크립트에서는 수백개가 넘는 속성과 메소드를 제공합니다. 아래 링크를 참고해주세요. 

[자바스크립트 표준 내장 객체 보기](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects)

## 4. 웹페이지 생성 순서

웹브라우저가 웹페이지를 실행하는 순서는 HTML코드를 위에서 아래로 실행합니다. 
script 태그를 head에 넣는 방법이 있고 body뒤에 넣는 방법이 있는데, 
개인적으로는 body 뒤에 넣는게 더 좋다고 생각합니다. 

## 5. jQuery

많은 프로그래밍 언어가 라이브러리를 사용하는데요, 자바스크립트도 라이브러리를 사용합니다. 
바로 jQuery라는 라이브러리 입니다. 

[jQuery 다운받기](http://jquery.com/)

jQuery를 사용하는 방법은 두가지가 있습니다. 첫번째는 특정 폴더에 다운로드한 후 HTML 페이지로 가져오는 것입니다. 
두번째 방법은 CDN(Content Delivery Network)를 활용하는 것입니다. 
CDN은 사용자에게 간편하게 콘텐츠를 제공하는 방식입니다. 
세계 여러 곳에 서버가 있는 기업(구글 등)이 사용자와 가장 가까운 곳에 있는 서버에서 데이터를 전달하므로 
빠르게 자바스크립트 파일을 불러올 수 있습니다. 

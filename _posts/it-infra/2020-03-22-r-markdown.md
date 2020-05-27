---
title: "R 마크다운(markdown)으로 한글 pdf 저장하기" 
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

# R 마크다운(markdown)으로 한글 pdf 저장하기

참고링크

* [R 마크다운 치트시트](https://rstudio.com/wp-content/uploads/2016/02/rmarkdown-cheatsheet-kr.pdf)

## 사전준비물 - latex 설치

R의 결과물을 pdf파일로 저장하기 위해선 우선 latex가 설치되어있어야 합니다. 
[latex설치 링크](http://wiki.ktug.org/wiki/wiki.php/%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0Windows/tlinstall)로 가시면 
latex를 설치하실수 있습니다. 
기본적인 latex는 영문만 지원하므로, latex로 한글을 출력하기 위해선 kotex를 설치하셔야 합니다. 
[kotex설치 참조 링크](http://www.ktug.org/xe/index.php?mid=Install)로 가시면 설치하실 수 있습니다. 
latex가 꽤 무거운 프로그램이다보니 설치 시간이 다소 걸릴 수 있습니다. 
latex및 kotex를 설치하셨다면 다음 단계로 가시죠. 

## R 패키지 설치

R을 실행한 후 rmarkdown이라는 패키지를 설치해 줍시다. 

```R
install.packages("rmarkdown")
```

## mark다운 파일 생성하기

<center><img src="/assets/images/infra/rmarkdown/01.JPG" width="800"></center>

<center><img src="/assets/images/infra/rmarkdown/02.jpg" width="800"></center>


## 아웃풋 설정

```R
---
title: "R마크다운으로 한글 저장"
mainfont: NanumGothic
output:
  pdf_document:
    latex_engine: xelatex
  word_document: default
  html_document:
    df_print: paged
editor_options:
  chunk_output_type: console
---
```

아웃풋 설정에서 latex_engine을 설정해주셔야하는데요, 저는 xelatex이기 때문에 xelatex라고 설정했습니다. 
또한 한글 글씨체중 나눔고딕을 설치하고 mainfont를 나눔고딕으로 설정했습니다. 

## R 재실행하기

이것 저것 설치를 하셨으면 R을 재시작하겠습니다. 
저는 재시작 안하고 실행했었는데 대체 왜 안되는거지라며 원인을 다른데서 찾았네요ㅠ

## 아웃풋 확인

<center><img src="/assets/images/infra/rmarkdown/03.jpg" width="800"></center>


## 참고: 옵션

<center><img src="/assets/images/infra/rmarkdown/04.jpg" width="800"></center>

## 참고: 옵션2

선택옵션 | 기본설정 | 효과
--------|---------|------- 
eval | TRUE | 코드 평가 및 결과 포함
echo | TRUE | 실행결과와 함께 코드 출력
warning | TRUE | 경고메시지 출력 
error | FALSE | 오류메시지 출력
message | TRUE | 메시지 출력
tidy | FALSE | 깔끔한 방식으로 코드 변형
results | "markup" | "markup", "asis", "hold", "hide"
cache | FALSE | 결과값을 캐쉬해서 향후 실행시 건너뛰게 설정
comment | "##" | 주석문자로 출력결과 서두에 붙인다.
fig.width | 7 | 덩어리로 생성되는 그래프 폭 인치 지정
fig.height | 7 | 덩어리로 생성되는 그래프에 대한 높이 인치 지정 
 
### 사용법

```r
---
title: "자기가 원하는 제목"
mainfont: NanumGothic
output:
  pdf_document:
    latex_engine: xelatex
  word_document: default
  html_document:
    df_print: paged
editor_options:
  chunk_output_type: console
---

(R코드 실행시 이 괄호 제거)```{r setup, include=FALSE} 
knitr::opts_chunk$set(echo = TRUE, error = FALSE, warning = FALSE)
(R코드 실행시 이 괄호 제거)```
```

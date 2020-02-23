---
title: "[기초통계] 유의수준, 유의확률, 검정력의 의미" 
categories:
  - statistics
tags:
  - statistics
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 유의수준, 유의확률, 검정력의 의미

참고링크
* [ROC 커브 복습하기](https://losskatsu.github.io/machine-learning/stat-roc-curve)

## 통계적 가설검정

오늘은 가설검정의 기초개념에 대해 알아보겠습니다. 
통계적 가설검정(statistical hypothesis test)의 정의는 다음과 같습니다.

> 통계적 가설검정은 통계적 추측의 하나로서,  [모집단](https://losskatsu.github.io/statistics/population-sample/) 실제의 값이 얼마가 된다는 주장과 관련해, [표본](https://losskatsu.github.io/statistics/population-sample/)의 정보를 사용해서 가설의 합당성 여부를 판정하는 과정을 의미한다. 간단히 가설 검정이라고 부르는 경우가 많다. 

즉, 통계적 가설검정은 자신이 세운 가설을 통계적 방법으로 검증하는 것을 의미합니다. 


## 귀무가설, 대립가설

가설에는 두가지 종류가 있는데요. 귀무가설(null hypothesis), 대립가설(alternative hypothesis)이 그것입니다. 
귀무가설의 정의부터 보시겠습니다. 

> 귀무가설(null hypothesis, H0) 또는 영가설은 통계학에서 처음부터 버릴 것을 예상하는 가설이다. 

귀무가설은 기존에 존재하는 가설이라고 보시면 됩니다. 분석가가 주장하는 가설의 반대인 가설입니다. 
반대로 분석가가 주장하고자 하는 가설은 대립가설인데요. 다음은 대립가설의 정의입니다. 

> 대립가설(alternative hypothesis, H1)은 귀무가설에 대립하는 명제이다. 

귀무가설과 대립가설의 예는 다음과 같습니다. 

* 어떤 사건의 특정 용의자를 진범으로 추정하는 상황에서 
  * 귀무가설- 해당 용의자는 진범이 아니다.
  * 대립가설- 해당 용의자는 진범이다.
* 신약을 개발한 후 기존 약과 비교를 하는 상황에서
  * 귀무가설- 신약은 기존 약과 치료율의 차이가 없다.
  * 대립가설- 신약은 기존 약보다 치료율이 높다.

## 1종오류, 2종오류

가설검정 후 제가 내린 결론이 참일 수도 있고 거짓일 수도 있는데요. 
통계적 오류 관련된 오류는 두 가지가 있습니다. 
바로 1종 오류(type I error)와 2종 오류(type II error)가 그것입니다. 

> 1종 오류(type I error, alpha error)는 귀무가설이 실제로 참이지만, 이에 불구하고 귀무가설을 기각하는 오류(H0 기각, H1 채택). 즉, 실제 음성인 것을 양성으로 판정하는 경우이다. 

> 2종 오류(type II error, beta error)는 귀무가설이 실제로 거짓이지만 이에 불구하고 귀무가설을 채택하는 오류(H1 기각, H0 채택). 즉, 실제 양성인 것을 음성으로 판정하는 경우이다. 

1종 오류와 2종 오류는 다음과 같은 예로 설명드릴 수 있겠네요. 

* 어떤 사건의 특정 용의자를 진범으로 추정하는 상황에서
  * 1종 오류- 용의자는 실제로 진범이 아니지만, 이에 불구하고 용의자를 진범으로 추정한 경우(H0 기각, H1 채택).
  * 2종 오류- 용의자가 실제로 진범이지만 이에 불구하고 용의자가 진범이 아니라고 추정한 경우(H1 기각, H0 채택).

## 유의수준

## 유의확률

## 검정력

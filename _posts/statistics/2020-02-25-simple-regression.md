---
title: "[기초통계] 단순 회귀분석의 개념과 의미" 
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


# 단순 회귀분석 정리

## 회귀분석 정의

> 회귀분석(regression analysis)는 [변수](https://losskatsu.github.io/statistics/random-variable/)들간의 함수관계를 추구하는 통계적 방법이다. 

회귀분석은 독립변수와 종속변수 간의 함수관계를 규명하는 통계적 방법입니다. 
그렇다면 독립변수와 종속변수는 무엇일까요?

> 독립변수(independent variable)는 입력값이나 원인을 나타내며, 종속변수(dependent variable)은 결과물이나 효과를 나타낸다. 

독립변수는 설명변수(explanatory variable)이라고도 하며, 종속변수는 반응변수(response variable)이라고도 합니다. 
독립변수와 종속변수는 $(x_i, y_i)$ 쌍으로 표현하고 독립변수의 집합을 대문자 $X$, 종속변수의 집합을 대문자 $Y$로 표현합니다. 
결국 회귀분석이란 독립변수 $X$의 분포를 분석한 후, 종속변수 $Y$의 값을 예측하는 것입니다. 
다른 말로하면 다양하게 분포된 $X$가 존재할 때, $Y$의 분포를 알아내는 것입니다. 

![figure01](){: width="500"}

오늘 알아볼 것은 독립변수가 한 개일 경우, 즉 **단순회귀분석**에 대해 알아보겠습니다. 

## 평균 함수(mean function)

우리가 $Y$의 분포에 대해 관심있을 때 중요한 것이 mean function 입니다. 

$$ E(Y|X=x) = \text{a function that depends on the value of } x $$

데이터에 대해서 생각해보면 데이터는 이미 '주어졌다'는 것을 알 수 있습니다. 
'주어졌다'를 다른 말로 바꾸면 '정해졌다'라고 할 수 있는데요. 
위 식에서 기대값은 $x$값이 '이미 정해을때'라는 조건부 기대값으로 볼 수 있습니다.
이를 수식으로 나타내면,

$$ E(Y|X=x) = \beta_{0} + \beta_{1}x $$

위 mean function을 자세히 살펴보면, 직선이라는 것을 알 수 있는데요. 
$\beta_{0}$가 절편(intercept)이 되고, $\beta_{1}$은 기울기(slope)입니다. 
또한 위 식에서 $\beta_{0} \, \beta_{1}$는 [모수](https://losskatsu.github.io/statistics/population-sample/)이며, 
우리가 추정해야할 값입니다. 

## 분산함수(variance function)

회귀분석에서 종종 적합 모델에 사용되는 가정은 모든 $x$값에 대해 [분산](https://losskatsu.github.io/statistics/mean-vairance/)이 동일하다는 것입니다. 
즉, 

$$ Var(Y|X=x) = \sigma^{2} $$

이며, [분산](https://losskatsu.github.io/statistics/mean-vairance/)이 얼마인지는 모르는상태(unknown)입니다. 

## 통계적 오차(statistical error)

회귀분석에서 빼놓을 수 없는 요소가 바로 오차(error)인데요. 
여기서 말하는 에러는 통계적 오차(statistical error)입니다. 
왜냐하면 우리가 예상한 종속변수 $y$값은 실제로 관측된 $y$값과 차이가 날 수 있기 때문입니다. 
즉, $E(Y|X=x_i)$와 $y_{i}$가 다를 수 있다는 뜻이죠. 이를 수식으로 나타내면 다음과 같습니다. 

$$ y_{i} = E(Y|X=x_{i})+e_{i} $$ 

$$ e_{i} = y_{i} - E(Y|X=x_{i}) = y_{i} - \beta_{0} + \beta_{1}x_i $$ 


![figure02](){: width="500"}



오차항에는 두가지 가정이 필요합니다. 

1. 오차항의 기대값은 0이다. $E(e|x_{i}) = 0$.
즉, 가로축을 $x_{i}$라고 놓고, 세로축을 $e_{i}$로 놓고 그래프르를 그리면 패턴이 없다는 뜻입니다. 

2. 오차항은 모두 서로독립(independent)이다. 
즉, 하나의 오차는 다른 오차에 대해 어떠한 정보도 줄 수 없다는 뜻 입니다. 영향을 끼치지 않는다는 뜻이죠. 

이 밖에도 오차항이 [정규분포](https://losskatsu.github.io/statistics/mean-vairance/)를 따라야한다는 가정도 있는데요. 
이 가정은 다소 강한 가정으로 오차항이 반드시 [정규분포](https://losskatsu.github.io/statistics/mean-vairance/)를 따라야하는 것은 아닙니다. 

또한 오차항은 [확률변수](https://losskatsu.github.io/statistics/random-variable/)이지만 [모수](https://losskatsu.github.io/statistics/population-sample/)는 아닙니다.

## 최소제곱법 

$$ y = \beta_{0} + \beta_{1}x $$

위와 같은 회귀분석 식에서 우리가 추정해야할 [모수](https://losskatsu.github.io/statistics/population-sample/)는 $\beta_{0} \, \beta_{1}$입니다. 최소제곱법은 바로 이 모수를 추정하는 방식으로 오차항의 제곱합을 최소화 하는 방식으로 값을 구합니다. 

> 최소제곱법(ordinary least squares, OLS)은 오차의 제곱합이 최소가 되는 해를 구하는 방법이다. 

잠시 표기법에 대해 언급하겠습니다. 
$y_i$는 실제값을 의미하구요, $\hat{y_i}$는 $i$번째 $y$의 추정치를 의미합니다. 
따라서 최소제곱법을 통해 구한 회귀식은 아래와 같이 표현됩니다. 

$$  \hat{y_i} = \hat{E}(Y|X=x_i) = \hat{\beta_{0}} + \hat{\beta_{1}}x_i $$

다음으로 오차항의 추정치는 아래와 같이 나타납니다. 

$$ \hat{e_i} = y_i - \hat{E}(Y|X=x=x_i) = y_i - \hat{y_i} = y_i - (\hat{\beta_0} + \hat{\beta_1}x_i) $$

결국, 최소제곱법이란 

$$ RSS = \sum_{i=1}^{n}\[y_i - (\hat{\beta_0} + \hat{\beta_1}x_i\]^{2} $$

을 최소화 시키는 것을 의미합니다. 이 때 RSS를 Residual sum of squares라고 합니다. 
최소제곱법을 이용한 모수의 추정치는 아래와 같습니다. 



## 최소제곱법으로 구한 모수 추정치

$$ \hat{\beta_{1}} = \frac{sum_{i=1}^{n}(x_i - \bat{x})(y_i - \bar{y})}{\sum_{i=1}^{n}(x_i - \bar{x})^{2} } $$ <br />

$$ \hat{\beta_{0}} = \bar{y} - \hat{\beta_{1}} - \hat{\beta_{1}}\bar{x} $$

## 분산 추정

$$ \hat{\sigma^2} = \frac{RSS}{n-2} $$

## 부록

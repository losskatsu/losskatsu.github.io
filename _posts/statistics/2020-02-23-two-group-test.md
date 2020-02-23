---
title: "[기초통계] 두 집단 간 평균, 분산 비교, T-test, F-test" 
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

# 두 집단 간 평균, 분산 비교, T-test, F-test

참고링크
* [모집단과 표본의 개념](https://losskatsu.github.io/statistics/population-sample/)
* [확률변수 개념](https://losskatsu.github.io/statistics/random-variable/)
* [확률분포의 의미 및 종류](https://losskatsu.github.io/statistics/prob-distribution/)
* [평균, 분산의 의미](https://losskatsu.github.io/statistics/mean-vairance/)
* [유의수준, 유의확률, 검정력의 의미](https://losskatsu.github.io/statistics/alpha-beta-test/)


## 1. 모분산이 알려진 경우(known population variacne)

모분산이 알려진 경우에는 모분산을  사용하지만 모분산이 알려지지 않더라도 표본의 크기가 큰 경우에는 표본분산을 모분산의 추정치로 사용가능합니다. 
또한 표본의 크기가 큰 경우에는 모집단이 정규분포를 따르지 않더라도 정규분포를 이용한 검정을 할 수 있습니다. 

### 1-1. 데이터 셋팅 및 가정 확인 

우선 두 집단의 분산이 알려진 경우라고 가정합시다.  
두 집단이 [iid](https://losskatsu.github.io/statistics/prob-distribution/)를 따른다고 가정합시다. 

$$ x_{1}, x_{2}, \dots ,x_{n1} \sim N(\mu_{1}, \sigma_{1}^{2}) $$, <br />
$$ y_{1}, y_{2}, \dots ,y_{n2} \sim N(\mu_{2}, \sigma_{2}^{2}) $$

위 식은 $x_{1}, x_{2}, \dots ,x_{n1}$은 평균 $\mu_{1}$이고, 분산이 $\sigma_{1}^{2}$인 정규분포에서 나온 표본이라는 뜻이고, 
$y_{1}, y_{2}, \dots ,y_{n2}$는 평균 $\mu_{2}$이고, 분산이 $\sigma_{2}^{2}$인 정규분포에서 나온 표본이라는 뜻입니다. 

### 1-2. 가설설정 

저희가 알고 싶은 것은 두 집단의 평균이 같냐 다르냐입니다. 
여기서 평균이 다를 경우 평균이 큰지, 작은지, 아니면 그저 다른지에 따라 아래처럼 세 가지 형태로 가설을 세울 수 있습니다. 

$$ H0: \mu_{1} - \mu_{2} = 0, \, H1: \mu_{1} - \mu_{2} > 0 $$, <br />
$$ H0: \mu_{1} - \mu_{2} = 0, \, H1: \mu_{1} - \mu_{2} < 0 $$, <br />
$$ H0: \mu_{1} - \mu_{2} = 0, \, H1: \mu_{1} - \mu_{2} \neq 0 $$

### 1-3. 검정통계량 

가설을 세운 후 가설을 검정하는 기준인 검정 통계량은 아래와 같은 식을 사용합니다.  

$$ Z = \frac{(\bar{x} - \bar{y}) - (\mu_{1} - \mu_{2})}{\sqrt{\sigma_{1}^{2}/n_{1} + \sigma_{2}^{2}/n_{2}}} $$

### 1-4. 가설검정 

그리고 위에 세운 가설의 형태와 검정통계량을 기준으로 아래와 같이 판별합니다.

$$ H0: \mu_{1} - \mu_{2} = 0, \, H1: \mu_{1} - \mu_{2} > 0 $$일 때,  $Z > z_{\alpha}$이면 H0 기각<br />
$$ H0: \mu_{1} - \mu_{2} = 0, \, H1: \mu_{1} - \mu_{2} < 0 $$일 때, $Z < -z_{\alpha}$이면 H0 기각<br />
$$ H0: \mu_{1} - \mu_{2} = 0, \, H1: \mu_{1} - \mu_{2} \neq 0 $$일 때, $ \|Z\| > z_{\alpha}$이면 H0 기각

### 1-5. 신뢰구간

모평균의 차이 $\mu_{1} - \mu_{2}$의 $100(1-\alpha)$% 신뢰구간은 아래와 같습니다.


$$ \bigg( (\bar{x}-\bar{y})-z_{\alpha/2} \sqrt{\frac{\sigma_{1}^{2}}{n_{1}}+ \frac{\sigma_{2}^{2}}{n_{2}}}, \,  (\bar{x}-\bar{y})+z_{\alpha/2} \sqrt{\frac{\sigma_{1}^{2}}{n_{1}}+ \frac{\sigma_{2}^{2}}{n_{2}}}\bigg) $$

## 2. 모분산이 알려지지 않은 경우(unknown population variance)

### 2-1. 모분산의 동일성 검정

모분산이 알려지지 않은 경우 모분산이 같은지 아닌지를 먼저 검정해야합니다. 
즉, 평균차이를 알아보기 전에 분산이 동일한지를 검정해야하기 때문에 모분산 비를 검정합니다. 

우선 가설은 아래와 같이 세웁니다. 

$$ H0: \sigma_{1}^{2}/\sigma_{2}^{2} = 1, \, H1: \sigma_{1}^{2}/\sigma_{2}^{2} > 1 $$, <br />
$$ H0: \sigma_{1}^{2}/\sigma_{2}^{2} = 1, \, H1: \sigma_{1}^{2}/\sigma_{2}^{2} < 1 $$, <br />
$$ H0: \sigma_{1}^{2}/\sigma_{2}^{2} = 1, \, H1: \sigma_{1}^{2}/\sigma_{2}^{2} \neq 1 $$

검정통계량은 원래 아래와 같지만

$$ F = \frac{s_{1}^{2}/s_{2}^{2}}{\sigma_{1}^{2}/\sigma_{2}^{2}} $$ 

$\sigma_{1}^{2}/\sigma_{2}^{2} = 1$ 이므로, 결과적으로 아래와 같은 검정통계량을 사용한다. 

$$ F = \frac{s_{1}^{2}}{s_{2}^{2}} \sim F_{\alpha}(n_{1}-1, n_{2}-1) $$

마지막으로 분산의 동일성 검정은 아래와 같이 합니다. 

$$ H0: \sigma_{1}^{2}/\sigma_{2}^{2} = 1, \, H1: \sigma_{1}^{2}/\sigma_{2}^{2} > 1 $$일 때, $$ F > F_{\alpha}(n_{1}-1, n_{2}-1)$$이면 H0 기각 <br />
$$ H0: \sigma_{1}^{2}/\sigma_{2}^{2} = 1, \, H1: \sigma_{1}^{2}/\sigma_{2}^{2} < 1 $$일 때, $$ F > F_{1-\alpha}(n_{1}-1, n_{2}-1)$$이면 H0 기각 <br />
$$ H0: \sigma_{1}^{2}/\sigma_{2}^{2} = 1, \, H1: \sigma_{1}^{2}/\sigma_{2}^{2} \neq 1 $$일 때, $$ F > F_{1-\alpha/2}(n_{1}-1, n_{2}-1)$$이면 H0 기각

### 2-2. 모분산이 동일한 경우

우선 두 집단의 모분산이 동일하다고 가정할 경우 아래와 같은 합동분산(pooled variance)를 사용합니다. 

$$ s_{p}^{2} = \frac{(n_{1}-1)s_{1}^{2} + (n_{2}-1)s_{2}^{2}}{n_{1} + n_{2} - 2}$$

검정통계량은 다음과 같습니다. 

$$ t = \frac{( \bar{x}-\bar{y} )-(\mu_{1}-\mu_{2})}{ s_{p} \sqrt{ \frac{1}{n_{1}} + \frac{1}{n_{2} }} } $$

검정은 아래와 같이 합니다. 

$$ H0: \mu_{1} - \mu_{2} = 0, \, H1: \mu_{1} - \mu_{2} > 0 $$일 때, $t > t_{\alpha}(n_{1} + n_{2} - 2)$이면 H0 기각<br />
$$ H0: \mu_{1} - \mu_{2} = 0, \, H1: \mu_{1} - \mu_{2} < 0 $$일 때, $t < -t_{\alpha}(n_{1} + n_{2} - 2)$이면 H0 기각<br />
$$ H0: \mu_{1} - \mu_{2} = 0, \, H1: \mu_{1} - \mu_{2} \neq 0 $$일 때, $ \|t\| > t_{\alpha/2}(n_{1} + n_{2} - 2)$이면 H0 기각

끝으로 신뢰구간은 이렇습니다. 

$$ \bigg( (\bar{x}-\bar{y})-t_{\alpha/2}(n_{1} + n_{2} - 2) \times s_{p} \sqrt{\frac{1}{n_{1}}+ \frac{1}{n_{2}}},  \, (\bar{x}-\bar{y})+t_{\alpha/2}(n_{1} + n_{2} - 2) \times s_{p} \sqrt{\frac{1}{n_{1}}+ \frac{1}{n_{2}}}\bigg) $$


### 2-3. 모분산이 다른 경우

모분산이 다른 경우에는 아래와 같은 검정통계량을 사용합니다. 

$$ t = \frac{( \bar{x}-\bar{y} )-(\mu_{1}-\mu_{2})}{ \sqrt{ \frac{s_{1}^{2}}{n_{1}} + \frac{s_{2}^{2}}{n_{2} }} } $$

그리고 이 때 t는 t분포를 따르게 되는데, 아래의 자유도를 가지게 됩니다. 이를 새터스웨이트(Satterthwaite) 자유도라고 합니다.

$$ v = \frac{ (   s_{1}^{2}/n_{1} + s_{2}^{2}/n_{2}   )^{2}  }{  \frac{(s_{1}^{2}/n_{1})^{2}}{n_{1}-1} + \frac{(s_{2}^{2}/n_{2})^{2}}{n_{2}-1}   } $$

신뢰구간은 다음과 같습니다. 

$$ \bigg( (\bar{x}-\bar{y})-t_{\alpha/2}(v) \sqrt{\frac{s_{2}^{2}}{n_{1}}+ \frac{s_{2}^{2}}{n_{2}}},  \, (\bar{x}-\bar{y})+t_{\alpha/2}(v)  \sqrt{\frac{s_{2}^{2}}{n_{1}}+ \frac{s_{2}^{2}}{n_{2}}}\bigg) $$



## 3. 대응표본의 경우(paired t-test)

앞에서는 두 집단에서 추출한 표본으로 검정을 하였습니다. 
하지만 대응표본의 경우 한 집단의 개체를 대상으로 전후 비교를 하는 경우가 있는데요. 
예를 들어 운동화를 비교할 때 각각 다른 사람에게 다른 운동화를 신게하는 것이 아니라, 
한 사람에게 한쪽발에는 A운동화를, 다른 발에는 B운동화를 신게하고 비교하는 것입니다. 
혹은 한 환자에게 A, B 두 종류의 약 모두 먹게하고 비교하는 것입니다. 
<br />

이 경우 $d_{i} = x_{i}-y_{i}$에 대해 검정하며 아래와 같은 검정통계량을 사용합니다. 

$$  t = \frac{\bar{x}}{s_{d}/sqrt{n}} \sim t(n-1)$$


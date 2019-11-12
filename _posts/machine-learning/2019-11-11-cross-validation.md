---
title: "[머신러닝] 교차검증(cross validation)의 개념, 의미" 
categories:
  - machine-learning
tags:
  - machine-learning
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# [머신러닝] 교차검증(cross validation)의 개념, 의미

오늘은 cross validation의 의미를 알아보겠습니다. 
training set, test set이라는 말은 많이 들어보셨죠. 
training set은 모델을 학습시키기 위해 사용하고, 
test set은 모델의 성능을 평가하기 위해 사용합니다. 
그렇다면 valiation set은 왜 필요한 걸까요? 

![figure02](/assets/images/ml/validation/validation02.jpg){: width="500"}

위와 같은 데이터가 있다고 생각해봅시다. 
목표는 우리에게 주어진 저 데이터를 이용해 목적에 맞는 적절한 모형을 만드는 . 

![figure03](/assets/images/ml/validation/validation03.jpg){: width="500"}

자, 모형을 만들어야하므로 학습시킬 데이터가 필요하겠네요. 
그러면 데이터 전체를 training set으로 사용해볼까요? 
위 그림처럼 데이터 전체를 training set으로 학습시키면 모형을 만들수 있습니다. 
하지만 여기서 한가지 문제점이 발생합니다. 
모형은 만들어냈지만, 모형의 성능을 평가할 수 없습니다. 
즉, 생성된 모형이 좋은지 안좋은지 알 수 없다는 거죠.

![figure04](/assets/images/ml/validation/validation04.jpg){: width="500"}

모델의 성능 평가를 위해 데이터를 두 부분으로 나눕니다. 
위 그림처럼 전체 데이터의 일부분을 모형 학습을 위한 tranining set으로 사용하고, 
나머지 부분을 모형 성능 평가를 위한 test set으로 사용합니다. 
하지만 여기서 또 문제점이 발생합니다. 
바로 test set이 모형의 parameter 추정에 영향을 미친다는 것입니다. 
무슨말이냐면, test set이 모형 결정에 영향을 미친다는 것이지요. 
음... test set에 잘 맞으면 좋은거 아닌가요? 라고 생각하실수 있지만, 
우리의 목적은 test set에 잘 적합시키는 것이 아니라, 실제로 사용할 수 있는 모형을 만드는 것입니다. 
test set에 잘 맞더라도 실세계에 적용했을 때 모형 성능이 좋지 않으면 문제가 생기겠죠?

![figure05](/assets/images/ml/validation/validation05.jpg){: width="500"}

그래서 validation set이 필요한 것입니다. 
모형의 parameter 추정에는 validation set을 사용하고, 
실제세계에 해당하는 데이터가 test set인 것입니다. 
즉, training data로 학습시키고, validation set으로 parameter 튜닝하고, test set으로 최종 테스트를 하는 것입니다. 

![figure06](/assets/images/ml/validation/validation06.jpg){: width="500"}

그리고 training set을 k등분하고 validation set을 여러번 바꿔가며 반복적으로 시행하는 방법을 k-fold cross validation이라고 합니다. 
위 그림에서는 training set을 3등분했으니 3-fold cross validation이겠네요. 
물론 꼭 저렇게 해야한다는 것은 아니고 
전체 데이터를 k등분한 후 validation set없이 test set 위치를 바꿔가며 테스트 하는 방법 등 여러가지 응용 방법이 존재합니다. 

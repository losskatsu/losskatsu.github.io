---
title: "[딥러닝] 배치(batch) vs 에포크(epoch) vs 반복(iteration)의 차이" 
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

# 배치(batch) vs 에포크(epoch) vs iteration의 차이

딥러닝을 하다보며 에포크(epoch), 배치(batch), 반복(iteration)이라는 단어를 많이 접하게 됩니다. 
그런데 이 단어들이 다 비슷비슷한 느낌이라 처음에는 헷갈릴 수 있는데요. 
이번 포스팅에서는 epoch, batch, iteration의 차이에 대해 알아보겠습니다.

## 1. 사전적 의미

먼저 batch 의 사전적 의미를 보겠습니다. 
batch를 영어사전에 검색하면 아래와 같은 뜻이 나옵니다.
batch 는 일괄적이라는 뜻이 포함되네요. 

> batch
>> (일괄적으로 처리되는) 집단, 무리
>> 한 회분(한 번에 만들어 내는 음식기계 등의 양)
>> (일괄 처리를 위해) 함께 묶다 

다음은 epoch의 사전적 의미를 보겠습니다. 
epoch는 시대라는 뜻으로 batch와는 조금 다른 느낌이 듭니다. 

> epoch
>> (중요한 사건·변화들이 일어난) 시대 (=era)

마지막으로 iteration을 검색해보겠습니다. 
iteration은 '반복'이라는 뜻으로 흔히 반복문할 때 그 반복이라고 생각하시면 이해가 쉬울 것 같습니다.

> iteration
>> (계산·컴퓨터 처리 절차의) 반복


## 2. epoch의 의미 

epoch는 사전적 의미로 시대를 의미한다고 했습니다. 
딥러닝에서 epoch는 전체 트레이닝 셋이 신경망을 통과한 횟수 의미합니다. 
예를 들어, 1-epoch는 전체 트레이닝 셋이 하나의 신경망에 적용되어 순전파와 역전파를 통해 신경망을 한 번 통과했다는 것을 의미합니다. 

## 3. batch의 의미

그렇다면 batch란 정확히 무엇을 의미할까요? 
batch는 전체 트레이닝 데이터 셋을 의미합니다. 
이 때, batch size는 조금 다른 것을 의미하는데, 
전체 트레이닝 데이터 셋을 여러 작은 그룹을 나누었을 때 batch size는 하나의 소그룹에 속하는 데이터 수를 의미합니다. 
전체 트레이닝 셋을 작게 나누는 이유는 트레이닝 데이터를 통째로 신경망에 넣으면 학습 시간이 오래 걸리기 때문입니다.

## 4. iteration의 의미



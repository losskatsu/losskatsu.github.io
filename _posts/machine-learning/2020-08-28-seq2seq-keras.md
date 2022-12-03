---
title: "[딥러닝] LSTM기반의 seq2seq 모형으로 기계 번역하기" 
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

# LSTM기반의 seq2seq 모형으로 기계 번역하기

### 참고링크  

|머신러닝|딥러닝|선형대수|기초통계|최적화|
|:------:|:------:|:------:|:------:|:------:|
|[k-means](https://losskatsu.github.io/machine-learning/kmeans-clustering/)|[신경망이란](https://losskatsu.github.io/machine-learning/dl-basic01/)|[고유값,고유벡터](https://losskatsu.github.io/linear-algebra/eigen/)| [확률변수](https://losskatsu.github.io/statistics/random-variable/) |[컨벡스 셋](https://losskatsu.github.io/machine-learning/convex-set/)|
|[k-최근접이웃](https://losskatsu.github.io/machine-learning/knn/)|[성능함수](https://losskatsu.github.io/machine-learning/dl-basic02/)|[행렬식](https://losskatsu.github.io/linear-algebra/determinant/)| [확률분포](https://losskatsu.github.io/statistics/prob-distribution/) | [컨벡스 함수](https://losskatsu.github.io/machine-learning/convex-function/)|
|[선형회귀](https://losskatsu.github.io/statistics/simple-regression/)|[신경망 학습](https://losskatsu.github.io/machine-learning/dl-basic03/)|[내적](https://losskatsu.github.io/linear-algebra/innerproduct/)| [모집단과 표본](https://losskatsu.github.io/statistics/population-sample/) |[라그랑주 듀얼](https://losskatsu.github.io/machine-learning/dual-function/)|
|[로지스틱회귀](https://losskatsu.github.io/statistics/logistic-regression/) |[교차연결](https://losskatsu.github.io/machine-learning/dl-basic04/) |[기저](https://losskatsu.github.io/linear-algebra/basis/)| [평균과 분산](https://losskatsu.github.io/statistics/mean-vairance/)   | [KKT 조건](https://losskatsu.github.io/machine-learning/kkt/) |
|[릿지,라쏘회귀](https://losskatsu.github.io/machine-learning/l1l2/) |[합성곱 신경망](https://losskatsu.github.io/machine-learning/dl-basic05/) |[랭크, 차원](https://losskatsu.github.io/linear-algebra/rank-dim/)| [공분산, 상관계수](https://losskatsu.github.io/statistics/cov-corr/)  | [ROC 커브](https://losskatsu.github.io/machine-learning/stat-roc-curve/) |
|[의사결정나무](https://losskatsu.github.io/machine-learning/decision-tree/) |[배치, 에포크 차이](https://losskatsu.github.io/machine-learning/epoch-batch/) | [선형변환](https://losskatsu.github.io/linear-algebra/linear-trans/)| [최대가능도추정](https://losskatsu.github.io/statistics/mle/) | [크로스 밸리데이션](https://losskatsu.github.io/machine-learning/cross-validation/) |
|[서포트벡터머신](https://losskatsu.github.io/machine-learning/svm/) | [텐서플로기초(1)](https://losskatsu.github.io/machine-learning/tensorflow-basic01/) |[직교행렬](https://losskatsu.github.io/linear-algebra/orthogonal/) | [베르누이,이항분포](https://losskatsu.github.io/statistics/binomial/)  | [실루엣 스코어](https://losskatsu.github.io/machine-learning/silhouette-score) |
|[원클래스 SVM](https://losskatsu.github.io/machine-learning/oneclass-svm/)  | [텐서플로기초(2)](https://losskatsu.github.io/machine-learning/tensorflow-basic02/)  | [고유값분해](https://losskatsu.github.io/linear-algebra/eigen-decomposition/)| [기하,음이항분포](https://losskatsu.github.io/statistics/geometric-negative/) | |
|[LDA ](https://losskatsu.github.io/machine-learning/lda/) | [seq2seq](https://losskatsu.github.io/machine-learning/seq2seq-keras/) | [특이값분해](https://losskatsu.github.io/linear-algebra/svd/) | [초기하분포](https://losskatsu.github.io/statistics/hypergeometric/) | |
|[GMM](https://losskatsu.github.io/machine-learning/gmm/) | [opencv기초](https://losskatsu.github.io/machine-learning/opencv01) | |[포아송분포](https://losskatsu.github.io/statistics/poisson/) | |
|[부스팅](https://losskatsu.github.io/machine-learning/boosting/) | [resnet](https://losskatsu.github.io/machine-learning/resnet) | | [정규분포](https://losskatsu.github.io/statistics/normaldist/) | |
|[사이킷런 실습](https://losskatsu.github.io/machine-learning/sklearn/) |[다각형내부판별](https://losskatsu.github.io/machine-learning/py-polygon01) | |[감마분포](https://losskatsu.github.io/statistics/gammadist/) | |
| | [엣지판별](https://losskatsu.github.io/machine-learning/edge-detect-canny) | | [지수분포](https://losskatsu.github.io/statistics/exponentialdist/) | |
| | | | [카이제곱분포](https://losskatsu.github.io/statistics/chisquareddist/) | |
| | | | [베타분포](https://losskatsu.github.io/statistics/betadist/) | |
| | | | [균일분포](https://losskatsu.github.io/statistics/uniformdist/) | |


<br/>

<a href="http://www.yes24.com/Product/Goods/97032765" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00001_ml.png" width="800" align="middle">

<br/>


본 포스팅은 [케라스 홈페이지](https://blog.keras.io/a-ten-minute-introduction-to-sequence-to-sequence-learning-in-keras.html)를 참고했습니다. 

## trivial 케이스

인풋 시퀀스와 아웃풋 시퀀스의 길이가 같은 경우입니다. 이 경우, 인풋 시퀀스의 길이 정보가 필수적으로 필요합니다.

## General 케이스

일반적인 케이스에서는 인풋 시퀀스와 아웃풋 시퀀스의 길이가 다르고, 
타겟을 예측하기 위해 인풋 시퀀스 전체가 요구됩니다. 
이 방법은 좀 더 어드밴스드 셋업을 요구합니다. 

## seq2seq 작동 원리

(1) 인코더: 인풋 시퀀스를 처리하고 그것의 내부상태를 return 합니다. 
여기서 주목해야 할 사실은 인코더 RNN의 아웃풋은 버리고 오직 상태(state)를 복구한다는 사실입니다. 
이 상태(state)는 context 역할을 하며 디코더 스텝으로 전달됩니다. 

(2) 디코더: 타겟 시퀀스의 이전 문자가 주어졌을때, 디코더는 타겟 시퀀스의 바로 다음 문자를 예측하도록 학습됩니다. 
디코더는 타겟 시퀀스를 같은 시퀀스로 변하게 학습되지만 1 step 미래로 offset하는데 이러한 학습과정을 교사강요(teacher forcing)이라고 부릅니다. 
이때 중요한 것은 인코더(디코더 아닌가?)는 인코더의 상태벡터를 초기벡터로 사용합니다. 
이것이 디코더가 어떤 문자를 생성할 것인지에 대한 정보를 얻는 방법입니다. 
인풋 시퀀스가 주어졌을 때 디코더는 타겟값 (...t)가 주어졌을떄 타겟값 (t+1,...)을 예측하도록 학습됩니다. 

## 추론 모드(inference mode)

추론 모드, 즉, 알려지지 않은 인풋 시퀀스에 대해 디코드 할 때는 약간 다른 과정을 거집니다. 

(1) 인풋 시퀀스를 상태벡터로 인코드합니다. 

(2) size 1 의 타겟 시퀀스로 시작합니다( 단지 start-of-sequence 문자입니다.) 

(3) 다음 문자를 예측하기 위해 디코더에 상태벡터와 1-char 타겟 시퀀스를 넣습니다. 

(4) 이러한 예측법으로 다음 문자를 샘플링합니다.(we simpy use argmax) 

(5) 뽑힌 문자를 타겟 시퀀스에 추가합니다. 

(6) eos가 나오거나 문자 한계치에 도달할 때까지 반복합니다. 

## 케라스 예제

아래 예제는 문자-문자 모형인데, 이포스팅 가장 아래에 단어-단어 모형이 있고, 일반적으로 단어-단어 모형이 더 많이 쓰입니다. 

(1) 해당 문장이 3 numpy array가 됩니다. 
encoder_input_data: 3D array of shape
(num_pairs, max_english_sentence_length, num_english_characters)  
영어문장을 원-핫 벡터화 시킨 것입니다. 

decoder_input_data: 3D array of shape 
(num_pairs, max_korean_sentence_length, num_korean_characters)  
한글 문장을 원-핫 벡터화 시킨 것입니다.

decoder_target_data: decoder_input_data와 같지만 1-step offset 되어 있습니다. 
decoder_target_data[:,t,:]는 decoder_input_data[:,t+1,:]과 같다. 

(2) encoder_input_data와 decoder_input_data가 주어졌을 때, 
LSTM기반의 seq2seq 모형을 예측합니다. 우리 모형은 교사 강요를 사용합니다. 

(3) 모형이 제대로 작동되는지 확인하기 위해 어떤 문장을 디코딩 해봅니다. 
즉, encoder_input_data의 샘플이 대응하는 decoder_target_data로 변하는지 확인합니다. 

<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>

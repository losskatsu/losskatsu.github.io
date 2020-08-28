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


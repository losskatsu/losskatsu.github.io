---
title: "텐서플로 튜토리얼(2)-회귀분석" 
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

# 텐서플로 튜토리얼(2)-회귀분석


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


본 포스팅은 [텐서플로 튜토리얼](https://www.tensorflow.org/tutorials/keras/regression?hl=ko)과 동일한 내용입니다. 

## import 라이브러리 

```python
from __future__ import absolute_import, division, print_function, unicode_literals, unicode_literals

import pathlib

import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns

import tensorflow as tf
from tensorflow import keras
from tensorflow.keras import layers

print(tf.__version__)
```
```text
2.0.0
```

```python
dataset_path = keras.utils.get_file("auto-mpg.data", "http://archive.ics.uci.edu/ml/machine-learning-databases/auto-mpg/auto-mpg.data")
dataset_path
```
```text
Downloading data from http://archive.ics.uci.edu/ml/machine-learning-databases/auto-mpg/auto-mpg.data
32768/30286 [================================] - 0s 5us/step
'C:\\Users\\Cheolwon\\.keras\\datasets\\auto-mpg.data'
```

```python
column_names = ['MPG','Cylinders','Displacement','Horsepower','Weight',
                'Acceleration', 'Model Year', 'Origin']
raw_dataset = pd.read_csv(dataset_path, names=column_names,
                      na_values = "?", comment='\t',
                      sep=" ", skipinitialspace=True)

dataset = raw_dataset.copy()
dataset.tail()
```

<center><img src="/assets/images/ml/dl/basic-tensorflow/basic02/01.JPG" width="500"></center>

```python
dataset.isna().sum()
```
```text
MPG             0
Cylinders       0
Displacement    0
Horsepower      6
Weight          0
Acceleration    0
Model Year      0
Origin          0
dtype: int64
```

```python
dataset = dataset.dropna()
```
```python
origin = dataset.pop('Origin')
```
```python
dataset['USA'] = (origin == 1)*1.0
dataset['Europe'] = (origin == 2)*1.0
dataset['Japan'] = (origin == 3)*1.0
dataset.tail()
```

<center><img src="/assets/images/ml/dl/basic-tensorflow/basic02/02.JPG" width="500"></center>

```python
train_dataset = dataset.sample(frac=0.8,random_state=0)
test_dataset = dataset.drop(train_dataset.index)
```
```python
sns.pairplot(train_dataset[["MPG", "Cylinders", "Displacement", "Weight"]], diag_kind="kde")
```

<center><img src="/assets/images/ml/dl/basic-tensorflow/basic02/03.JPG" width="500"></center>

```python
train_stats = train_dataset.describe()
train_stats.pop("MPG")
train_stats = train_stats.transpose()
train_stats
```
<center><img src="/assets/images/ml/dl/basic-tensorflow/basic02/04.JPG" width="500"></center>

```python
train_labels = train_dataset.pop('MPG')
test_labels = test_dataset.pop('MPG')
```
```python
def norm(x):
    return (x - train_stats['mean']) / train_stats['std']
normed_train_data = norm(train_dataset)
normed_test_data = norm(test_dataset)
```
```python
def build_model():
    model = keras.Sequential([
        layers.Dense(64, activation='relu', input_shape=[len(train_dataset.keys())]),
        layers.Dense(64, activation='relu'),
        layers.Dense(1)
    ])

    optimizer = tf.keras.optimizers.RMSprop(0.001)

    model.compile(loss='mse',
                optimizer=optimizer,
                metrics=['mae', 'mse'])
    return model
```
```python
model = build_model()
```
```python
model.summary()
```
```text
Model: "sequential"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
dense (Dense)                (None, 64)                640       
_________________________________________________________________
dense_1 (Dense)              (None, 64)                4160      
_________________________________________________________________
dense_2 (Dense)              (None, 1)                 65        
=================================================================
Total params: 4,865
Trainable params: 4,865
Non-trainable params: 0
_________________________________________________________________
```

```python
example_batch = normed_train_data[:10]
example_result = model.predict(example_batch)
example_result
```
```text
WARNING:tensorflow:Falling back from v2 loop because of error: Failed to find data adapter that can handle input: <class 'pandas.core.frame.DataFrame'>, <class 'NoneType'>
array([[ 0.06245446],
       [ 0.02115527],
       [ 0.13023175],
       [ 0.10740937],
       [ 0.03407659],
       [ 0.03584604],
       [ 0.06583143],
       [-0.02276877],
       [ 0.09479404],
       [ 0.4227924 ]], dtype=float32)
```

```python
# 에포크가 끝날 때마다 점(.)을 출력해 훈련 진행 과정을 표시합니다
class PrintDot(keras.callbacks.Callback):
    def on_epoch_end(self, epoch, logs):
        if epoch % 100 == 0: print('')
        print('.', end='')

EPOCHS = 1000

history = model.fit(
  normed_train_data, train_labels,
  epochs=EPOCHS, validation_split = 0.2, verbose=0,
  callbacks=[PrintDot()])
```
```text
WARNING:tensorflow:Falling back from v2 loop because of error: Failed to find data adapter that can handle input: <class 'pandas.core.frame.DataFrame'>, <class 'NoneType'>

....................................................................................................
....................................................................................................
....................................................................................................
....................................................................................................
....................................................................................................
....................................................................................................
....................................................................................................
....................................................................................................
....................................................................................................
....................................................................................................
```

```python
hist = pd.DataFrame(history.history)
hist['epoch'] = history.epoch
hist.tail()
```

seq  | loss |	mae |	mse |	val_loss	| val_mae |	val_mse	| epoch
-----|------|-----|-----|------------|-------|----------|----------
995 |	2.289433 |	0.994390 |	2.289433 |	9.913252 |	2.445295 |	9.913252 |	995
996 |	2.515076 |  1.011410 |	2.515076 |	9.837109 |	2.418498 |	9.837110 |	996
997 |	2.291175 |	0.951902 |	2.291175 |	9.417823 |	2.379304 |	9.417823 |	997
998 |	2.391673 |	0.990138 |	2.391673 |	9.346193 |	2.254582 |	9.346193 |	998
999 |	2.451552 |	0.980501 |	2.451552 |	9.323985 |	2.291088 |	9.323984 |	999


```python
import matplotlib.pyplot as plt

def plot_history(history):
    hist = pd.DataFrame(history.history)
    hist['epoch'] = history.epoch

    plt.figure(figsize=(8,12))

    plt.subplot(2,1,1)
    plt.xlabel('Epoch')
    plt.ylabel('Mean Abs Error [MPG]')
    plt.plot(hist['epoch'], hist['mae'],
           label='Train Error')
    plt.plot(hist['epoch'], hist['val_mae'],
           label = 'Val Error')
    plt.ylim([0,5])
    plt.legend()

    plt.subplot(2,1,2)
    plt.xlabel('Epoch')
    plt.ylabel('Mean Square Error [$MPG^2$]')
    plt.plot(hist['epoch'], hist['mse'],
           label='Train Error')
    plt.plot(hist['epoch'], hist['val_mse'],
           label = 'Val Error')
    plt.ylim([0,20])
    plt.legend()
    plt.show()

plot_history(history)
```

<center><img src="/assets/images/ml/dl/basic-tensorflow/basic02/05.JPG" width="500"></center>

```python
model = build_model()

# patience 매개변수는 성능 향상을 체크할 에포크 횟수입니다
early_stop = keras.callbacks.EarlyStopping(monitor='val_loss', patience=10)

history = model.fit(normed_train_data, train_labels, epochs=EPOCHS,
                    validation_split = 0.2, verbose=0, callbacks=[early_stop, PrintDot()])

plot_history(history)
```
<center><img src="/assets/images/ml/dl/basic-tensorflow/basic02/06.JPG" width="500"></center>

```python
loss, mae, mse = model.evaluate(normed_test_data, test_labels, verbose=2)

print("테스트 세트의 평균 절대 오차: {:5.2f} MPG".format(mae))
```
```text
WARNING:tensorflow:Falling back from v2 loop because of error: Failed to find data adapter that can handle input: <class 'pandas.core.frame.DataFrame'>, <class 'NoneType'>
78/78 - 0s - loss: 6.4118 - mae: 2.0169 - mse: 6.4118
테스트 세트의 평균 절대 오차:  2.02 MPG
```
```python
test_predictions = model.predict(normed_test_data).flatten()

plt.scatter(test_labels, test_predictions)
plt.xlabel('True Values [MPG]')
plt.ylabel('Predictions [MPG]')
plt.axis('equal')
plt.axis('square')
plt.xlim([0,plt.xlim()[1]])
plt.ylim([0,plt.ylim()[1]])
_ = plt.plot([-100, 100], [-100, 100])
```
<center><img src="/assets/images/ml/dl/basic-tensorflow/basic02/07.JPG" width="500"></center>

```python
error = test_predictions - test_labels
plt.hist(error, bins = 25)
plt.xlabel("Prediction Error [MPG]")
_ = plt.ylabel("Count")
```

<center><img src="/assets/images/ml/dl/basic-tensorflow/basic02/08.JPG" width="500"></center>


<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>


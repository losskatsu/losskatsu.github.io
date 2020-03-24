---
title: "텐서플로 튜토리얼(1)-기본 이미지 분류" 
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

# 텐서플로 튜토리얼(1)-기본 이미지 분류

본 포스팅은 [텐서플로 튜토리얼](https://www.tensorflow.org/tutorials/keras/classification?hl=ko)과 동일한 내용입니다. 

## import 라이브러리

```python
from __future__ import absolute_import, division, print_function, unicode_literals, unicode_literals

# tensorflow와 tf.keras를 임포트합니다
import tensorflow as tf
from tensorflow import keras

import numpy as np
import matplotlib.pyplot as plt

print(tf.__version__)
```
```text
2.0.0
```

## train, test 분리

```python
fashion_mnist = keras.datasets.fashion_mnist

(train_images, train_labels), (test_images, test_labels) = fashion_mnist.load_data()
```
```text
Downloading data from https://storage.googleapis.com/tensorflow/tf-keras-datasets/train-labels-idx1-ubyte.gz
32768/29515 [=================================] - 0s 3us/step
Downloading data from https://storage.googleapis.com/tensorflow/tf-keras-datasets/train-images-idx3-ubyte.gz
26427392/26421880 [==============================] - 10s 0us/step
Downloading data from https://storage.googleapis.com/tensorflow/tf-keras-datasets/t10k-labels-idx1-ubyte.gz
8192/5148 [===============================================] - 0s 0us/step
Downloading data from https://storage.googleapis.com/tensorflow/tf-keras-datasets/t10k-images-idx3-ubyte.gz
4423680/4422102 [==============================] - 1s 0us/step
```

## 데이터 확인

```python
class_names = ['T-shirt/top', 'Trouser', 'Pullover', 'Dress', 'Coat',
               'Sandal', 'Shirt', 'Sneaker', 'Bag', 'Ankle boot']
```

아래 결과는 train 데이터는 28x28 이미지가 60,000장 이라는 뜻입니다.

```python
train_images.shape
```
```text
(60000, 28, 28)
```
```python
len(train_labels)
```
```text
60000
```

```python
train_labels
```
```text
array([9, 0, 0, ..., 3, 0, 5], dtype=uint8)
```

```python
test_images.shape
```
```text
(10000, 28, 28)
```

```python
len(test_labels)
```
```text
10000
```

```python
plt.figure()
plt.imshow(train_images[0])
plt.colorbar()
plt.grid(False)
plt.show()
```

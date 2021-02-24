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

### 전체 데이터 모양

<center><img src="/assets/images/ml/dl/basic-tensorflow/basic01/01.JPG" width="500"></center>

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
<center><img src="/assets/images/ml/dl/basic-tensorflow/basic01/02.JPG" width="500"></center>

```python
train_images = train_images / 255.0
test_images = test_images / 255.0
```
```python
plt.figure(figsize=(10,10))
for i in range(25):
    plt.subplot(5,5,i+1)
    plt.xticks([])
    plt.yticks([])
    plt.grid(False)
    plt.imshow(train_images[i], cmap=plt.cm.binary)
    plt.xlabel(class_names[train_labels[i]])
plt.show()
```
<center><img src="/assets/images/ml/dl/basic-tensorflow/basic01/03.JPG" width="500"></center>

```python
model = keras.Sequential([
    keras.layers.Flatten(input_shape=(28, 28)),
    keras.layers.Dense(128, activation='relu'),
    keras.layers.Dense(10, activation='softmax')
])
```

```python
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])
```
```python
model.fit(train_images, train_labels, epochs=5)
```
```text
Train on 60000 samples
Epoch 1/5
60000/60000 [==============================] - 6s 99us/sample - loss: 0.4996 - accuracy: 0.8248
Epoch 2/5
60000/60000 [==============================] - 5s 82us/sample - loss: 0.3755 - accuracy: 0.8634
Epoch 3/5
60000/60000 [==============================] - 5s 80us/sample - loss: 0.3367 - accuracy: 0.8780
Epoch 4/5
60000/60000 [==============================] - 5s 75us/sample - loss: 0.3125 - accuracy: 0.8856
Epoch 5/5
60000/60000 [==============================] - 5s 82us/sample - loss: 0.2943 - accuracy: 0.8913
```

```python
test_loss, test_acc = model.evaluate(test_images,  test_labels, verbose=2)

print('\n테스트 정확도:', test_acc)
```
```text
10000/1 - 1s - loss: 0.2947 - accuracy: 0.8728

테스트 정확도: 0.8728
```

```python
predictions = model.predict(test_images)
```
```python
predictions[0]
```
```text
array([1.6788504e-06, 5.5685239e-09, 8.1212349e-08, 1.3833268e-08,
       1.4137331e-07, 2.8559810e-02, 9.8572048e-07, 2.8257709e-02,
       3.2442263e-06, 9.4317627e-01], dtype=float32)
```

```python
np.argmax(predictions[0])
```
```text
9
```

```python
test_labels[0]
```
```text
9
```

```python
def plot_image(i, predictions_array, true_label, img):
    predictions_array, true_label, img = predictions_array[i], true_label[i], img[i]
    plt.grid(False)
    plt.xticks([])
    plt.yticks([])

    plt.imshow(img, cmap=plt.cm.binary)

    predicted_label = np.argmax(predictions_array)
    if predicted_label == true_label:
        color = 'blue'
    else:
        color = 'red'

    plt.xlabel("{} {:2.0f}% ({})".format(class_names[predicted_label],
                                100*np.max(predictions_array),
                                class_names[true_label]),
                                color=color)

def plot_value_array(i, predictions_array, true_label):
    predictions_array, true_label = predictions_array[i], true_label[i]
    plt.grid(False)
    plt.xticks([])
    plt.yticks([])
    thisplot = plt.bar(range(10), predictions_array, color="#777777")
    plt.ylim([0, 1])
    predicted_label = np.argmax(predictions_array)

    thisplot[predicted_label].set_color('red')
    thisplot[true_label].set_color('blue')
```

```python
i = 0
plt.figure(figsize=(6,3))
plt.subplot(1,2,1)
plot_image(i, predictions, test_labels, test_images)
plt.subplot(1,2,2)
plot_value_array(i, predictions,  test_labels)
plt.show()
```

<center><img src="/assets/images/ml/dl/basic-tensorflow/basic01/04.JPG" width="500"></center>

```python
i = 12
plt.figure(figsize=(6,3))
plt.subplot(1,2,1)
plot_image(i, predictions, test_labels, test_images)
plt.subplot(1,2,2)
plot_value_array(i, predictions,  test_labels)
plt.show()
```
<center><img src="/assets/images/ml/dl/basic-tensorflow/basic01/05.JPG" width="500"></center>

```python
# 처음 X 개의 테스트 이미지와 예측 레이블, 진짜 레이블을 출력합니다
# 올바른 예측은 파랑색으로 잘못된 예측은 빨강색으로 나타냅니다
num_rows = 5
num_cols = 3
num_images = num_rows*num_cols
plt.figure(figsize=(2*2*num_cols, 2*num_rows))
for i in range(num_images):
    plt.subplot(num_rows, 2*num_cols, 2*i+1)
    plot_image(i, predictions, test_labels, test_images)
    plt.subplot(num_rows, 2*num_cols, 2*i+2)
    plot_value_array(i, predictions, test_labels)
plt.show()
```
<center><img src="/assets/images/ml/dl/basic-tensorflow/basic01/06.JPG" width="500"></center>

```python
# 테스트 세트에서 이미지 하나를 선택합니다
img = test_images[0]

print(img.shape)
```
```text
(28, 28)
```

```python
# 이미지 하나만 사용할 때도 배치에 추가합니다
img = (np.expand_dims(img,0))

print(img.shape)
```
```text
(1, 28, 28)
```
```python
predictions_single = model.predict(img)

print(predictions_single)
```
```text
[[1.6788470e-06 5.5685234e-09 8.1212491e-08 1.3833266e-08 1.4137342e-07
  2.8559841e-02 9.8571843e-07 2.8257780e-02 3.2442322e-06 9.4317615e-01]]
```
```python
plot_value_array(0, predictions_single, test_labels)
_ = plt.xticks(range(10), class_names, rotation=45)
```
<center><img src="/assets/images/ml/dl/basic-tensorflow/basic01/07.JPG" width="500"></center>

```python
np.argmax(predictions_single[0])
```
```text
9
```


<br/>

### 잠깐! 선형대수, 머신러닝에 대해 좀 더 자세히 알고 싶다면?

<a href="http://www.yes24.com/Product/Goods/97032765?OzSrank=1"><img src="/assets/images/mybook/book_cover01.JPG" width="100" align="middle"> [선형대수와 통계학으로 배우는 머신러닝 with 파이썬](http://www.yes24.com/Product/Goods/97032765?OzSrank=1)

<br/>

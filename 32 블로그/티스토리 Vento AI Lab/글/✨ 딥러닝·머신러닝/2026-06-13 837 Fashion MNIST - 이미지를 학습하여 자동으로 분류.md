---
title: Fashion MNIST - 이미지를 학습하여 자동으로 분류
type: blog-archive
status: active
created: '2026-06-13'
updated: '2026-08-16'
published: '2026-06-13T19:14:57+09:00'
source: https://agapeuni.tistory.com/837
source_blog: agapeuni.tistory.com
post_id: 837
category: ✨ 딥러닝·머신러닝
tags:
- FashionMNIST
- FashionMNIST분류방법
- Kerasfit메소드정리
- KerasSequential모델
- Keras딥러닝예제
- TensorFlow모델훈련방법
- TensorFlow이미지분류
- TensorFlow초보자가이드
- 딥러닝Callback사용법
- 딥러닝이미지분류실습
body_hash: 91837c826214b5cdd4177f727dce8137404410624b089050996eb00f99205ecb
visibility: private
rag: exclude
---

# Fashion MNIST - 이미지를 학습하여 자동으로 분류

- 원문: https://agapeuni.tistory.com/837
- 게시일: 2026-06-13T19:14:57+09:00
- 분류: ✨ 딥러닝·머신러닝

## 본문

![[03 Attachments/티스토리 Vento AI Lab/837/837-001-파이썬-001_(4).png]]

## 1. Fashion MNIST

Fashion MNIST는 10가지 패션 분류에 대한 28x28 그레일 스케일 이미지이다. 60,000개의 훈련 이미지 데이터셋과 10,000개의 테스트 이미지 셋으로 구성되어 있다. 텐서플로를 이용해 Fashion MNIST 이미지를 학습하여 테스트 이미지를 분류해 본다.

![[03 Attachments/티스토리 Vento AI Lab/837/837-002-2.jpg]]

Fashion MNIST 클래스 라벨

| 라벨 | 클래스이름 |
| --- | --- |
| 0 | 티셔츠/상의 |
| 1 | 바지 |
| 2 | 점퍼 |
| 3 | 드레스 |
| 4 | 코트 |
| 5 | 샌들 |
| 6 | 셔츠 |
| 7 | 운동화 |
| 8 | 가방 |
| 9 | 앵클 부츠 |

****

## 2. Tensorflow 코드

Tensorflow 코드로 데이터를 준비하고 모델을 생성한다.

생성한 모델을 컴파일하고 데이터를 훈련하고 모델을 평가하고 예측한다.

```
import matplotlib.pyplot as plt
import numpy as np
import tensorflow as tf
from keras.datasets import fashion_mnist

# Fashion MNIST 데이터셋 로드
# train_images, test_images: 그레이 스케일 이미지 데이터 배열.
# train_labels, test_labels: 숫자 라벨의 배열.
(train_images, train_labels), (test_images, test_labels) = fashion_mnist.load_data()

# 훈련 이미지와 레이블 60,000개
print(train_images.shape, train_labels.shape)

# 테스트 이미지와 레이블 10,000개
print(test_images.shape, test_labels.shape)

# 5개 테스트 이미지 표시
fig, axs = plt.subplots(1, 5, figsize=(15, 15))
for i in range(5):
    axs[i].imshow(test_images[i])
    axs[i].axis('off')
plt.show()

# 5개 테스트 레이블 표시
print([test_labels[i] for i in range(5)])

# 데이터 전처리
train_images, test_images = train_images / 255.0, test_images / 255.0

# 모델 생성
# Flatten 클래스는 입력 데이터를 1차원으로 변환한다.
model = tf.keras.models.Sequential()
model.add(tf.keras.layers.Flatten(input_shape=(28, 28)))
model.add(tf.keras.layers.Dense(512, activation='relu'))
# model.add(tf.keras.layers.Dense(256, activation='relu'))
# model.add(tf.keras.layers.Dense(128, activation='relu'))
model.add(tf.keras.layers.Dense(10, activation='softmax'))

# 모델 요약
model.summary()

# 모델 컴파일
model.compile(optimizer='adam',  # 옵티마이저(optimizer)는 adam을 사용
              # 손실함수는 sparse_categorical_crossentropy 사용
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])  # 지표(metrics)는 accuracy 지정

# 모델 훈련
model.fit(train_images, train_labels, epochs=10)

# 모델 평가
loss, accuracy = model.evaluate(test_images, test_labels)
print(loss, accuracy)

# 모델 예측
preds = model.predict(test_images)

# 예측값 출력
for i in range(0, 5):
    print(preds[i])

# 가장 높은 값을 갖는 인덱스를 확인
for i in range(0, 5):
    print(np.argmax(preds[i]))
```

****

**실행 결과**

코드를 처음 실행시 훈련 데이터와 테스트 데이터를 다운로드 한다.

다음 실행시에는 로컬에 데이터를 확인하고 다운로드를 스킵한다.

다운로드한 테스트 이미지 5개 표시한다.

- 9 앵클 부츠

- 2 점퍼

- 1 바지

- 1 바지

- 6 셔츠

![[03 Attachments/티스토리 Vento AI Lab/837/837-003-image.png]]

훈련을 마치친 딥러닝 예측값과 테스트 데이터 라벨값이 일치한다.

- 테스트 데이터 라벨값 : [9, 2, 1, 1, 6]

- 학습한 딥러닝 예측값 : 9, 2

모델을 훈련하는 Epoch 단계마다 손실(loss)와 정확도(accuracy)를 표시하고 있는데 훈련할수록 정확도가 향상한다.

```
Downloading data from https://storage.googleapis.com/tensorflow/tf-keras-datasets/train-labels-idx1-ubyte.gz
29515/29515 [==============================] - 0s 0us/step
Downloading data from https://storage.googleapis.com/tensorflow/tf-keras-datasets/train-images-idx3-ubyte.gz
26421880/26421880 [==============================] - 2s 0us/step
Downloading data from https://storage.googleapis.com/tensorflow/tf-keras-datasets/t10k-labels-idx1-ubyte.gz
5148/5148 [==============================] - 0s 0s/step
Downloading data from https://storage.googleapis.com/tensorflow/tf-keras-datasets/t10k-images-idx3-ubyte.gz
4422102/4422102 [==============================] - 0s 0us/step

(60000, 28, 28) (60000,)
(10000, 28, 28) (10000,)
[9, 2, 1, 1, 6]

Model: "sequential"
_________________________________________________________________
 Layer (type)                Output Shape              Param #
=================================================================
 flatten (Flatten)           (None, 784)               0

 dense (Dense)               (None, 512)               401920

 dense_1 (Dense)             (None, 10)                5130

=================================================================
Total params: 407050 (1.55 MB)
Trainable params: 407050 (1.55 MB)
Non-trainable params: 0 (0.00 Byte)
_________________________________________________________________
Epoch 1/10
1875/1875 [==============================] - 18s 9ms/step - loss: 0.4722 - accuracy: 0.8319
Epoch 2/10
1875/1875 [==============================] - 19s 10ms/step - loss: 0.3594 - accuracy: 0.8682
Epoch 3/10
1875/1875 [==============================] - 17s 9ms/step - loss: 0.3217 - accuracy: 0.8815
Epoch 4/10
1875/1875 [==============================] - 26s 14ms/step - loss: 0.2989 - accuracy: 0.8891
Epoch 5/10
1875/1875 [==============================] - 21s 11ms/step - loss: 0.2811 - accuracy: 0.8968
Epoch 6/10
1875/1875 [==============================] - 19s 10ms/step - loss: 0.2657 - accuracy: 0.9009
Epoch 7/10
1875/1875 [==============================] - 19s 10ms/step - loss: 0.2539 - accuracy: 0.9048
Epoch 8/10
1875/1875 [==============================] - 20s 10ms/step - loss: 0.2421 - accuracy: 0.9088
Epoch 9/10
1875/1875 [==============================] - 19s 10ms/step - loss: 0.2329 - accuracy: 0.9119
Epoch 10/10
1875/1875 [==============================] - 19s 10ms/step - loss: 0.2225 - accuracy: 0.9146
313/313 [==============================] - 1s 4ms/step - loss: 0.3442 - accuracy: 0.8768
0.34420648217201233 0.876800000667572
313/313 [==============================] - 1s 3ms/step
[2.4046892e-06 6.9541511e-10 4.5498091e-10 6.7821374e-12 8.3896035e-10
 1.7473153e-03 6.4839050e-08 4.9535059e-03 3.4041239e-09 9.9329668e-01]
[1.0605012e-05 1.7392545e-12 9.9030238e-01 1.6595583e-11 9.3686460e-03
 2.8324842e-12 3.1843327e-04 9.4296951e-15 6.1220619e-11 2.5559533e-14]
[6.1930326e-12 1.0000000e+00 5.2024362e-13 5.7756226e-09 2.0922988e-09
 8.6610600e-21 2.3127609e-11 2.9825179e-26 4.1276092e-14 4.3881592e-20]
[1.32807126e-10 9.99999404e-01 1.35544284e-11 5.72864622e-07
 1.98551788e-08 2.10517572e-16 3.22321170e-09 3.07023562e-20
 4.48044325e-13 1.05374985e-17]
[2.3779535e-01 2.1413905e-06 1.7733654e-02 3.0266074e-03 3.1491283e-03
 3.3050418e-07 7.3826426e-01 3.5127272e-07 2.5385629e-05 2.7805470e-06]
9
2
1
1
6
```

## 3. 보충내용 - fit() 메소드

모델 훈련에서 사용한 fit() 메소드에 대해 좀더 알아보자.

fit() 메소드는 매개변수로 훈련 과정에 원하는 작업을 수행하는 콜백(Callback)을 지정할 수 있다.

훈련을 마치면 훈련 측정값(손실과 정확도)이 담겨있는 History 객체를 반환한다.

그 값으로 matplot을 이용해 그래프로 그릴 수 있다.

```
... (생략) ...

class StopTraining(tf.keras.callbacks.Callback):
  def on_epoch_end(self, epoch, logs={}):
      if logs.get('loss') < 0.3:
          print('stop training.')
          self.model.stop_training = True

callbacks = StopTraining()

history = model.fit(train_images, train_labels, epochs=10, callbacks=[callbacks])

plt.plot(history.history['loss'])
plt.plot(history.history['accuracy'])
plt.xlabel('epoch')
plt.ylabel('val')
plt.show()

... (생략) ...
```

실행하는 과정에서 callbacks에 지정한 StopTtraining으로 인해 loss 값이 0.3 미만일때 훈련을 중지했다.

```
... (생략) ...
Epoch 1/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.4768 - accuracy: 0.8300
Epoch 2/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.3607 - accuracy: 0.8686
Epoch 3/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.3233 - accuracy: 0.8808
Epoch 4/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.2986 - accuracy: 0.8884
stop training.
... (생략) ...
```

![[03 Attachments/티스토리 Vento AI Lab/837/837-004-image.png]]

![[03 Attachments/티스토리 Vento AI Lab/837/837-005-주한길.png]]

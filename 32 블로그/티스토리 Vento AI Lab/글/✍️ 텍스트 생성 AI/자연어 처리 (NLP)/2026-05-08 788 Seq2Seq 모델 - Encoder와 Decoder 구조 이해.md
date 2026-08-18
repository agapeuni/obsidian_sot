---
title: Seq2Seq 모델 - Encoder와 Decoder 구조 이해
type: blog-archive
status: active
created: '2026-05-08'
updated: '2026-08-16'
published: '2026-05-08T21:19:32+09:00'
source: https://agapeuni.tistory.com/788
source_blog: agapeuni.tistory.com
post_id: 788
category: ✍️ 텍스트 생성 AI/자연어 처리 (NLP)
tags:
- Encoder-Decoder
- EncoderDecoder구조
- LSTM
- LSTM번역모델구현
- Seq2Seq개념정리
- TensorFlowNLP실습
- 딥러닝번역모델
- 문자 단위 번역 예제 내용을 기준으로 구성했습니다. 텐서플로Seq2Seq예제
- 문자단위Seq2Seq
- 입력 파일의 TensorFlow Seq2Seq
body_hash: d77e5346eb8d0e25e16b3b04c4ba2a623e84cb9afd2fb3a2b2235efdc3c39f9d
visibility: private
rag: exclude
---

# Seq2Seq 모델 - Encoder와 Decoder 구조 이해

- 원문: https://agapeuni.tistory.com/788
- 게시일: 2026-05-08T21:19:32+09:00
- 분류: ✍️ 텍스트 생성 AI/자연어 처리 (NLP)

## 본문

![[03 Attachments/티스토리 Vento AI Lab/788/788-001-img1.daumcdn.png]]

![[03 Attachments/티스토리 Vento AI Lab/788/788-002-ComfyUI_00001_.png]]

텐서플로 Seq2Seq 모델은 번역, 챗봇, 문장 요약처럼 하나의 순차 데이터를 입력받아 다른 순차 데이터를 출력하는 딥러닝 구조이다. 예를 들어 “I am a student”라는 영어 문장을 입력하면 “나는 학생입니다”라는 한국어 문장을 생성하는 방식이다.

Seq2Seq는 Sequence to Sequence의 줄임말이다. 말 그대로 입력 시퀀스를 출력 시퀀스로 변환하는 모델이다. 여기서 시퀀스란 단어, 문자, 토큰처럼 순서가 중요한 데이터를 의미한다.

초기 자연어 처리 모델에서는 문장을 단순히 단어의 나열로 다루는 경우가 많았다. 하지만 실제 언어는 앞뒤 문맥이 매우 중요하다. “나는 밥을”이라는 문장 뒤에는 “먹었다”, “먹고 있다”, “먹고 싶다”처럼 다양한 표현이 이어질 수 있다. Seq2Seq 모델은 이러한 순서와 문맥을 학습하기 위해 등장한 구조이다.

## Seq2Seq 모델의 기본 개념

Seq2Seq는 크게 두 부분으로 구성된다. 첫 번째는 Encoder, 두 번째는 Decoder이다.

Encoder는 입력 문장을 읽고 핵심 정보를 하나의 문맥 벡터로 압축한다. 예를 들어 영어 문장을 입력받으면 단어의 순서를 따라가며 문장의 의미를 내부 상태로 저장한다.

Decoder는 Encoder가 만든 문맥 벡터를 바탕으로 출력 문장을 하나씩 생성한다. 번역 모델이라면 Decoder는 한국어 단어를 순서대로 예측하면서 최종 문장을 만든다.

쉽게 말하면 Encoder는 “이 문장이 무슨 뜻인지 이해하는 역할”이고, Decoder는 “그 의미를 바탕으로 새로운 문장을 작성하는 역할”이다.

## TensorFlow로 구현하는 간단한 Seq2Seq 예제

아래 코드는 문자 단위의 간단한 Seq2Seq 예제이다.

입력 문장을 받아 출력 문장을 학습하는 구조이며, TensorFlow와 Keras를 사용해 실행할 수 있다.

```
import numpy as np
import tensorflow as tf
from tensorflow.keras.models import Model
from tensorflow.keras.layers import Input, LSTM, Dense

# 예제 데이터
input_texts = ["hello", "hi", "good", "bye"]
target_texts = ["안녕", "안녕", "좋아", "잘가"]

# Decoder 입력과 종료 토큰 추가
target_texts = ["\t" + text + "\n" for text in target_texts]

# 문자 집합 생성
input_chars = sorted(list(set("".join(input_texts))))
target_chars = sorted(list(set("".join(target_texts))))

# 문자 집합 크기 및 최대 시퀀스 길이 계산
num_encoder_tokens = len(input_chars)
num_decoder_tokens = len(target_chars)

# 최대 시퀀스 길이 계산
max_encoder_seq_length = max(len(text) for text in input_texts)
max_decoder_seq_length = max(len(text) for text in target_texts)

# 문자 인덱스 생성
input_token_index = dict((char, i) for i, char in enumerate(input_chars))
target_token_index = dict((char, i) for i, char in enumerate(target_chars))

# 원-핫 인코딩 배열 생성
encoder_input_data = np.zeros(
    (len(input_texts), max_encoder_seq_length, num_encoder_tokens),
    dtype="float32"
)

# Decoder 입력과 타겟 데이터 배열 생성
decoder_input_data = np.zeros(
    (len(input_texts), max_decoder_seq_length, num_decoder_tokens),
    dtype="float32"
)

# Decoder 타겟 데이터 배열 생성
decoder_target_data = np.zeros(
    (len(input_texts), max_decoder_seq_length, num_decoder_tokens),
    dtype="float32"
)

# 원-핫 인코딩 수행
for i, (input_text, target_text) in enumerate(zip(input_texts, target_texts)):
    for t, char in enumerate(input_text):
        encoder_input_data[i, t, input_token_index[char]] = 1.0

    for t, char in enumerate(target_text):
        decoder_input_data[i, t, target_token_index[char]] = 1.0

        if t > 0:
            decoder_target_data[i, t - 1, target_token_index[char]] = 1.0

# 모델 구성
latent_dim = 128

encoder_inputs = Input(shape=(None, num_encoder_tokens))
encoder_lstm = LSTM(latent_dim, return_state=True)
encoder_outputs, state_h, state_c = encoder_lstm(encoder_inputs)

encoder_states = [state_h, state_c]

decoder_inputs = Input(shape=(None, num_decoder_tokens))
decoder_lstm = LSTM(latent_dim, return_sequences=True, return_state=True)

decoder_outputs, _, _ = decoder_lstm(
    decoder_inputs,
    initial_state=encoder_states
)

# 디코더 출력에 Dense 레이어 추가
decoder_dense = Dense(num_decoder_tokens, activation="softmax")
decoder_outputs = decoder_dense(decoder_outputs)

model = Model([encoder_inputs, decoder_inputs], decoder_outputs)

# 모델 컴파일
model.compile(
    optimizer="rmsprop",
    loss="categorical_crossentropy",
    metrics=["accuracy"]
)

# 모델 요약 출력
model.summary()

# 모델 학습
model.fit(
    [encoder_input_data, decoder_input_data],
    decoder_target_data,
    batch_size=2,
    epochs=10,
    validation_split=0.2
)
```

**실행 결과 :**

```
Model: "functional"
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃ Layer (type)                  ┃ Output Shape              ┃         Param # ┃ Connected to               ┃
┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━┩
│ input_layer (InputLayer)      │ (None, None, 9)           │               0 │ -                          │
├───────────────────────────────┼───────────────────────────┼─────────────────┼────────────────────────────┤
│ input_layer_1 (InputLayer)    │ (None, None, 8)           │               0 │ -                          │
├───────────────────────────────┼───────────────────────────┼─────────────────┼────────────────────────────┤
│ lstm (LSTM)                   │ [(None, 128), (None,      │          70,656 │ input_layer[0][0]          │
│                               │ 128), (None, 128)]        │                 │                            │
├───────────────────────────────┼───────────────────────────┼─────────────────┼────────────────────────────┤
│ lstm_1 (LSTM)                 │ [(None, None, 128),       │          70,144 │ input_layer_1[0][0],       │
│                               │ (None, 128), (None, 128)] │                 │ lstm[0][1], lstm[0][2]     │
├───────────────────────────────┼───────────────────────────┼─────────────────┼────────────────────────────┤
│ dense (Dense)                 │ (None, None, 8)           │           1,032 │ lstm_1[0][0]               │
└───────────────────────────────┴───────────────────────────┴─────────────────┴────────────────────────────┘
 Total params: 141,832 (554.03 KB)
 Trainable params: 141,832 (554.03 KB)
 Non-trainable params: 0 (0.00 B)
Epoch 1/10
2/2 ━━━━━━━━━━━━━━━━━━━━ 3s 585ms/step - accuracy: 0.1667 - loss: 1.5567 - val_accuracy: 0.0000e+00 - val_loss: 1.5575
Epoch 2/10
2/2 ━━━━━━━━━━━━━━━━━━━━ 0s 85ms/step - accuracy: 0.3333 - loss: 1.5203 - val_accuracy: 0.2500 - val_loss: 1.5563
Epoch 3/10
2/2 ━━━━━━━━━━━━━━━━━━━━ 0s 83ms/step - accuracy: 0.3333 - loss: 1.4881 - val_accuracy: 0.2500 - val_loss: 1.5557
Epoch 4/10
2/2 ━━━━━━━━━━━━━━━━━━━━ 0s 95ms/step - accuracy: 0.3333 - loss: 1.4569 - val_accuracy: 0.2500 - val_loss: 1.5540
Epoch 5/10
2/2 ━━━━━━━━━━━━━━━━━━━━ 0s 83ms/step - accuracy: 0.3333 - loss: 1.4201 - val_accuracy: 0.2500 - val_loss: 1.5515
Epoch 6/10
2/2 ━━━━━━━━━━━━━━━━━━━━ 0s 82ms/step - accuracy: 0.2500 - loss: 1.3785 - val_accuracy: 0.2500 - val_loss: 1.5479
Epoch 7/10
2/2 ━━━━━━━━━━━━━━━━━━━━ 0s 81ms/step - accuracy: 0.2500 - loss: 1.3351 - val_accuracy: 0.2500 - val_loss: 1.5426
Epoch 8/10
2/2 ━━━━━━━━━━━━━━━━━━━━ 0s 85ms/step - accuracy: 0.2500 - loss: 1.2797 - val_accuracy: 0.2500 - val_loss: 1.5402
Epoch 9/10
2/2 ━━━━━━━━━━━━━━━━━━━━ 0s 79ms/step - accuracy: 0.2500 - loss: 1.2152 - val_accuracy: 0.2500 - val_loss: 1.5465
Epoch 10/10
2/2 ━━━━━━━━━━━━━━━━━━━━ 0s 78ms/step - accuracy: 0.2500 - loss: 1.1560 - val_accuracy: 0.2500 - val_loss: 1.5617
```

## 코드 구조 설명

이 코드는 먼저 입력 문장과 출력 문장을 준비한다. 입력 문장은 영어 단어이고, 출력 문장은 한국어 표현이다. 실제 번역 모델에서는 훨씬 많은 데이터가 필요하지만, 구조를 이해하기 위한 예제로는 충분하다.

Decoder 입력에는 시작 토큰 \t와 종료 토큰 \n을 추가한다. 시작 토큰은 Decoder가 문장 생성을 시작할 위치를 알려주고, 종료 토큰은 문장 생성이 끝났음을 알려준다.

그다음 입력 문자와 출력 문자를 각각 숫자 벡터로 변환한다. 딥러닝 모델은 문자를 직접 이해하지 못하므로, 원-핫 인코딩 방식으로 각 문자를 숫자 배열로 바꾸어야 한다.

Encoder는 LSTM을 사용해 입력 시퀀스를 읽는다. LSTM은 순서가 있는 데이터를 처리하는 순환 신경망 구조이며, 문장의 앞뒤 흐름을 반영할 수 있다.

Decoder 역시 LSTM을 사용한다. 다만 Decoder는 Encoder의 마지막 상태를 초기 상태로 받아 출력 문장을 생성한다. 이것이 Seq2Seq 구조의 핵심이다.

마지막 Dense 계층은 다음에 나올 문자를 확률로 예측한다. 예를 들어 현재까지 “안”을 생성했다면 다음 문자가 “녕”일 확률을 계산하는 식이다.

## Seq2Seq 모델이 중요한 이유

Seq2Seq 모델은 자연어 처리에서 중요한 전환점이 된 구조이다. 이전에는 입력과 출력의 길이가 다르면 처리하기 어려웠다. 하지만 Seq2Seq는 입력 문장과 출력 문장의 길이가 달라도 학습할 수 있다.

이 특징 덕분에 기계 번역, 문장 요약, 챗봇, 음성 인식, 질의응답 시스템 등에 활용되었다.

물론 현재는 Transformer 기반 모델이 Seq2Seq 구조를 대체하거나 확장한 형태로 많이 사용된다. 하지만 Encoder와 Decoder의 개념은 여전히 중요하다. Transformer, T5, BART 같은 모델도 큰 틀에서는 입력을 이해하고 출력을 생성하는 구조를 갖는다.

## 정리

텐서플로 Seq2Seq 코드는 입력 시퀀스를 Encoder가 읽고, Decoder가 새로운 출력 시퀀스를 생성하는 방식으로 동작한다.

핵심은 세 가지이다. 첫째, 문장을 숫자 데이터로 변환해야 한다. 둘째, Encoder는 입력 문장의 의미를 상태 벡터로 압축한다. 셋째, Decoder는 그 상태를 바탕으로 출력 문장을 순차적으로 생성한다.

Seq2Seq를 이해하면 RNN, LSTM, Attention, Transformer 구조를 더 쉽게 이해할 수 있다. 특히 자연어 처리와 LLM 구조를 공부하는 입장에서는 Encoder와 Decoder의 역할을 먼저 잡아두는 것이 중요하다.

![[03 Attachments/티스토리 Vento AI Lab/788/788-003-주한길.png]]

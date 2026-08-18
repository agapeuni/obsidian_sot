---
title: 자연어 처리(NLP) - Word2Vec 와 Sentence-Transformers
type: blog-archive
status: active
created: '2026-05-10'
updated: '2026-08-16'
published: '2026-05-10T02:46:44+09:00'
source: https://agapeuni.tistory.com/812
source_blog: agapeuni.tistory.com
post_id: 812
category: ✍️ 텍스트 생성 AI/자연어 처리 (NLP)
tags:
- NLP임베딩가이드
- RAG임베딩전략
- SentenceTransformers비교
- Word2Vec비교
- 단어임베딩개념
- 문장유사도계산
- 문장임베딩활용
- 의미기반검색방법
- 자연어처리벡터화
- 텍스트벡터화방법
body_hash: 44df1f55244a9c518b40c53fc7a45da0f069c480d146667d0bf408119da2d7fd
visibility: private
rag: exclude
---

# 자연어 처리(NLP) - Word2Vec 와 Sentence-Transformers

- 원문: https://agapeuni.tistory.com/812
- 게시일: 2026-05-10T02:46:44+09:00
- 분류: ✍️ 텍스트 생성 AI/자연어 처리 (NLP)

## 본문

![[03 Attachments/티스토리 Vento AI Lab/812/812-001-img1.daumcdn.png]]

자연어 처리(NLP) 분야에서 텍스트 데이터를 벡터화하는 작업은 중요한 작업이다. 텍스트는 인간이 이해하기에 적합한 형태로 존재하지만, 컴퓨터는 이를 바로 이해하거나 처리할 수 없다. 따라서 텍스트를 벡터로 변환하여 수치 데이터로 표현하면 컴퓨터가 언어를 이해하고 분석할 수 있는 기반을 제공하게 된다. 벡터화된 텍스트는 기계 학습 모델에 입력값으로 사용되며, 이를 통해 분류, 군집화, 문장 유사도 계산, 번역, 감정 분석 등 다양한 NLP 작업을 수행할 수 있다.

이 텍스트 벡터화 과정에서 널리 사용되는 두 가지 주요 기법이 바로 Word2Vec과 Sentence-Transformers이다. Word2Vec은 단어 수준에서 텍스트를 벡터로 변환하는 데 중점을 두며, 각 단어를 고정된 크기의 벡터로 표현한다. 이를 통해 단어 간의 의미적 유사성을 수치적으로 표현할 수 있다. 예를 들어, "왕"과 "여왕" 같은 단어는 유사한 벡터 값을 가지며, "남자"와 "여자" 사이의 관계를 벡터 차이로 나타낼 수도 있다. Word2Vec은 주로 단어 간의 관계를 탐구하거나 특정 문맥에서 단어의 의미를 분석하는 데 유용하다.

반면, Sentence-Transformers는 문장 수준에서 텍스트를 벡터로 변환하는 데 초점을 맞추고 있다. 이는 단어 벡터만으로는 복잡한 문장의 의미를 충분히 표현하기 어렵다는 점을 보완한 기법이다. Sentence-Transformers는 문장 전체의 문맥적 의미를 하나의 벡터로 압축하여 표현하며, 이를 통해 문장 간의 유사도를 계산하거나 의미론적 관계를 분석하는 작업이 가능해진다. 특히, 문장이 길어지거나 복잡한 구조를 가질수록 Sentence-Transformers의 장점이 두드러진다.

Word2Vec과 Sentence-Transformers는 각각 고유한 작동 원리를 가지고 있으며, 활용 가능한 상황에서도 차이를 보인다. 단어 수준에서 빠르고 간단한 분석이 필요한 경우 Word2Vec이 적합하고, 문장이나 문단의 복잡한 의미를 이해해야 하는 경우 Sentence-Transformers를 사용하는 것이 좋다. 두 방법의 차이점과 각 기법이 작동하는 방식을 이해해 보자.

## Word2Vec

Word2Vec은 단어 수준에서 텍스트를 벡터화하는 데 사용되는 기법으로, 2013년 구글의 연구진에 의해 개발되었다. Word2Vec은 단어를 키워드가 아닌 벡터 공간으로 표현하는 기술이다. 두 가지 주요 모델인 CBOW(Continuous Bag of Words)와 Skip-gram을 통해 단어를 수치화한다. CBOW는 주변 단어에서 중심 단어를 예측하여 대규모 데이터에 효율적이고, Skip-gram은 중심 단어에서 주변 단어를 예측하여 소규모 데이터에 효율적이다.

### 1. Word2Vec의 작동 원리

**CBOW**: 주변 단어(context words)를 입력으로 받아 타깃 단어를 예측. "The cat sat on the [_]"라는 문장에서, "mat"을 예측.

**Skip-gram**: 타깃 단어를 입력으로 받아 주변 단어를 예측. "cat"을 입력으로 받아 "The"와 "sat" 등을 예측.

이 과정에서 Word2Vec은 단어를 고정된 크기의 밀집 벡터(dense vector)로 변환한다. 이 벡터들은 의미적으로 유사한 단어들이 벡터 공간상에서 가까운 위치에 배치되도록 학습된다. "king" - "man" + "woman" = "queen"처럼 단어 간 유사성을 효과적으로 캡처하고 계산량이 비교적 적고 구현이 간단하다.

### 2. Word2Vec의 한계

- 문맥(context)을 고려하지 않는다.

- "bank"라는 단어가 "강가"와 "은행" 중 어떤 의미인지 구별할 수 없다.

- 단어 수준에서만 작동하므로 문장이나 문단의 의미를 이해하는 데는 한계가 있다.

### 3. Word2Vec 예제 코드

gensim 라이브러리를 사용하여 단어 임베딩 생성 및 유사도를 계산해 보자.

```
from gensim.models import Word2Vec

# 샘플 데이터: 토큰화된 문장 리스트
sentences = [
    ["Computer", "programming", "learning"],
    ["Natural", "language", "processing", "lesson"],
    ["Word2Vec", "creates", "word", "embeddings"]
]

# Word2Vec 모델 학습
model = Word2Vec(sentences, vector_size=100, window=5, min_count=1, workers=4)

# 특정 단어의 벡터 출력
word_vector = model.wv['language']
print("'language' 벡터 출력:", word_vector)

# 단어 간 유사도 계산
similarity = model.wv.similarity('learning', 'lesson')
print("'language'과 'lesson'의 유사도 :", similarity)

# 가장 유사한 단어 찾기
most_similar = model.wv.most_similar('lesson', topn=3)
print("'lesson'과 가장 유사한 단어 3개:", most_similar)
```

실행 결과

```
'language' 벡터 출력: [ 8.13227147e-03 -4.45733406e-03 -1.06835726e-03  1.00636482e-03
 -1.91113955e-04  1.14817743e-03  6.11386076e-03 -2.02715401e-05
 -3.24596534e-03 -1.51072862e-03  5.89729892e-03  1.51410222e-03
 -7.24261976e-04  9.33324732e-03 -4.92128357e-03 -8.38409644e-04
  9.17541143e-03  6.74942741e-03  1.50285603e-03 -8.88256077e-03
  1.14874600e-03 -2.28825561e-03  9.36823711e-03  1.20992784e-03
  1.49006362e-03  2.40640994e-03 -1.83600665e-03 -4.99963388e-03
  2.32429506e-04 -2.01418041e-03  6.60093315e-03  8.94012302e-03
 -6.74754381e-04  2.97701475e-03 -6.10765442e-03  1.69932481e-03
 -6.92623248e-03 -8.69402662e-03 -5.90020278e-03 -8.95647518e-03
  7.27759488e-03 -5.77203138e-03  8.27635173e-03 -7.24354526e-03
  3.42167495e-03  9.67499893e-03 -7.78544787e-03 -9.94505733e-03
 -4.32914635e-03 -2.68313056e-03 -2.71289347e-04 -8.83155130e-03
 -8.61755759e-03  2.80021061e-03 -8.20640661e-03 -9.06933658e-03
 -2.34046578e-03 -8.63180775e-03 -7.05664977e-03 -8.40115082e-03
 -3.01328895e-04 -4.56429832e-03  6.62717456e-03  1.52716041e-03
 -3.34147573e-03  6.10897178e-03 -6.01328490e-03 -4.65616956e-03
 -7.20750913e-03 -4.33658017e-03 -1.80932996e-03  6.48964290e-03
 -2.77039292e-03  4.91896737e-03  6.90444233e-03 -7.46370573e-03
  4.56485013e-03  6.12697843e-03 -2.95447465e-03  6.62502181e-03
  6.12587947e-03 -6.44348515e-03 -6.76455162e-03  2.53895880e-03
 -1.62381888e-03 -6.06512791e-03  9.49920900e-03 -5.13014663e-03
 -6.55409694e-03 -1.19885204e-04 -2.70142802e-03  4.44400299e-04
 -3.53745813e-03 -4.19330609e-04 -7.08615757e-04  8.22820642e-04
  8.19481723e-03 -5.73670724e-03 -1.65952800e-03  5.57160750e-03]
'language'과 'lesson'의 유사도 : -0.06900333
'lesson'과 가장 유사한 단어 3개: [('creates', 0.17018885910511017), ('processing', 0.13887980580329895), ('language', 0.034764934331178665)]
```

## Sentence-Transformers

**Sentence-Transformers**는 문장 수준에서 텍스트를 벡터화하는 최신 기법으로, BERT(Bidirectional Encoder Representations from Transformers)와 같은 트랜스포머 기반 모델을 확장한 것이다. Sentence-Transformers는 문장, 문단, 혹은 그 이상의 텍스트를 벡터로 변환하는 데 적합하다.

### 1. Sentence-Transformers의 작동 원리

Sentence-Transformers는 **트랜스포머(Transformer)** 구조를 기반으로 하며, **BERT**와 같은 사전 학습(pretrained)된 언어 모델을 사용한다. 문장이나 문단을 입력으로 받아, 해당 입력의 의미를 벡터로 변환한다. **Siamese 네트워크** 구조를 활용해 텍스트 쌍 간의 유사도를 학습한다.

**Sentence-Transformers**는 문맥을 깊이 이해할 수 있고 단어의 위치, 주변 단어, 전체 문장의 구조를 고려한다. 문장, 문단, 심지어 문서 수준의 의미를 효과적으로 표현한다. 텍스트 간 유사도 계산에 매우 적합하며 검색 시스템, 질문-응답 시스템 등에 응용된다.

### 2. Sentence-Transformers의 한계

- 계산량이 Word2Vec에 비해 많다.

- 대규모 데이터셋에서 학습하는 데 시간이 걸린다.

****

### 3. Sentence-Transformers 예제 코드

sentence-transformers 라이브러리를 사용하여 문장 임베딩 생성 및 문장 간 유사도를 계산해 보자.

```
from sentence_transformers import SentenceTransformer, util

# 사전 학습된 모델 로드
model = SentenceTransformer('sentence-transformers/bert-base-nli-mean-tokens')

# 샘플 문장
sentences = [
    "I like machine learning.",
    "Natural language processing is exciting.",
    "Artificial intelligence is the future.",
    "I am a boy.",
    "You are a girl"
]

# 문장 임베딩 생성
embeddings = model.encode(sentences)

# 문장 간 유사도 계산
similarity = util.cos_sim(embeddings[0], embeddings[1])
print(f"문장1과 문장2 유사도: {similarity.item()}")

# 두 문장이 가장 유사한 문장을 찾기
sentence_pairs = [(sentences[i], sentences[j]) for i in range(len(sentences)) for j in range(i+1, len(sentences))]
for i, (s1, s2) in enumerate(sentence_pairs):
    score = util.cos_sim(model.encode(s1), model.encode(s2)).item()
    print(f"'{s1}'와 '{s2}'의 유사도: {score:.4f}")
```

실행 결과

```
문장1과 문장2 유사도: 0.7753481268882751
'I like machine learning.'와 'Natural language processing is exciting.'의 유사도: 0.7753
'I like machine learning.'와 'Artificial intelligence is the future.'의 유사도: 0.4144
'I like machine learning.'와 'I am a boy.'의 유사도: 0.4231
'I like machine learning.'와 'You are a girl'의 유사도: 0.4967
'Natural language processing is exciting.'와 'Artificial intelligence is the future.'의 유사도: 0.4243
'Natural language processing is exciting.'와 'I am a boy.'의 유사도: 0.4092
'Natural language processing is exciting.'와 'You are a girl'의 유사도: 0.4877
'Artificial intelligence is the future.'와 'I am a boy.'의 유사도: 0.3899
'Artificial intelligence is the future.'와 'You are a girl'의 유사도: 0.3587
'I am a boy.'와 'You are a girl'의 유사도: 0.4049
```

## Word2Vec과 Sentence-Transformers의 비교

| 특징 | Word2Vec | Sentence-Transformers |
| --- | --- | --- |
| 단위 | 단어 | 문장, 문단 |
| 문맥 이해 | 없음 | 있음 |
| 학습/추론 속도 | 빠름 | 느림 |
| 응용 분야 | 단어 유사성 계산, 간단한 NLP 태스크 | 문장 유사도 계산, 정보 검색, 질문-응답 |
| 모델 구조 | 신경망 기반의 간단한 구조 | 트랜스포머 기반의 복잡한 구조 |
| 모델 크기 | 작음 | 큼 |
| 활용 사례 | 단어 간 유사도 계산, 클러스터링 및 군집화 | 문장 유사도 검색, 의미 기반 검색, 텍스트 분류, 질문에 대한 적절한 답변 제공. |

![[03 Attachments/티스토리 Vento AI Lab/812/812-002-주한길.png]]

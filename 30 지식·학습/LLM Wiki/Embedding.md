---
title: Embedding
type: concept
status: verified
created: 2026-08-18
updated: 2026-08-18
tags:
  - ai/embedding
  - ai/rag
source_checked: 2026-08-18
visibility: private
rag: include
---

# Embedding

Embedding은 텍스트·이미지·오디오 같은 입력을 의미 비교와 검색에 사용할 수 있는 밀집 벡터로 표현한 것이다.

## RAG에서의 역할

1. 문서 chunk와 질문을 같은 벡터 공간으로 변환한다.
2. cosine similarity, dot product 등의 기준으로 후보를 검색한다.
3. 메타데이터 필터와 reranker를 결합해 최종 근거를 선택한다.

## 모델 선택 기준

- 업무 언어와 도메인 데이터에서의 검색 성능
- 입력 길이와 문서 구조 보존 방식
- 벡터 차원, 저장 비용, 색인 성능
- API·내부망 배포 가능 여부와 데이터 경계
- query/document instruction이나 비대칭 검색 지원 여부

## 운영 주의

- 모델을 변경하면 기존 벡터와 혼용하지 않고 색인을 다시 만든다.
- 임베딩 버전, 전처리, 분할 규칙을 함께 기록한다.
- 유사도가 높다는 사실을 정답이나 권한 허용으로 해석하지 않는다.
- 벡터 검색은 키워드·메타데이터·reranker와 비교 평가한다.

## 실패 패턴

- 평가 없이 인기 모델을 선택한다.
- 표·코드·제목 구조를 파괴한 chunk를 임베딩한다.
- 권한 필터를 생성 단계에서만 적용한다.
- 문서 갱신 후 오래된 벡터를 남겨 중복 근거가 검색된다.

## 출처

- [Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks](https://arxiv.org/abs/1908.10084)
- [Dense Passage Retrieval for Open-Domain Question Answering](https://arxiv.org/abs/2004.04906)

## 관련

- [[RAG]]
- [[Transformer]]
- [[LLM 평가]]

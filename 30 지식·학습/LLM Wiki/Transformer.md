---
title: Transformer
type: concept
status: verified
created: 2026-08-18
updated: 2026-08-18
tags:
  - ai/llm
  - ai/architecture
source_checked: 2026-08-18
visibility: private
rag: include
---

# Transformer

Transformer는 recurrence 없이 attention을 중심으로 토큰 사이의 관계를 계산하는 신경망 아키텍처다. 현대 LLM은 이 구조를 다양한 방식으로 확장해 대규모 사전학습과 생성에 사용한다.

## 핵심 구성

- **Token embedding**: 토큰 ID를 연속 벡터로 변환한다.
- **Position information**: 순서 정보를 모델에 제공한다.
- **Self-attention**: 각 토큰이 다른 토큰을 얼마나 참고할지 계산한다.
- **Feed-forward network**: 토큰별 비선형 변환을 수행한다.
- **Residual connection·normalization**: 깊은 네트워크의 학습을 안정화한다.
- **Masking**: 생성 모델에서 미래 토큰 참조를 제한한다.

## 실무 의미

- 컨텍스트 길이가 늘면 attention의 메모리·연산 비용이 커진다.
- 토크나이저, 위치 표현, attention 구현이 모델의 언어·길이 특성에 영향을 준다.
- 모델 크기만으로 품질을 판단하지 않고 데이터·학습·추론 방식과 함께 평가한다.

## 한계와 실패 사례

- 긴 입력이 모두 동일한 품질로 활용된다고 가정한다.
- attention score를 모델의 충실한 설명으로 오인한다.
- 컨텍스트를 늘리는 것만으로 검색·기억·사실성 문제가 해결된다고 기대한다.

## 출처

- [Attention Is All You Need](https://arxiv.org/abs/1706.03762)

## 관련

- [[LLM 핵심 용어]]
- [[Embedding]]
- [[LLM 애플리케이션 아키텍처]]

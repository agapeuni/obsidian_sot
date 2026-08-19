---
title: RAG
type: concept
status: verified
created: 2026-08-15
updated: 2026-08-18
aliases:
  - Retrieval-Augmented Generation
tags:
  - ai/rag
  - ai/llm
visibility: private
rag: include
source_checked: 2026-08-18
---

# RAG

RAG는 질문과 관련된 외부 지식을 검색해 모델의 컨텍스트에 제공하고, 해당 근거를 바탕으로 답변하게 하는 구조다.

## 처리 흐름

```text
문서 수집 → 정제 → 분할 → 임베딩·색인
질문 → 검색 → 필터 → 재랭킹 → 컨텍스트 구성
→ 생성 → 인용 검증 → 평가
```

## 핵심 설계 결정

- 원본 문서의 신뢰도와 갱신 주기
- 문서 구조를 보존하는 분할 전략
- 벡터·키워드·하이브리드 검색 선택
- 사용자 권한을 검색 단계에서 적용하는 방법
- 재랭킹 모델과 최종 컨텍스트 개수
- 답변 거부 조건과 인용 형식

## 실패 패턴

- 검색 결과가 없는데 모델이 자체 지식으로 답변
- 표·코드·문단 구조를 파괴한 분할
- 오래된 문서와 최신 문서의 충돌
- 문서 접근 권한을 무시한 검색
- 검색 평가는 하지 않고 최종 답변만 평가

## 평가 지표

- Retrieval: Recall@k, Precision@k, MRR, nDCG
- Generation: 정답성, 근거성, 인용 정확성, 완결성
- Operation: 지연시간, 비용, 실패율, 색인 최신성

## 적용 조건

- 답변 근거가 사내 문서나 자주 갱신되는 지식에 있다.
- 원본의 접근 권한과 갱신 주기를 관리할 수 있다.
- 검색 실패 시 답변 거부 또는 수동 탐색 경로가 있다.
- 검색과 생성 품질을 분리해 평가할 데이터가 있다.

## 최소 실험

1. 실제 질문과 정답 근거 문서로 평가셋을 만든다.
2. BM25를 기준선으로 두고 벡터·하이브리드 검색과 비교한다.
3. chunk 크기, overlap, top-k, reranker를 한 번에 하나씩 변경한다.
4. Recall@k와 인용 정확성, 최종 답변 근거성을 함께 측정한다.
5. 권한 밖 문서가 검색되지 않는지 별도 테스트한다.

## 출처

- [Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks](https://arxiv.org/abs/2005.11401)
- [RAGAS: Automated Evaluation of Retrieval Augmented Generation](https://arxiv.org/abs/2309.15217)

## 관련

- [[LLM 평가]]
- [[LLM 애플리케이션 아키텍처]]
- [[LLM 보안]]

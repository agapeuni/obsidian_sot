---
title: RAG
type: concept
status: active
created: 2026-08-15
updated: 2026-08-15
aliases:
  - Retrieval-Augmented Generation
tags:
  - ai/rag
  - ai/llm
visibility: private
rag: include
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

## 관련

- [[LLM 평가]]
- [[LLM 애플리케이션 아키텍처]]
- [[LLM 보안]]


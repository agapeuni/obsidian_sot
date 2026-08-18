---
title: LLM 핵심 용어
type: glossary
status: active
created: 2026-08-15
updated: 2026-08-15
tags:
  - ai/llm
  - knowledge/glossary
visibility: private
rag: include
---

# LLM 핵심 용어

| 용어 | 실무 정의 | 연결 주제 |
|---|---|---|
| Token | 모델이 텍스트를 처리하는 기본 단위 | 비용, 컨텍스트 길이 |
| Tokenizer | 텍스트를 토큰 ID로 변환하는 규칙과 도구 | 다국어, 모델 호환 |
| Embedding | 의미 비교에 사용하는 밀집 벡터 표현 | [[RAG]], 검색, 군집화 |
| Transformer | Attention을 핵심으로 하는 신경망 구조 | LLM 기반 구조 |
| Attention | 입력 토큰 사이의 관련성을 계산하는 메커니즘 | 문맥 처리 |
| Context window | 한 요청에서 모델이 참조할 수 있는 토큰 범위 | 긴 문서, 비용 |
| Temperature | 출력의 확률적 다양성을 조정하는 값 | 재현성, 창의성 |
| Hallucination | 근거가 없거나 사실과 다른 내용을 생성하는 현상 | [[LLM 평가]], [[RAG]] |
| Prompt | 모델에 역할, 목적, 입력, 제약, 출력 형식을 전달하는 지시 | [[프롬프트 엔지니어링]] |
| System prompt | 모델의 기본 역할과 상위 행동 경계를 정의하는 메시지 | Agent, 보안 |
| Structured output | JSON Schema 등 정해진 형식으로 생성한 출력 | API, 자동화 |
| Tool calling | 모델이 외부 함수나 시스템 호출을 구조화해 요청하는 방식 | [[AI Agent]], [[MCP]] |
| RAG | 검색한 외부 근거를 컨텍스트로 제공해 답변하는 구조 | [[RAG]] |
| Reranker | 1차 검색 결과의 관련성을 다시 평가해 순서를 조정하는 모델 | 검색 품질 |
| Fine-tuning | 특정 데이터와 목적에 맞게 모델 파라미터를 추가 학습하는 과정 | 도메인 적응 |
| Quantization | 모델 가중치 정밀도를 낮춰 메모리와 연산량을 줄이는 기법 | 로컬 LLM |
| Agent | 목표를 위해 모델이 도구와 상태를 활용해 여러 단계를 실행하는 시스템 | [[AI Agent]] |
| MCP | 모델과 외부 도구·데이터 연결을 표준화하는 프로토콜 | [[MCP]] |
| Evaluation | 품질, 안전, 비용, 속도를 기준으로 시스템을 측정하는 과정 | [[LLM 평가]] |
| Guardrail | 허용되지 않는 입력·출력·행동을 제한하는 통제 장치 | [[LLM 보안]] |

## 작성 원칙

- 용어는 제품 홍보 문구보다 시스템 동작과 운영 의미를 설명한다.
- 모델·벤더마다 정의가 다른 경우 차이를 별도 노트로 확장한다.
- 최신 기능이나 수치는 출처와 확인 날짜를 기록한다.

## 관련

- [[LLM Wiki]]
- [[LLM 학습 로드맵]]


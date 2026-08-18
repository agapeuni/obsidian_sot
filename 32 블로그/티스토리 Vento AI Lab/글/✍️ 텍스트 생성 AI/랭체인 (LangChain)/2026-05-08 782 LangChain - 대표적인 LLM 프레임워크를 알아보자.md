---
title: LangChain - 대표적인 LLM 프레임워크를 알아보자
type: blog-archive
status: active
created: '2026-05-08'
updated: '2026-08-16'
published: '2026-05-08T21:08:05+09:00'
source: https://agapeuni.tistory.com/782
source_blog: agapeuni.tistory.com
post_id: 782
category: ✍️ 텍스트 생성 AI/랭체인 (LangChain)
tags:
- AI챗봇개발가이드
- LangChainAgent활용
- LangChainRAG구조
- LangChain개념정리
- LangChain활용방법
- LLM서비스개발
- LLM애플리케이션구축
- RAG시스템구현
- StreamlitAI서비스구축
- VectorDB임베딩검색
body_hash: 92e4433f83b10d00e17f304c963d520236f8415e2c5e19dc2c547a964d96d5fa
visibility: private
rag: exclude
---

# LangChain - 대표적인 LLM 프레임워크를 알아보자

- 원문: https://agapeuni.tistory.com/782
- 게시일: 2026-05-08T21:08:05+09:00
- 분류: ✍️ 텍스트 생성 AI/랭체인 (LangChain)

## 본문

![[03 Attachments/티스토리 Vento AI Lab/782/782-001-1.png]]

LLM(Large Language Model)은 단순한 질문-응답 수준을 넘어, 실제 업무 시스템과 결합되는 방향으로 빠르게 발전하고 있다. 그러나 LLM 단독으로는 실시간 데이터 활용, 복잡한 로직 처리, 외부 시스템 연동에 한계가 존재한다.

이러한 한계를 해결하기 위해 등장한 것이 바로 LangChain이다. LangChain은 LLM을 중심으로 다양한 데이터, API, 로직을 연결하여 “실제 서비스 수준의 AI 애플리케이션”을 만들 수 있도록 설계된 프레임워크다.

단순히 모델을 호출하는 것이 아니라,

**검색 → 처리 → 판단 → 응답**의 흐름을 하나의 구조로 설계할 수 있다는 점이 핵심이다.

## LangChain의 핵심 구조

LangChain은 이름 그대로 “Chain(사슬)” 구조를 기반으로 동작한다. 즉, 여러 단계를 연결하여 하나의 작업 흐름을 만든다.

예를 들어 다음과 같은 구조가 가능하다.

사용자 질문 입력 → 관련 문서 검색 → 내용 요약 → 최종 답변 생성

이처럼 하나의 작업을 여러 단계로 나누고, 이를 순차적으로 연결하여 처리하는 방식이 LangChain의 기본 개념이다. 이 구조 덕분에 복잡한 NLP 작업도 비교적 단순한 코드로 구현할 수 있다.

## LangChain 주요 개념 정리

LangChain을 제대로 이해하려면 다음 4가지 개념을 정확히 구분해야 한다.

![[03 Attachments/티스토리 Vento AI Lab/782/782-002-2.jpg]]

[출처] https://www.kdnuggets.com/2023/04/langchain-101-build-gptpowered-applications.html

**첫째, 체인(Chain)**
여러 작업 단계를 순차적으로 연결한 실행 흐름이다.
RAG 구조에서도 “검색 → 생성” 과정이 하나의 체인으로 구성된다.

**둘째, LLM 통합**
LangChain은 GPT 계열, 오픈소스 모델 등 다양한 LLM과 연동된다.
단순 응답을 넘어, 데이터 기반 판단까지 수행할 수 있다.

**셋째, 외부 데이터 연동**
DB, 파일, API 등 외부 데이터를 가져와 LLM 입력으로 활용한다.
이 구조가 바로 RAG(Retrieval-Augmented Generation)의 핵심이다.

**넷째, 에이전트(Agent)**
LLM이 스스로 판단하여 필요한 도구(API, 검색 등)를 선택하고 실행한다.
즉, 단순 응답이 아니라 “행동하는 AI”를 구현하는 구조다.

## LangChain 구성 요소

실제 구현 관점에서 중요한 구성 요소만 정리하면 다음과 같다.

![[03 Attachments/티스토리 Vento AI Lab/782/782-003-0_ETUjwGN50cKRnIqO.webp]]

[출처] https://medium.com/@ai-data-drive/langchain-series-01-what-is-it-dc2ae8db9edd

**1) 프롬프트 템플릿**
입력 구조를 표준화하여 LLM의 출력 품질을 안정화한다.

**2) 체인(Chains)**
여러 단계를 연결하여 복합 작업을 처리한다.

**3) 메모리(Memory)**
대화 문맥을 유지하여 지속적인 인터랙션을 가능하게 한다.

**4) 인덱스(Index)**
문서, 데이터 등을 벡터화하여 검색 가능하도록 만든다.
(실질적으로는 Vector DB + Embedding 구조)

**5) 에이전트(Agents)**
상황에 따라 도구를 선택하고 실행하는 의사결정 엔진이다.

## LangChain의 핵심 기능 (RAG 중심)

LangChain이 실무에서 많이 쓰이는 이유는 다음 기능 때문이다.

**1) 검색(Retrieval)**
외부 데이터에서 필요한 정보를 찾는다.

**2) 임베딩(Embedding)**
텍스트를 벡터로 변환하여 의미 기반 검색을 가능하게 한다.

**3) 유사도 검색(Similarity Search)**
질문과 가장 유사한 데이터를 찾아낸다.

**4) 랭킹(Reranking)**
검색 결과 중 가장 적합한 정보를 선별한다.

**5) 프롬프트 관리**
LLM 입력을 구조화하여 결과 품질을 제어한다.

이 기능들이 결합되면 **RAG 시스템**이 완성된다.

## LangChain 활용 사례 (실제 적용 관점)

LangChain은 다음과 같은 영역에서 바로 적용 가능하다.

- 문서 기반 QA 시스템 : 사내 문서, 매뉴얼, 정책 등을 검색하고 답변하는 시스템

- AI 챗봇 : 대화 문맥을 유지하면서 점점 똑똑해지는 대화형 시스템

- 자동 의사결정 시스템 : 데이터 분석 → 판단 → 결과 생성까지 자동화

- API 통합 서비스 : 외부 서비스와 연동하여 실시간 데이터 기반 응답 제공

## LangChain의 장점 (왜 쓰는가)

- 모듈성 : 필요한 기능만 조합하여 구조를 설계할 수 있다

- 확장성 : 외부 데이터와 쉽게 연결되어 실시간 정보 활용이 가능하다

- 자동화 : 에이전트를 통해 반복 작업을 자동으로 수행할 수 있다

결론적으로, LangChain은 “LLM을 서비스화하기 위한 표준 구조”에 가깝다.

## LLM 사용을 위한 필수 요소

LLM을 실제로 사용하려면 API 접근이 필요하다.

대표적으로

- OpenAI

- Hugging Face

이 두 플랫폼에서 API 키를 발급받아 사용할 수 있다.

다만, 온프레미스 환경에서는 Ollama, vLLM 같은 로컬 서빙 구조를 사용하는 것이 일반적이다.

## 스트림릿(Streamlit)

빠른 UI 구축 도구

프로토타입이나 내부 서비스 UI를 빠르게 만들고 싶다면 Streamlit을 활용하는 것이 효율적이다.

파이썬 코드 몇 줄로 웹 UI를 만들 수 있으며, RAG 결과를 바로 시각화하거나 데모 시스템을 구축하는 데 적합하다.

## 정리

LangChain은 단순한 라이브러리가 아니라 LLM 기반 시스템을 설계하는 아키텍처 프레임워크다.

특히 다음과 같은 구조를 이해하는 것이 핵심이다.

LLM 단독 → 한계 존재
LLM + LangChain → 서비스 수준 확장

앞으로 AI 서비스 개발의 핵심은 “모델 성능”이 아니라 “구조 설계”가 될 가능성이 높다.

LangChain은 그 구조를 가장 빠르게 구현할 수 있는 실질적인 도구다.

![[03 Attachments/티스토리 Vento AI Lab/782/782-004-주한길.png]]

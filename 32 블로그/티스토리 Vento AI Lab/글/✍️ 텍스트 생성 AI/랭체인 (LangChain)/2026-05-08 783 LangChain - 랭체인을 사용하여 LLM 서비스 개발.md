---
title: LangChain - 랭체인을 사용하여 LLM 서비스 개발
type: blog-archive
status: active
created: '2026-05-08'
updated: '2026-08-16'
published: '2026-05-08T21:08:50+09:00'
source: https://agapeuni.tistory.com/783
source_blog: agapeuni.tistory.com
post_id: 783
category: ✍️ 텍스트 생성 AI/랭체인 (LangChain)
tags:
- LangChainOllama연동
- LLM서비스구축가이드
- ollama
- 랭체인사용법
- 랭체인프롬프트템플릿
- 메모리
- 외부 도구 통합 내용을 기준으로 구성했습니다. LangChainLLM개발
- 입력 파일의 LangChain
- 체이닝
- 프롬프트 템플릿
body_hash: fa6a83a26a8bd0e04cbd006b19976127f4bbaa6fd5239f0fffb96d45150e292a
visibility: private
rag: exclude
---

# LangChain - 랭체인을 사용하여 LLM 서비스 개발

- 원문: https://agapeuni.tistory.com/783
- 게시일: 2026-05-08T21:08:50+09:00
- 분류: ✍️ 텍스트 생성 AI/랭체인 (LangChain)

## 본문

![[03 Attachments/티스토리 Vento AI Lab/783/783-001-img1.daumcdn.png]]

LLM(Large Language Model)은 대규모 데이터를 학습하여 인간의 언어를 이해하고 생성할 수 있는 AI 모델이다. 이 모델은 수십억에서 수조 개의 매개변수를 사용해 텍스트 패턴, 문맥, 의미를 학습하며, 자연어 처리(NLP) 문제를 해결하는 데 뛰어난 성능을 발휘한다. 대표적인 LLM에는 OpenAI의 GPT 시리즈(GPT-3, GPT-4), Google의 PaLM, Meta의 LLaMA 등이 있다.

랭체인(LangChain)은 LLM 애플리케이션을 효율적으로 개발할 수 있도록 돕는 프레임워크다. 랭체인은 LLM을 활용한 애플리케이션 개발을 단순화하고 최적화한다. 랭체인 프레임워크는 전체 애플리케이션 라이프사이클을 지원하며, 다양한 LLM과의 연결, 프롬프트 관리, 체이닝(Chaining), 메모리 관리 등을 통해 강력하고 확장 가능한 AI 애플리케이션을 구축할 수 있다. 랭체인을 사용하여 LLM 서비스 개발하는 과정을 살펴보자.

## 1. 랭체인으로 할 수 있는 것

랭체인을 사용하면 다음과 같은 작업을 수행할 수 있다.

- RAG 기반 질의응답 시스템: 다양한 소스에서 데이터를 검색 및 생성.

- 구조화된 출력 추출: 일관된 데이터 출력 생성.

- 챗봇 제작: 사용자 정의 가능한 대화형 에이전트 개발.

- Streamlit : 사용자와 상호작용이 가능한 애플리케이션 제작 도구.

- LangGraph: 상태 기반의 멀티 액터 애플리케이션을 쉽게 설계 가능.

- LangSmith: 앱 디버깅, 테스트, 모니터링을 지원하는 개발자 플랫폼.

## 2. 환경 설정

- Python 설치: Python 3.11.x 이상 버전을 설치.

- Python 라이브러리 설치: pip install langchain openai

- API 키 설정: Hugging Face 등 사용할 LLM API 키를 환경 변수 또는 코드에 설정.

- LLM 모델 : LLaMa 3.2 (3b) - Ollama에 모델을 등록하여 서비스.

**패키지 설치**

> pip install langchain_ollama

```
(langchain-rag-master) sgkim@3d:~/book/langchain-rag-master$ pip install langchain_ollama

Collecting langchain_ollama
  Downloading langchain_ollama-0.3.7-py3-none-any.whl.metadata (2.1 kB)
Collecting ollama<1.0.0,>=0.5.3 (from langchain_ollama)
  Using cached ollama-0.5.3-py3-none-any.whl.metadata (4.3 kB)
Collecting langchain-core<1.0.0,>=0.3.74 (from langchain_ollama)
  Using cached langchain_core-0.3.75-py3-none-any.whl.metadata (5.7 kB)
Collecting langsmith>=0.3.45 (from langchain-core<1.0.0,>=0.3.74->langchain_ollama)
  Using cached langsmith-0.4.21-py3-none-any.whl.metadata (14 kB)
Collecting tenacity!=8.4.0,<10.0.0,>=8.1.0 (from langchain-core<1.0.0,>=0.3.74->langchain_ollama)
  Using cached tenacity-9.1.2-py3-none-any.whl.metadata (1.2 kB)
Collecting jsonpatch<2.0,>=1.33 (from langchain-core<1.0.0,>=0.3.74->langchain_ollama)
  Using cached jsonpatch-1.33-py2.py3-none-any.whl.metadata (3.0 kB)

... (생략) ...

Using cached zstandard-0.24.0-cp311-cp311-manylinux2014_x86_64.manylinux_2_17_x86_64.whl (5.6 MB)
Using cached anyio-4.10.0-py3-none-any.whl (107 kB)
Using cached sniffio-1.3.1-py3-none-any.whl (10 kB)
Installing collected packages: zstandard, urllib3, typing-inspection, tenacity, sniffio, PyYAML, pydantic-core, orjson, jsonpointer, idna, h11, charset_normalizer, certifi, annotated-types, requests, pydantic, jsonpatch, httpcore, anyio, requests-toolbelt, httpx, ollama, langsmith, langchain-core, langchain_ollama
Successfully installed PyYAML-6.0.2 annotated-types-0.7.0 anyio-4.10.0 certifi-2025.8.3 charset_normalizer-3.4.3 h11-0.16.0 httpcore-1.0.9 httpx-0.28.1 idna-3.10 jsonpatch-1.33 jsonpointer-3.0.0 langchain-core-0.3.75 langchain_ollama-0.3.7 langsmith-0.4.21 ollama-0.5.3 orjson-3.11.3 pydantic-2.11.7 pydantic-core-2.33.2 requests-2.32.5 requests-toolbelt-1.0.0 sniffio-1.3.1 tenacity-9.1.2 typing-inspection-0.4.1 urllib3-2.5.0 zstandard-0.24.0(langchain-rag-master) sgkim@3d:~/book/langchain-rag-master$
```

> pip install langchain

```
(langchain-rag-master) sgkim@3d:~/book/langchain-rag-master$ pip install langchain
Collecting langchain
  Using cached langchain-0.3.27-py3-none-any.whl.metadata (7.8 kB)
Requirement already satisfied: langchain-core<1.0.0,>=0.3.72 in /home/sgkim/.pyenv/versions/3.11.11/envs/langchain-rag-master/lib/python3.11/site-packages (from langchain) (0.3.75)
Collecting langchain-text-splitters<1.0.0,>=0.3.9 (from langchain)
  Using cached langchain_text_splitters-0.3.10-py3-none-any.whl.metadata (1.9 kB)
Requirement already satisfied: langsmith>=0.1.17 in /home/sgkim/.pyenv/versions/3.11.11/envs/langchain-rag-master/lib/python3.11/site-packages (from langchain) (0.4.21)
Requirement already satisfied: pydantic<3.0.0,>=2.7.4 in /home/sgkim/.pyenv/versions/3.11.11/envs/langchain-rag-master/lib/python3.11/site-packages (from langchain) (2.11.7)

... (생략) ...

/home/sgkim/.pyenv/versions/3.11.11/envs/langchain-rag-master/lib/python3.11/site-packages (from httpx<1,>=0.23.0->langsmith>=0.1.17->langchain) (1.0.9)
Requirement already satisfied: h11>=0.16 in /home/sgkim/.pyenv/versions/3.11.11/envs/langchain-rag-master/lib/python3.11/site-packages (from httpcore==1.*->httpx<1,>=0.23.0->langsmith>=0.1.17->langchain) (0.16.0)
Requirement already satisfied: sniffio>=1.1 in /home/sgkim/.pyenv/versions/3.11.11/envs/langchain-rag-master/lib/python3.11/site-packages (from anyio->httpx<1,>=0.23.0->langsmith>=0.1.17->langchain) (1.3.1)
Using cached langchain-0.3.27-py3-none-any.whl (1.0 MB)
Using cached langchain_text_splitters-0.3.10-py3-none-any.whl (34 kB)
Using cached sqlalchemy-2.0.43-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (3.3 MB)
Using cached greenlet-3.2.4-cp311-cp311-manylinux_2_24_x86_64.manylinux_2_28_x86_64.whl (587 kB)
Installing collected packages: greenlet, SQLAlchemy, langchain-text-splitters, langchain
Successfully installed SQLAlchemy-2.0.43 greenlet-3.2.4 langchain-0.3.27 langchain-text-splitters-0.3.10
(langchain-rag-master) sgkim@3d:~/book/langchain-rag-master$
```

## 3. LLM 설정

랭체인을 사용하려면 먼저 사용할 LLM을 설정해야 한다.

```
from langchain.llms import OpenAI

# OpenAI LLM 초기화
llm = OpenAI(model="gpt-4", temperature=0.2)
```

참고로 OpenAI를 사용하려면 비용이 발생한다. OpenAI API는 사용량에 따라 과금되며, GPT-4는 요청된 입력 토큰과 출력 토큰에 대해 비용이 발생한다. 비용은 입력 토큰(Input Token, 사용자가 보낸 텍스트)과 출력 토큰(Output Token, 모델이 생성한 텍스트)에 따라 부과된다.

max_tokens을 설정하여 응답 길이를 제한해 불필요한 비용을 방지하거나 temperature를 조정하여 모델의 응답을 간결하게 조정함으로 비용을 관리할 수 있다.

Ollama에 모델을 설치하고 ChatOllama로 LLM을 초기화 한다.

```
from langchain_ollama import ChatOllama

# ChatOllama LLM 초기화
llm = ChatOllama(model="llama3.2:3b", temperature=0.2)
```

- model: 사용할 모델을 지정.

- temperature: 응답의 창의성을 조정(0: 사실적, 1: 창의적).

## 4. 프롬프트 템플릿 관리

랭체인의 PromptTemplate을 사용하면 프롬프트를 동적으로 생성할 수 있다.

```
from langchain.prompts import PromptTemplate

# 프롬프트 템플릿 정의
template = """
당신은 {role}입니다. 다음 질문에 답변하세요:
질문: {question}
"""
prompt = PromptTemplate(
    input_variables=["role", "question"],
    template=template,
)

# 템플릿 사용
formatted_prompt = prompt.format(role="AI 전문가", question="랭체인은 무엇인가요?")
print(formatted_prompt)
```

```
당신은 AI 전문가입니다. 다음 질문에 답변하세요:
질문: 랭체인은 무엇인가요?
```

## 5. 체이닝(Chaining)

체이닝은 여러 단계를 연결해 복잡한 워크플로를 생성하는 기능이다.

```
from langchain.chains import LLMChain

# 체인을 정의
chain = LLMChain(llm=llm, prompt=prompt)

# 체인 실행
response = chain.run({"role": "AI 도우미", "question": "LLM을 사용하는 방법은?"})
print(response)
```

```
LLM(Large Language Model)을 사용하는 방법에는 다음과 같은 몇 가지가 있습니다.

1. **텍스트 입력**: LLM은 텍스트를 입력받아 ответ을 생성합니다. 예를 들어, "이번 주말에 무엇을 할 수 있을까요?"라는 질문을 입력하면 LLM은 관련된 정보를 제공할 수 있습니다.
2. **문서 분석**: LLM은 문서를 분석하여 특정한 내용이나 정보를 추출할 수 있습니다. 예를 들어, 문서의 주요 키워드를 추출하거나, 문서의 내용을 요약할 수 있습니다.
3. **Natural Language Processing (NLP)**: LLM은 NLP를 사용하여 텍스트 데이터를 처리하고 분석할 수 있습니다. 예를 들어, 텍스트 데이터를 분류하거나, 텍스트 데이터를 전처리할 수 있습니다.
4. **Generative Model**: LLM은 생성 모델로 사용될 수 있으며, 새로운 텍스트를 생성할 수 있습니다. 예를 들어, 소설을 작성하거나, 음악을 작곡할 수 있습니다.
5. **Chatbot**: LLM은 chatbot을 개발하여 사용할 수 있습니다. 예를 들어, 고객 service나 customer support에서 chatbot을 사용할 수 있습니다.

LLM을 사용하는 방법에는 다양한 방법이 있지만, 가장 일반적인 방법은 텍스트 입력을 통해 LLM과 대화하는 것입니다.
```

## 6. 메모리 관리

대화형 애플리케이션에서는 컨텍스트를 유지하기 위해 메모리를 관리해야 한다.

랭체인은 이를 위한 ConversationBufferMemory를 제공한다.

```
from langchain.chains import ConversationChain
from langchain.memory import ConversationBufferMemory

# 메모리 설정
memory = ConversationBufferMemory()

# 대화형 체인 생성
conversation = ConversationChain(llm=llm, memory=memory)

# 대화 진행
response1 = conversation.predict(input="한글로 인사해요. 안녕하세요!")
response2 = conversation.predict(input="한글로 대답해 주세요. 오늘 날씨가 어떤가요?")

print(response1)
print(response2)
```

```
Hello! I recognize the Korean greeting "안녕하세요" (annyeonghaseyo), which literally means "hello" or "good day." It's a common way to greet someone in Korea, especially among friends and acquaintances. In fact, did you know that the word "안녕하세요" is often used as a formal greeting in business settings, similar to how "hello" might be used in English?
The Korean phrase "" (han-gul) literally means "Chinese characters" or "characters from China," which refers to the writing system used in Korea, known as Hangul.

Regarding your question about the weather today, I'm a large language model, I don't have real-time access to current weather conditions. However, I can suggest some ways for you to find out the weather forecast for today. You can check online weather websites such as AccuWeather or Weather.com, which provide up-to-date weather forecasts and conditions for various locations around the world.

Alternatively, if you're in Korea, you can try checking a local news website or app, such as Naver News or KakaoTalk, which often provide current weather updates.
```

## 7. 외부 도구와의 통합

랭체인은 외부 데이터 소스나 API와 통합할 수 있다.

파이썬 함수를 호출하거나 데이터베이스에서 정보를 가져올 수 있다.

```
from langchain.tools import Tool

# 커스텀 도구 정의
def get_weather(location):
    return f"{location}의 날씨는 맑음입니다."

weather_tool = Tool(name="WeatherTool", func=get_weather, description="날씨 정보를 제공합니다.")

# 도구 실행
print(weather_tool.run("용인"))
```

```
용인의 날씨는 맑음입니다.
```

## 8. 참고 자료

- [https://reference.langchain.com/?lang=python](https://reference.langchain.com/?lang=python)

- [https://github.com/langchain-ai/langchain](https://github.com/langchain-ai/langchain)

![[03 Attachments/티스토리 Vento AI Lab/783/783-002-주한길.png]]

---
title: LangChain - Ollama로 구현하는 LLM 서비스
type: blog-archive
status: active
created: '2026-05-08'
updated: '2026-08-16'
published: '2026-05-08T21:09:55+09:00'
source: https://agapeuni.tistory.com/785
source_blog: agapeuni.tistory.com
post_id: 785
category: ✍️ 텍스트 생성 AI/랭체인 (LangChain)
tags:
- FAISS
- FAISS벡터DB구축
- LangChainRetrievalQA
- LLaMA3랭체인연동
- ollama
- Ollama임베딩활용
- PDF 기반 RAG 실습 내용을 기준으로 구성했습니다. LangChainOllamaRAG
- 랭체인PDF질의응답
- 로컬LLM활용방법
- 입력 파일의 LangChain
body_hash: 3162128e5e5780ca1c9e5e0997536dc00eea9c66dcb08d9aa706db36ce9368be
visibility: private
rag: exclude
---

# LangChain - Ollama로 구현하는 LLM 서비스

- 원문: https://agapeuni.tistory.com/785
- 게시일: 2026-05-08T21:09:55+09:00
- 분류: ✍️ 텍스트 생성 AI/랭체인 (LangChain)

## 본문

![[03 Attachments/티스토리 Vento AI Lab/785/785-001-img1.daumcdn.png]]

랭체인을 사용하여 LLM 기반의 AI 서비스를 개발할 때, OpenAI의 언어모델이나 임베딩 모델을 사용하려면 과금을 해야 한다. 서적이나 인터넷 자료를 참조하며 해당 기술을 배우는 시점에서 실행할 때마다 돈을 내야 하는 것은 부담이 될 수 있다.

Ollama를 사용하면 LLM과 Embedding 모델을 무료로 사용할 수 있다. 인터넷 자료나 서적의 코드의 일부를 변경하면 실행하는데 문제가 없다.

## 1. PDF 파일 불러오기

LangChain을 사용하여 "황순원의 소나기(TheCloudburst.pdf)" PDF 파일을 불러와 문서객체로 변환한다. LangChain에서 제공하는 PDF 전용 로더 클래스인 PyPDFLoader를 사용한다.

```
from langchain.document_loaders import PyPDFLoader
loader = PyPDFLoader("../Data/TheCloudburst.pdf")
document = loader.load()
```

document는 PDF의 각 페이지가 분리되어 담긴 Document 객체 리스트가 된다. 첫번째 문서를 출력해 보자.

```
print(document[0].page_content)
```

| '- 1 -\n소나기황순원소년은 개울가에서 소녀를 보자 곧 윤 초시네 증손녀(曾孫女)딸이라는 걸 알 수 있었다. 소녀는 개울에다 손을 잠그고 물장난을 하고 있는 것이다. 서울서는 이런 개울물을 보지 못하기나 한 듯이.벌써 며칠째 소녀는, 학교에서 돌아오는 길에 물장난이었다. 그런데, 어제까지 개울 기슭에서 하더니, 오늘은 징검다리 한가운데 앉아서 하고 있다.소년은 개울둑에 앉아 버렸다. 소녀가 비키기를 기다리자는 것이다.요행 지나가는 사람이 있어, 소녀가 길을 비켜 주었다.다음 날은 좀 늦게 개울가로 나왔다.이 날은 소녀가 징검다리 한가운데 앉아 세수를 하고 있었다. 분홍 스웨터 소매를 걷어올린 목덜미가 마냥 희었다.한참 세수를 하고 나더니, 이번에는 물 속을 빤히 들여다 본다. 얼굴이라도 비추어 보는 것이리라.  ... (생략) ... |
| --- |

첫번째 문서의 메타정보를 표시해본다.

```
print(document[0].metadata)

{'source': '../Data/TheCloudburst.pdf', 'page': 0}
```

## 2. 문장을 벡터로 변경

Ollama 기반의 임베딩 및 LLM 모델을 LangChain에서 사용할 수 있게 해주는 langchain_ollama 패키지를 불러온다. 임베딩 생성 전용 클래스인 OllamaEmbeddings를 사용하여 Ollama에 설치한 "nomic-embed-text:latest" 임베딩 모델을 정의한다. 임베딩 모델을 사용해서 텍스트를 벡터로 변경해 보자.

```
from langchain_ollama import OllamaEmbeddings
embeddings = OllamaEmbeddings(model="nomic-embed-text:latest")

embedding_val = embeddings.embed_query("황순원의 소나기")
print(embedding_val)
```

embeddings 객체를 통해 텍스트를 벡터로 바꿀 수 있다.

| [-0.012877207, 0.012734982, -0.13071358, 0.019070521, -0.0009059934, -0.018864013, 0.01247058, 0.061778475, -0.017505525, -0.029770445, -0.013006447, 0.062609546, 0.05734551, 0.03305325, 0.01170749,  ... (생략) ...  -0.013438395,-0.0044117155, 0.016986763, 0.0067552775, 0.013778783, -0.05561764, 0.007978033, 0.049627554, 0.026359154, 0.010810524, 0.024162639, -0.017452797, -0.024396116, 0.0028539882, -0.07503245, -0.0349145, -0.041117404] |
| --- |

## 3. FAISS에 저장

LangChain에서 제공하는 FAISS 벡터 데이터베이스 모듈을 불러온다. FAISS(Facebook AI Similarity Search)는 고속 유사도 검색을 위한 라이브러리다. 대규모 임베딩 벡터를 빠르게 검색하는 데 최적화되어 있습니다. PDF에서 로드한 각 문서를 임베딩하여 FAISS 벡터 디비에 저장한다.

```
from langchain.vectorstores import FAISS
database = FAISS.from_documents(document, embeddings)
```

FAISS 데이터베이스에 있는 문서 벡터들과 코사인 유사도를 비교하여 유사한 문서들을 반환해보자. documents에는 해당 질문과 가장 비슷한 내용이 담긴 문서가 리스트로 저장된다.

```
documents =  database.similarity_search("소녀는 어디에 있는가?")
for document in documents:
    print(document.page_content)
```

유사도가 높은 문서를 4개 불러왔다.

| - 7 - 나 어쩌나. 가면 소녀를 보게 될까 어떨까.그러다가 까무룩 잠이 들었는가 하는데,“허, 참 세상일도…….”마을 갔던 아버지가 언제 돌아왔는지,“윤 초시 댁도 말이 아니야, 그 많던 전답을 다 팔아 버리고, 대대로 살아오던 집마저 남의 손에 넘기더니, 또 악상까지 당하는걸 보면…….”남폿불 밑에서 바느질감을 안고 있던 어머니가,“증손(曾孫)이라곤 계집애 그 애 하나뿐이었지요?”“  ... (생략) ...  - 1 - 소나기황순원소년은 개울가에서 소녀를 보자 곧 윤 초시네 증손녀(曾孫女)딸이라는 걸 알 수 있었다. 소녀는 개울에다 손을 잠그고 물장난을 하고 있는 것이다. 서울서는 이런 개울물을 보지 못하기나 한 듯이.벌써 며칠째 소녀는, 학교에서 돌아오는 길에 물장난이었다.  ... (생략) ...  - 3 - 돌아다보니, 소녀는 지금 자기가 지나쳐 온 허수아비를 흔들고 있다. 좀 전 허수아비보다 더 우쭐거린다.논이 끝난 곳에 도랑이 하나 있었다. 소녀가 먼저 뛰어 건넜다.거기서부터 산 밑까지는 밭이었다.수숫단을 세워 놓은 밭머리를 지났다.“저게 뭐니?”“원두막.”“여기 참외, 맛있니?”“그럼, 참외 맛도 좋지만 수박 맛은 더 좋다.”“하나 먹어 봤으면.”소년이 참외 그루에 심은 무우밭으로 들어가, 무우 두 밑을 뽑아 왔다. 아직 밑이 덜 들어 있었다. 잎을 비틀어 팽개친 후, 소녀에게 한개 건넨다.  ... (생략) ...  - 4 - 다. 좀처럼 끊어지지 않는다. 안간힘을 쓰다가 그만 미끄러지고 만다. 칡덩굴을 그러쥐었다.소년이 놀라 달려갔다. 소녀가 손을 내밀었다. 손을 잡아 이끌어 올리며, 소년은 제가 꺾어다 줄 것을 잘못했다고 뉘우친다. 소녀의 오른쪽 무릎에 핏방울이 내맺혔다. 소년은 저도 모르게 생채기에 입술을 가져다 대고 빨기 시작했다. 그러다가, 무슨 생각을 했는지 홱 일어나 저 쪽으로 달려간다.  ... (생략) ... |
| --- |

## 4. LLaMa3.2:3b 모델 사용

Ollama에 설치한 llama3.2:3b 모델을 사용한다. ChatOllama는 채팅 기반 LLM 인터페이스로, 프롬프트에 따라 문장 생성 또는 질문 응답을 수행한다. temperature는 0으로 설정하여, 무작위성을 최소화하여 일관되고 안정적인 응답을 생성하도록 한다. ChatOllama는 사용하는데 별도의 요금을 내지 않아도 된다. 실행을 위한 전기만 사용한다.

```
from langchain_ollama import ChatOllama
from langchain.chains import RetrievalQA
llm = ChatOllama(model="llama3.2:3b", temperature=0)
```

database는 벡터스토어 객체(예: FAISS)이며, 여기에 저장된 문서들 중 질문과 유사한 문서를 찾아주는 retriever로 변환한다. 질문이 들어오면 연관 문서를 찾아주는 역할을 한다. RetrievalQA 클래스는 LangChain에서 제공하는 검색 기반 질의응답 체인 클래스다.

```
retriever = database.as_retriever()
retrievalQA  = RetrievalQA.from_chain_type(llm=llm, retriever=retriever)
```

## 5. RetrievalQA를 활용하여 질문

본문에 있는 내용을 질문해 보았는데 가끔 엉뚱한 답을 하기도 하지만 상당히 답변을 잘하는 편이다.

```
query = "소녀가 물 속에서 집은 것은?"
result = retrievalQA .invoke({"query": query})
print(result["result"])
```

> 조약돌

```
query = "소녀가 흔들어 댄 것은?"
result = retrievalQA.invoke({"query": query})
print(result["result"])
```

> 허수아비

## 6. 전체 코드

```
# 1. PDF 파일 불러오기
from langchain.document_loaders import PyPDFLoader
loader = PyPDFLoader("../Data/TheCloudburst.pdf")
document = loader.load()

print(document[0].page_content)
print(document[0].metadata)

# 2. 문장을 벡터로 변경
from langchain_ollama import OllamaEmbeddings
embeddings = OllamaEmbeddings(model="nomic-embed-text:latest")

embedding_val = embeddings.embed_query("황순원의 소나기")
print(embedding_val)

# 3. FAISS 벡터 디비에 저장
from langchain.vectorstores import FAISS
database = FAISS.from_documents(document, embeddings)

documents =  database.similarity_search("소녀는 어디에 있는가?")
for document in documents:
    print(document.page_content)

# 4. LLaMa3.2:3b 모델 사용
from langchain_ollama import ChatOllama
from langchain.chains import RetrievalQA
llm = ChatOllama(model="llama3.2:3b", temperature=0)

retriever = database.as_retriever()
retrievalQA  = RetrievalQA.from_chain_type(llm=llm, retriever=retriever)

# 5. RetrievalQA를 활용하여 질문
query = "소녀가 물 속에서 집은 것은?"
result = retrievalQA .invoke({"query": query})
print(result["result"])

query = "소녀가 흔들어 댄 것은?"
result = retrievalQA.invoke({"query": query})
print(result["result"])
```

![[03 Attachments/티스토리 Vento AI Lab/785/785-002-주한길.png]]

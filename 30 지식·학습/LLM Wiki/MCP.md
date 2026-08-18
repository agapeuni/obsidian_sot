---
title: MCP
type: concept
status: active
created: 2026-08-15
updated: 2026-08-15
aliases:
  - Model Context Protocol
tags:
  - ai/mcp
  - ai/agent
visibility: private
rag: include
---

# MCP

MCP는 AI 애플리케이션이 외부 데이터와 도구를 일관된 방식으로 발견하고 호출하도록 연결하는 프로토콜이다.

## 주요 개념

- **Client**: 모델을 사용하는 애플리케이션 측 연결 주체
- **Server**: 도구, 리소스, 프롬프트 등을 제공
- **Tool**: 실행 가능한 함수
- **Resource**: 읽을 수 있는 데이터와 문맥
- **Transport**: 클라이언트와 서버 사이의 통신 방식

## 설계 체크리스트

- [ ] 도구 이름과 설명만으로 모델이 용도를 구분할 수 있는가?
- [ ] 입력 스키마가 모호하지 않은가?
- [ ] 읽기·쓰기·파괴적 작업이 구분되는가?
- [ ] 인증과 권한이 사용자 범위를 보존하는가?
- [ ] 오류가 모델과 운영자에게 충분한 정보를 주는가?
- [ ] 호출 결과의 민감정보가 로그에 노출되지 않는가?
- [ ] 시간 제한, 재시도, 멱등성이 정의되어 있는가?

## 관련

- [[AI Agent]]
- [[LLM 애플리케이션 아키텍처]]
- [[LLM 보안]]


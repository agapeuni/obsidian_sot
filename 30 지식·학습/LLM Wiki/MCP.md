---
title: MCP
type: concept
status: verified
created: 2026-08-15
updated: 2026-08-18
aliases:
  - Model Context Protocol
tags:
  - ai/mcp
  - ai/agent
visibility: private
rag: include
source_checked: 2026-08-18
---

# MCP

MCP(Model Context Protocol)는 AI 애플리케이션이 외부 데이터, 도구, 재사용 프롬프트를 표준 인터페이스로 발견하고 사용하도록 연결하는 프로토콜이다.

## 아키텍처

- **Host**: 사용자 승인, 보안 정책, 모델 통합과 여러 Client의 생명주기를 관리한다.
- **Client**: Host가 생성하며 특정 Server와 연결하고 capability 협상과 메시지 처리를 담당한다.
- **Server**: 한정된 책임 범위에서 Tool, Resource, Prompt 등의 기능을 제공한다.

## Server primitive

| primitive | 주 제어 주체 | 용도 |
|---|---|---|
| Tool | 모델 | 외부 기능 실행과 데이터 조회 |
| Resource | 애플리케이션 | 파일·DB·API 결과 등 문맥 제공 |
| Prompt | 사용자 | 재사용 가능한 상호작용 템플릿 선택 |

## 전송과 버전

- 표준 전송은 로컬 프로세스용 `stdio`와 원격 서비스용 Streamable HTTP를 사용한다.
- 2026-07-28 규격은 프로토콜 코어를 stateless request/response 방식으로 전환했다.
- Streamable HTTP 요청은 라우팅·권한·관측을 위해 `Mcp-Method`, `Mcp-Name` 헤더를 사용한다.
- 서버가 추가 사용자 입력이나 모델 처리를 요구하는 흐름은 MRTR(Multi Round-Trip Requests)로 표현한다.
- 구현은 Client와 Server가 합의한 protocol version과 SDK 지원 범위를 확인해야 한다.

## 설계 체크리스트

- [ ] 도구 이름과 설명만으로 모델이 용도를 구분할 수 있는가?
- [ ] 입력 스키마가 모호하지 않은가?
- [ ] 읽기·쓰기·파괴적 작업이 구분되는가?
- [ ] 인증과 권한이 사용자 범위를 보존하는가?
- [ ] 오류가 모델과 운영자에게 충분한 정보를 주는가?
- [ ] 호출 결과의 민감정보가 로그에 노출되지 않는가?
- [ ] 시간 제한, 재시도, 멱등성이 정의되어 있는가?

## 기업 적용 기준

- Host가 사용자 동의와 Server별 연결 권한을 통제한다.
- Server는 전체 대화나 다른 Server의 문맥에 접근하지 않는 독립 경계를 유지한다.
- 원격 Server는 OAuth 대상 리소스, 발급자, scope와 credential 격리를 검증한다.
- Tool 목록과 결과를 신뢰하지 않고 Schema, 민감정보, 실행 영향을 검증한다.
- protocol version, Server 버전, Tool Schema를 배포 기록에 남긴다.

## 실패 패턴

- Host와 Client를 같은 구성요소로 설명해 보안 책임이 불분명해진다.
- Tool·Resource·Prompt의 제어 주체를 구분하지 않는다.
- 과거 HTTP+SSE 또는 세션 기반 예제를 최신 규격으로 오인한다.
- 도구 성공 응답만 믿고 실제 외부 시스템 상태를 확인하지 않는다.

## 출처

- [MCP 2026-07-28 Specification 발표](https://blog.modelcontextprotocol.io/posts/2026-07-28/)
- [MCP 공식 Architecture](https://modelcontextprotocol.io/specification/2025-06-18/architecture)
- [MCP Server primitives](https://modelcontextprotocol.io/specification/draft/server/index)
- [SEP-2243 HTTP Header Standardization](https://modelcontextprotocol.io/seps/2243-http-standardization)

## 관련

- [[AI Agent]]
- [[LLM 애플리케이션 아키텍처]]
- [[LLM 보안]]

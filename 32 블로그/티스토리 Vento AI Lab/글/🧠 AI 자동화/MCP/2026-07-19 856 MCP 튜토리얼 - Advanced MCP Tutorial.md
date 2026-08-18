---
title: MCP 튜토리얼  - Advanced MCP Tutorial
type: blog-archive
status: active
created: '2026-07-19'
updated: '2026-08-16'
published: '2026-07-19T21:40:21+09:00'
source: https://agapeuni.tistory.com/856
source_blog: agapeuni.tistory.com
post_id: 856
category: 🧠 AI 자동화/MCP
tags:
- AI에이전트워크플로우
- CodexAGENTS작성법
- DESIGN문서작성가이드
- MCP감사로그구현
- MCP고도화
- MCP보안권한설계
- MCP서버설계
- MCP툴리소스프롬프트
- 실무형MCP튜토리얼
- 프로젝트관리AI에이전트
body_hash: c44bd0873a17214d806b466a69f50da3933effdc5eeef781ca0d6240b994d0d0
visibility: private
rag: exclude
---

# MCP 튜토리얼  - Advanced MCP Tutorial

- 원문: https://agapeuni.tistory.com/856
- 게시일: 2026-07-19T21:40:21+09:00
- 분류: 🧠 AI 자동화/MCP

## 본문

![[03 Attachments/티스토리 Vento AI Lab/856/856-001-AI-Agent-001 (1).png]]

MCP(Model Context Protocol)를 처음 학습할 때는 사칙연산이나 간단한 CRUD 예제가 적합하다. Tool을 등록하고 입력값을 전달한 뒤 결과를 반환하는 흐름을 빠르게 이해할 수 있기 때문이다. 그러나 실제 업무에 MCP를 적용하려면 단순한 함수 호출 수준을 넘어 데이터베이스, 파일, 외부 API, 권한, 로그, 예외 처리까지 함께 고려해야 한다.

삼성전자 임직원을 대상으로 MCP와 AI Agent 개념을 정리하고, 사칙연산 MCP와 Item CRUD MCP 튜토리얼을 제공했다. 다음 단계로는 실제 프로젝트에서 활용할 수 있는 구조를 학습할 수 있도록 고도화된 MCP 예제를 설계할 필요가 있었다.

이번 고도화 튜토리얼은 프로젝트 관리 업무를 지원하는 Advanced MCP Assistant를 기준으로 구성했다. 사용자는 자연어로 프로젝트 현황을 조회하고, 지연된 작업을 확인하며, 관련 문서를 검색하고, 주간보고 초안을 생성할 수 있다.

## 단순 CRUD에서 실무형 MCP로 확장하기

기초 MCP 예제는 일반적으로 다음과 같은 구조를 가진다.

```
사용자 요청
→ MCP Tool 호출
→ 함수 실행
→ 결과 반환
```

실무 환경에서는 이보다 더 많은 구성 요소가 필요하다.

```
사용자
→ AI Agent 또는 MCP Host
→ MCP Client
→ MCP Server
→ Application Service
→ Database / File / REST API
→ 결과 반환
```

여기에 인증, 권한, 감사 로그, 입력 검증, 오류 처리, 재시도 정책이 추가된다. 특히 사내 시스템과 연결되는 MCP 서버는 단순히 기능이 동작하는 것만으로 충분하지 않다. 누가 어떤 Tool을 호출했는지, 어떤 데이터가 변경되었는지, 실패 원인이 무엇인지 추적할 수 있어야 한다.

## 고도화 MCP 튜토리얼의 주요 기능

이번 튜토리얼에서는 프로젝트 관리 업무를 예제로 사용한다. 실제 사내 데이터는 사용하지 않고 SQLite, 샘플 문서, Mock REST API를 이용해 독립적으로 실행할 수 있도록 설계한다.

주요 조회 Tool은 다음과 같다.

```
list_projects
get_project
list_tasks
list_delayed_tasks
search_project_documents
get_project_summary
get_audit_logs
```

데이터를 변경하는 쓰기 Tool도 별도로 제공한다.

```
create_task
update_task_status
add_project_note
```

보고서 생성을 위한 Tool도 포함한다.

```
generate_weekly_report
```

예를 들어 사용자가 다음과 같이 요청할 수 있다.

```
진행 중인 프로젝트 중 지연된 작업을 조회하고,
관련 운영 가이드에서 대응 절차를 찾아
주간보고 초안을 작성해줘.
```

AI Agent는 요청을 처리하기 위해 여러 Tool을 순서대로 호출한다.

```
list_delayed_tasks
→ get_project
→ search_project_documents
→ weekly_project_report
→ generate_weekly_report
```

이 과정을 통해 단일 Tool 호출이 아니라 여러 Tool을 조합하는 Agent Workflow를 학습할 수 있다.

## MCP Tool, Resource, Prompt 구분

MCP를 실무에 적용할 때 자주 혼동하는 부분이 Tool, Resource, Prompt의 역할이다.

Tool은 특정 작업을 실행할 때 사용한다. 데이터베이스를 조회하거나 외부 API를 호출하고, 작업 상태를 변경하는 기능이 해당한다. Resource는 URI 기반으로 데이터를 제공할 때 사용한다.

```
project://overview/1001
project://tasks/1001
guide://operation
guide://security
audit://recent
```

Resource는 기본적으로 조회 전용으로 구성하는 것이 적절하다.

Prompt는 반복적으로 사용되는 업무 지시문을 템플릿으로 제공한다.

```
weekly_project_report
delayed_task_analysis
incident_response_plan
project_risk_review
```

주간보고나 장애 분석과 같이 일정한 출력 구조가 필요한 업무에 활용할 수 있다.

## MCP 서버의 계층 구조

MCP Tool 함수 안에 데이터베이스 처리와 비즈니스 로직을 모두 작성하면 코드가 빠르게 복잡해진다. 따라서 MCP는 외부 인터페이스 계층으로 분리하는 것이 좋다.

```
MCP Adapter
→ Application Service
→ Repository
→ Database 또는 External API
```

MCP Tool은 입력값 검증, 권한 확인, 서비스 호출, 오류 변환, 감사 로그 기록, 결과 반환만 담당한다.

실제 업무 규칙은 Application Service에 작성하고 데이터 접근은 Repository에서 처리한다. 이 구조를 적용하면 MCP SDK가 변경되거나 REST API 형태로 전환해도 비즈니스 로직을 재사용할 수 있다.

## 인증과 역할 기반 권한

튜토리얼에서는 사용자를 viewer와 operator 두 역할로 구분한다.

viewer는 프로젝트, 작업, 문서를 조회할 수 있지만 데이터를 변경할 수 없다. operator는 작업 생성, 상태 변경, 프로젝트 노트 추가와 같은 쓰기 작업을 수행할 수 있다.

쓰기 Tool은 다음 절차를 반드시 거친다.

```
인증
→ 권한 확인
→ 입력값 검증
→ 사용자 확인
→ 데이터 변경
→ 감사 로그 기록
→ 결과 반환
```

작업 상태 변경 Tool의 입력 예시는 다음과 같다.

```
{
  "task_id": 501,
  "status": "DONE",
  "confirmed": true
}
```

confirmed=true를 요구하면 AI Agent가 사용자의 의도와 다르게 데이터를 자동 변경하는 위험을 줄일 수 있다.

## 감사 로그와 요청 추적

업무 시스템과 연결된 MCP에서는 감사 로그가 중요하다. 모든 Tool 호출에는 요청 ID를 부여하고 다음 항목을 기록한다.

```
timestamp
request_id
user_id
role
tool_name
input_summary
result_status
duration_ms
error_code
```

쓰기 Tool은 변경 전 상태와 변경 후 상태를 함께 기록한다.

로그에는 비밀번호, API Key, Token, 전체 문서 내용, 개인식별정보를 저장하지 않는다. 민감한 값은 반드시 마스킹해야 한다.

## 외부 API 장애와 Fallback 처리

고도화된 MCP 서버는 외부 REST API와 연결되는 상황도 고려해야 한다. 튜토리얼에서는 조직 정보를 조회하는 Mock API를 제공한다.

외부 API 호출에는 다음 정책을 적용한다.

```
연결 시간 제한: 3초
응답 시간 제한: 10초
재시도: 최대 2회
5xx 오류: 재시도
4xx 오류: 즉시 실패
```

외부 API가 실패하면 데이터베이스에 저장된 최근 정보를 반환하는 Fallback도 구현할 수 있다. 이때 결과에 source=cache와 같은 정보를 포함해 실시간 데이터가 아니라는 점을 표시해야 한다.

## 프로젝트 문서 검색

문서 검색 기능은 초기 단계에서 벡터 데이터베이스를 사용하지 않는다. 먼저 파일 기반 키워드 검색으로 구현한 뒤 이후 RAG로 확장하는 방식이 적절하다.

검색 대상은 프로젝트별 디렉터리로 제한한다.

```
data/projects/{project_id}/
```

허용 확장자는 .md, .txt, .json으로 제한하고, 절대 경로와 ../를 이용한 경로 탐색을 차단한다.

검색 결과에는 파일 전체 내용을 반환하지 않고 파일명, 관련 문장, 검색 점수만 제공한다.

```
{
  "filename": "operation-guide.md",
  "snippet": "장애 발생 시 담당자는...",
  "score": 0.85
}
```

이 구조는 이후 Chunking, Embedding, Vector DB, 권한 기반 검색을 적용하는 RAG 튜토리얼로 확장할 수 있다.

## AI Agent의 다중 Tool 호출

이번 튜토리얼의 핵심은 AI Agent가 여러 MCP Tool을 연결해 하나의 업무를 처리하는 것이다.

기본 실행 흐름은 다음과 같다.

```
사용자 요청 분석
→ 필요한 Tool 선택
→ 조회 Tool 실행
→ 결과 충분성 판단
→ 추가 Tool 호출
→ 최종 응답 생성
```

Agent의 무한 반복과 불필요한 Tool 호출을 방지하기 위해 다음과 같은 제한을 둔다.

```
동일 Tool 연속 호출 최대 2회
전체 Tool 호출 최대 8회
동일 인자로 실패한 호출 반복 금지
쓰기 Tool 자동 재시도 금지
```

외부 API 오류나 데이터 부족이 발생하면 재시도 가능 여부를 확인하고, 대체 Tool이나 캐시 데이터를 사용하도록 설계한다.

## Codex를 위한 AGENTS.md

AGENTS.md는 Codex가 프로젝트를 구현할 때 지켜야 하는 기준을 정의한다.

주요 내용은 다음과 같다.

- 프로젝트 목표와 구현 범위

- 디렉터리 구조

- MCP Tool, Resource, Prompt 목록

- 계층 분리 원칙

- 입력과 출력 스키마 규칙

- 인증과 권한 정책

- 민감정보 처리

- 감사 로그

- 테스트 기준

- README 작성 규칙

- Codex 작업 순서

- 금지 사항

- 최종 산출물

Codex에 단순히 “MCP 서버를 만들어줘”라고 요청하면 기능은 동작하지만 구조와 품질은 일관되지 않을 수 있다. AGENTS.md를 통해 구현 규칙, 보안 정책, 테스트 기준을 미리 정의하면 결과물의 품질을 높일 수 있다.

## 시스템 설계를 위한 DESIGN.md

DESIGN.md는 프로젝트의 전체 구조와 기술적 의사결정을 설명한다.

주요 내용은 다음과 같다.

- 프로젝트 배경과 목표

- 대상 사용자와 선수 지식

- 사용자 시나리오

- 전체 아키텍처

- 도메인 모델

- Tool 입력과 출력

- Resource URI

- Prompt Template

- Agent Workflow

- 인증과 권한

- 외부 API 연계

- 파일 검색

- 오류 코드

- 로깅과 모니터링

- 데이터베이스 구조

- 테스트 전략

- 성능 기준

- 보안 테스트

- 배포 방식

- 단계별 개발 일정

- 후속 고도화 과제

AGENTS.md가 Codex의 작업 규칙이라면 DESIGN.md는 개발자와 검토자가 시스템의 의도와 구조를 이해하기 위한 설계 문서라고 볼 수 있다.

## 권장 프로젝트 구조

```
advanced-mcp-assistant/
├── AGENTS.md
├── DESIGN.md
├── README.md
├── pyproject.toml
├── .env.example
├── docker-compose.yml
├── docs/
├── src/
│   └── app/
│       ├── domain/
│       ├── application/
│       ├── infrastructure/
│       ├── mcp/
│       └── agent/
├── data/
├── scripts/
└── tests/
    ├── unit/
    ├── integration/
    ├── security/
    └── scenarios/
```

도메인, 서비스, 인프라, MCP, Agent를 분리하면 코드의 역할이 명확해지고 테스트와 확장이 쉬워진다.

## 테스트와 검증 기준

고도화된 MCP 튜토리얼은 코드 작성보다 검증 과정이 중요하다.

단위 테스트에서는 서비스 로직, 권한 정책, 상태 전이, 경로 검증, 오류 매핑을 확인한다.

통합 테스트에서는 MCP Tool 등록, Resource 조회, Prompt 조회, 데이터베이스 연계, 외부 API 연계, 감사 로그 저장을 확인한다.

보안 테스트에서는 다음 항목을 점검한다.

```
인증 없는 쓰기 요청 차단
viewer 역할의 쓰기 요청 차단
잘못된 Token 차단
경로 탐색 공격 차단
SQL Injection 형태 입력 차단
대량 조회 제한
로그 내 민감정보 미노출
오류 응답 내 내부 경로 미노출
```

최종적으로 다음 명령이 모두 통과해야 한다.

```
ruff check .
ruff format --check .
mypy src
pytest -q
```

## 단계별 구현 계획

1. 프로젝트 구조, 도메인 모델, SQLite, 조회 Tool을 구현하고 MCP Inspector로 검증한다.

2. Resource, Prompt, 파일 검색, Mock REST API, 오류 처리를 추가한다.

3. 인증, 역할 기반 권한, 쓰기 Tool, 감사 로그와 보안 테스트를 구현한다.

4. AI Agent Workflow, 다중 Tool 호출, 장애 대응, Docker 실행 환경, 최종 문서를 완성한다.

한 번에 모든 기능을 구현하기보다 조회 Tool, 외부 연계, 보안, Agent Workflow 순으로 단계적으로 확장하는 것이 안정적이다.

## 다음 단계

이번 튜토리얼은 MCP 기초 예제와 실제 사내 업무 시스템 PoC 사이의 중간 단계에 해당한다.

이후에는 다음과 같은 방향으로 확장할 수 있다.

```
Spring AI 기반 Java MCP 서버
PostgreSQL 전환
Vector DB 기반 문서 검색
사내 SSO 연계
API Gateway 적용
사용자별 데이터 권한
OpenTelemetry 추적
Tool 실행 승인 Workflow
A2A 기반 복수 Agent 협업
MCP 서버 카탈로그
자동 평가와 회귀 테스트
사내 LLM Gateway 연계
```

MCP를 실무에 적용하려면 Tool을 많이 만드는 것보다 안전하고 추적 가능하게 운영할 수 있는 구조를 만드는 것이 중요하다.

사칙연산과 CRUD 예제가 MCP의 동작 원리를 이해하는 단계라면, 고도화 튜토리얼은 데이터 연계, 권한, 오류 처리, 감사 로그, AI Agent Workflow를 함께 설계하는 단계다. AGENTS.md와 DESIGN.md를 기반으로 Codex를 활용하면 단순 코드 생성이 아니라 설계, 구현, 테스트, 문서화가 연결된 MCP 프로젝트를 만들 수 있다.

![[03 Attachments/티스토리 Vento AI Lab/856/856-002-주한길.png]]

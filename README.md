# Obsidian Personal Knowledge System

개인 지식과 업무 자산을 한곳에서 관리하기 위한 Obsidian Vault입니다.  
이 저장소는 자료 수집, 지식 연결, 콘텐츠 제작, 프로젝트 운영을 하나의 **Single Source of Truth(SSOT)** 로 유지하는 것을 목표로 합니다.

> 이 저장소는 개인·업무 자료를 포함할 수 있는 비공개 저장소입니다. 공개 저장소로 전환하거나 외부에 공유하기 전에 반드시 민감정보와 문서 공개 범위를 점검해야 합니다.

## 운영 목표

- 개인 지식과 업무 자료의 기준 원본을 Obsidian으로 통합
- 수집 자료와 정제된 지식 노트를 구분해 보존
- MOC(Map of Content), 내부 링크, 태그를 이용한 지식 연결
- LLM·RAG·AI Agent에서 안전하게 재사용할 문서 선별
- Git을 이용한 변경 이력 추적과 복구
- OpenClaw 자동화 작업의 변경 범위와 보안 통제

## 주요 구조

```text
Obsidian/
├─ 00 Inbox/             분류 전 자료와 임시 메모
├─ 01 Dashboard/         Home, 영역별 MOC, 운영 현황
├─ 02 Templates/         기본 노트와 목적별 템플릿
├─ 03 Attachments/       이미지·PDF 등 첨부파일
├─ 10 신앙·성경/         성경 공부, 묵상, 신앙 기록
├─ 20 생활·가족/         생활, 가족, 건강 기록
├─ 30 지식·학습/         학습 노트와 LLM Wiki
├─ 31 독서·서평/         독서 기록과 서평 아카이브
├─ 32 블로그/            블로그 아이디어와 게시 기록
├─ 33 스레드/            Threads 콘텐츠
├─ 40 코딩·인프라/       개발, AI, 서버, 인프라
├─ 50 개인·과제/         목표, 실행 과제, 주기 노트
├─ 60 자동화·Agent/      OpenClaw, MCP, RAG, Agent
├─ 65 생성·창작/         글·이미지·영상 창작 자료
├─ 70 업무·프로젝트/     프로젝트, 회의, 업무 산출물
├─ 80 사업·전략/         서비스, 제품, 사업 전략
├─ 90 재무·투자/         재무 계획과 투자 기록
└─ 99 Archive/           완료·중단·비활성 자료
```

상세 구조와 문서 이동 기준은 [Vault 구조 및 운영 가이드](01%20Dashboard/Vault%20구조%20및%20운영%20가이드.md)를 참고합니다.

## 시작 위치

- [Home](01%20Dashboard/Home.md): Vault 전체 진입점
- [지식 연결 허브](01%20Dashboard/지식%20연결%20허브.md): 영역을 넘는 주제별 탐색
- [Vault 데이터 현황](01%20Dashboard/Vault%20데이터%20현황.md): 자료 구성과 품질 현황
- [Vault 태그 사전](01%20Dashboard/Vault%20태그%20사전.md): 태그 역할과 표준 계층
- [LLM Wiki](30%20지식·학습/LLM%20Wiki/LLM%20Wiki.md): LLM·RAG·Agent 지식 허브
- [OpenClaw 변경 정책](60%20자동화·Agent/OpenClaw%20Obsidian%20변경%20정책.md): 자동 수정의 안전·검증·복구 기준

## 문서 메타데이터

일반 노트는 다음 frontmatter를 기본으로 사용합니다.

```yaml
---
title: 문서 제목
type: note
status: active
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags: []
visibility: private
rag: exclude
---
```

주요 필드의 의미는 다음과 같습니다.

| 필드 | 용도 |
|---|---|
| `type` | 문서 형식과 처리 방식 |
| `status` | `seed`, `active`, `verified`, `deprecated`, `archived` 등 생명주기 |
| `visibility` | `private`, `company-confidential` 등 공개 범위 |
| `rag` | LLM/RAG 검색 대상 포함 여부 |
| `source` | 원본 자료 위치 또는 출처 |
| `body_hash` | 수집 자료의 중복·변경 추적 값 |

`README.md`는 GitHub 첫 화면 표시를 위한 저장소 문서이므로 Vault frontmatter 적용 대상에서 제외합니다.

## 자료 처리 흐름

1. 새 자료는 `00 Inbox`에 저장합니다.
2. 검토 후 적절한 영역으로 이동합니다.
3. 관련 MOC·개념 노트와 내부 링크를 연결합니다.
4. 공개 범위와 RAG 포함 여부를 확인합니다.
5. 완료되거나 비활성화된 자료는 `99 Archive`로 이동합니다.
6. 의미 있는 변경은 Git 커밋으로 기록합니다.

## 보안 원칙

- API 키, 토큰, 비밀번호, 쿠키, 개인키를 Markdown에 저장하지 않습니다.
- `visibility: company-confidential` 문서는 외부 게시·전송·RAG 처리에서 제외합니다.
- `.env`, 인증서, 개인키, Obsidian UI 상태와 플러그인 로컬 데이터는 Git에서 제외합니다.
- 외부 공개나 자동 게시 전에 문서 내용과 첨부파일을 함께 검토합니다.
- `source`, `body_hash`, 수집 manifest는 자동화 재실행에 필요한 추적 계약으로 취급합니다.

## 변경 원칙

- 원본 아카이브는 보존하고 해석·요약·연결은 별도 지식 노트에서 수행합니다.
- 문서 이동과 이름 변경은 내부 링크가 함께 갱신되는 방식으로 수행합니다.
- 대량 이동, 병합, 삭제, 공개 범위 변경은 사전 검토와 복구 지점을 필요로 합니다.
- 자동화 작업 후에는 frontmatter, broken link, 첨부 누락, Git diff를 검증합니다.
- GitHub push는 검증된 변경만 수행합니다.

## 권장 작업 순서

```text
수집 → 분류 → 정제 → 연결 → 검증 → 커밋 → 필요 시 push
```

이 Vault는 단순한 파일 보관소보다, 과거 자료를 현재의 지식과 실행 가능한 자산으로 전환하는 운영형 지식 시스템을 지향합니다.

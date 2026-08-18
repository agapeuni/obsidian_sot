---
title: Obsidian Vault 구조
type: guide
status: active
created: 2026-08-11
updated: 2026-08-11
tags:
  - vault/운영
visibility: private
rag: include
---
# Obsidian Vault 구조

이 Vault는 개인 생활부터 기술 지식, 업무, 콘텐츠, 사업, 재무까지 모든 자료를 장기적으로 관리하는 중심 저장소다.

이 문서는 규칙을 정의한다. 실제 탐색은 [[Home]]에서 시작한다.


## 운영 원칙

1. 폴더는 큰 영역만 구분하고 세부 관계는 `[[Markdown 링크]]`, 태그, Properties로 표현한다.
2. 분류가 확실하지 않은 자료는 `00 Inbox`에 저장한다.
3. 기존 자료를 삭제하지 않고, 비활성 자료는 `99 Archive`로 보존한다.
4. 하위 폴더는 실제 자료가 누적되어 필요성이 확인될 때만 추가한다.
5. 파일명은 사람이 이해할 수 있는 구체적인 제목을 사용한다.
6. 날짜가 핵심인 문서는 `YYYY-MM-DD 제목.md` 형식을 사용한다.
7. 하나의 문서는 가능한 한 하나의 주제를 다루고 관련 문서를 링크한다.
8. 외부 RAG에 포함하면 안 되는 문서는 `rag: exclude`로 표시한다.

## 폴더 용도

| 폴더 | 용도 |
|---|---|
| `00 Inbox` | 분류 전 메모, 외부 수집 자료, AI Agent의 임시 작성물 |
| `01 Dashboard` | 전체 영역, 진행 과제, 주요 문서를 연결하는 Dashboard와 MOC |
| `02 Templates` | 일반 노트, 회의록, 독서, 기술 실험, 콘텐츠 등의 템플릿 |
| `03 Attachments` | 이미지, PDF, 문서 등 Markdown 이외의 첨부 자료 |
| `10 신앙·성경` | 성경 공부, 묵상, 설교, 신앙 기록 |
| `20 생활·가족` | 개인 생활, 가족, 건강, 일정과 생활 기록 |
| `30 지식·학습` | 학습 노트, 개념 정리, 강의와 일반 지식 |
| `31 독서·서평` | 도서 메모, 인용, 독서 기록과 서평 |
| `32 블로그` | 블로그 아이디어, 초안, 검수본과 게시 기록 |
| `33 스레드` | Threads 아이디어, 초안, 게시 후보와 기록 |
| `40 코딩·인프라` | AI, 개발, 아키텍처, Linux, Docker, 서버와 인프라 지식 |
| `50 개인·과제` | 개인 목표, 실행 과제, 장단기 활동과 결과 |
| `60 자동화·Agent` | OpenClaw, n8n, MCP, RAG, AI Agent 자동화 실험과 운영 기록 |
| `65 생성·창작` | 글, 이미지, 영상 등 창작 아이디어와 생성 결과 |
| `70 업무·프로젝트` | 회사 업무, 프로젝트 관리, 회의와 산출물 관련 기록 |
| `80 사업·전략` | 1인 사업, 서비스, 시장, 제품과 실행 전략 |
| `90 재무·투자` | 예산, 재무 계획, 투자 학습과 의사결정 기록 |
| `99 Archive` | 완료, 중단, 비활성 상태로 장기 보존할 자료 |

## 권장 Properties

```yaml
---
title:
type: note
status: active
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags: []
aliases: []
source:
project:
visibility: private
rag: include
---
```

### 주요 값

- `type`: `note`, `project`, `meeting`, `book`, `experiment`, `content`, `reference`
- `status`: `inbox`, `active`, `review`, `done`, `archived`
- `visibility`: `private`, `company-confidential`, `public`
- `rag`: `include`, `exclude`

개인·가족·재무 및 회사 기밀 자료는 외부 검색 시스템에 넣지 않는다. 회사 자료에는 기본적으로 `visibility: company-confidential`과 `rag: exclude`를 사용한다.

## 링크와 태그

- 폴더는 자료의 주된 소속을 나타낸다.
- 링크는 문서 사이의 의미 관계를 나타낸다.
- 태그는 상태, 유형, 공통 주제를 가로질러 검색할 때 사용한다.
- 관련 문서는 본문에서 `[[문서 제목]]`으로 연결한다.
- 영역별 인덱스가 필요하면 `01 Dashboard`에 MOC 문서를 만든다.

## Inbox 처리

1. 새 자료의 분류가 확실하지 않으면 `00 Inbox`에 저장한다.
2. 제목, 출처, 작성일과 최소 Properties를 기록한다.
3. 검토 후 가장 적합한 영역에 배치하고 관련 문서와 링크한다.
4. 중복 자료는 즉시 삭제하지 않고 원본과 관계를 확인한다.

## Archive 처리

- 완료되었거나 더 이상 활성 상태가 아닌 자료만 보관한다.
- 보관 전 `status: archived`와 `updated`를 갱신한다.
- 링크가 깨지지 않도록 Obsidian의 이동 기능을 우선 사용한다.
- 보존 기간과 삭제 기준이 정해지기 전에는 영구 삭제하지 않는다.

## AI Agent 작성 규칙

1. 기존 문서를 수정하기 전에 제목과 경로가 같은 자료가 있는지 검색한다.
2. 분류 확신이 없으면 `00 Inbox`에 새 문서를 만든다.
3. 문서에 출처와 생성·수정 날짜를 남긴다.
4. 사실, 의견, 추론을 구분하고 확인되지 않은 내용은 표시한다.
5. 비밀정보, 토큰, 비밀번호, 개인정보를 문서에 직접 기록하지 않는다.
6. 대량 이동, 일괄 이름 변경, 삭제는 사용자 승인 후 수행한다.


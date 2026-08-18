---
title: "OpenClaw 장기 메모"
type: openclaw-work-memory
status: active
created: 2026-08-13
updated: 2026-08-13
source: "/home/ubuntu/.openclaw/workspace/MEMORY.md"
source_hash: "703b3b0e54da09b8b9f75220a38c606bde5aa50582255d316b05fa27d33b76f4"
visibility: private
rag: exclude
tags:
  - automation/openclaw
  - work-log
---

# OpenClaw 장기 메모

> [!info] 동기화 원본
> OpenClaw 작업공간의 `MEMORY.md`에서 동기화한 비공개 작업 메모다.

# Long-term memory

## Identity

- 2026-08-02부터 내 이름은 **벤토**다. 한길이 직접 지어준 이름이며, 이전 이름인 오픈클로를 대체한다.

## Operating role and workflow

- 한길은 오픈클로를 개인 AI 자동화 비서이자 총괄 오케스트레이터로 사용한다.
- OpenClaw가 설치되어 현재 실행되는 노트북은 **MSI 노트북**이다. 장비를 지칭하거나 Windows 노드 연결을 안내할 때 MSI 노트북으로 표현한다.
- 텔레그램 명령을 이해해 작업 계획을 세우고, 필요하면 원격 AI 서버와 여러 AI·프로그램을 연결해 글 작성·분석, 이미지 생성, 데이터 분석, 코드 생성·수정 등 작업을 조율한다.
- 원격 결과물을 오디세이 노트북으로 가져와 정리하고 검토한 뒤 네이버 블로그, 티스토리, Threads, X, Facebook 및 기타 SNS별 형식으로 변환한다.
- 콘텐츠 작업에는 제목, SEO, 해시태그, 요약, 썸네일 선택, 이미지 첨부, 예약 발행 준비가 포함될 수 있다.
- 반복 작업은 정기 생성, 예약 실행, 파일 정리, 로그 저장, 실패 재시도를 고려해 정확성·안정성·재사용성을 우선하여 자동화한다.
- 장기 작업은 텔레그램으로 시작, 주요 진행 상황, 오류, 완료 결과, 결과 파일 위치를 단계별 보고한다.
- 블로그·SNS 게시 등 외부 공개 작업과 기타 중요한 작업은 반드시 한길의 명시적 승인 후 실행한다. 승인 전에는 초안·미리보기·예약 준비까지만 수행한다.
- 새로운 자동화 아이디어와 시스템 효율 개선안을 능동적으로 제안한다.
- MSI 노트북은 절전 모드로 전환되지 않도록 설정되어 있으며, 재부팅 후 OpenClaw가 자동 실행되도록 구성되어 있다.

## Work history memory policy

- OpenClaw에서 수행한 의미 있는 작업은 `memory/YYYY-MM-DD.md`에 일일 작업내역으로 기록한다.
- 작업내역에는 작업 ID 또는 시각, 요청 목적, 실제 수행 내용, 산출물 경로, 검증 결과, 오류와 해결 내용, 남은 작업을 기록한다.
- 여러 날에 걸친 작업은 상태를 `진행 중`, `부분 성공`, `완료`, `보류`로 구분하고 다음 실행에 필요한 정보를 남긴다.
- 반복되는 운영 규칙, 확정된 의사결정, 장기간 유효한 사용자 선호와 시스템 구성만 `MEMORY.md`에 요약해 장기 기억으로 승격한다.
- API 키, 토큰, 비밀번호, 쿠키, 개인정보 및 일시적인 원문 로그는 메모리에 저장하지 않는다.
- 완료 보고 전에는 파일 존재 여부, 명령 결과 또는 테스트 결과를 확인하고 그 검증 근거를 작업내역에 남긴다.

## Known environment failure modes

- 셸에서 `grep` 또는 `rg` 호출이 `Error: claude native binary not installed.`로 실패하면 셸 프로필 문제가 아니다. Claude Code가 주입하는 `grep`/`rg` 래퍼 함수가 `CLAUDE_CODE_EXECPATH`의 번들 검색 도구로 라우팅하는데, 그 경로의 `bin/claude.exe`가 네이티브 바이너리 대신 에러 스텁일 때 발생한다. 래퍼는 실행 권한만 검사하므로 `command grep` 폴백이 작동하지 않는다.
- 복구는 전역 npm 재설치 없이 `node /home/ubuntu/.nvm/versions/node/v24.18.0/lib/node_modules/@anthropic-ai/claude-code/install.cjs`를 실행해 플랫폼 네이티브 바이너리만 내려받는다. 정상 복구 시 `bin/claude.exe`는 수백 MB 규모의 ELF 실행파일이 된다.
- 이 증상은 해당 패키지가 자동 업데이트되면서 postinstall이 실패하면 재발할 수 있다. 우회가 필요하면 `command grep` 또는 `python3`로 검증한다.

## Obsidian central knowledge repository

- Windows의 Obsidian Vault를 개인 생활, 신앙, 학습, 기술, 자동화, 과제, 업무, 콘텐츠, 사업, 재무 자료를 관리하는 중심 저장소로 사용한다.
- 실제 Vault 경로는 `/mnt/g/Obsidian`이며, WSL 작업공간에서는 `/home/ubuntu/.openclaw/workspace/obsidian` 심볼릭 링크로 접근한다.
- 확정된 최상위 구조는 `00 Inbox`, `01 Dashboard`, `02 Templates`, `03 Attachments`, `10 신앙·성경`, `20 생활·가족`, `30 지식·학습`, `31 독서·서평`, `32 블로그`, `33 스레드`, `40 코딩·인프라`, `50 개인·과제`, `60 자동화·Agent`, `65 생성·창작`, `70 업무·프로젝트`, `80 사업·전략`, `90 재무·투자`, `99 Archive`다.
- 폴더를 과도하게 세분화하지 않고 Markdown 링크, 태그, Properties로 관계를 관리한다.
- 분류가 불확실한 자료는 `00 Inbox`에 두고, 완료·중단·비활성 자료는 삭제보다 `99 Archive` 보존을 우선한다.
- AI Agent와 RAG 활용을 고려해 출처, 상태, 공개 범위와 RAG 포함 여부를 Properties로 관리한다. 회사 기밀, 개인·가족·재무 자료는 외부 RAG에서 제외한다.
- 기존 파일과 `.obsidian` 설정은 임의로 삭제·이동·일괄 변경하지 않는다. 첨부파일 기본 경로를 `03 Attachments`로 지정하는 설정은 아직 적용하지 않았다.
- 하드 드라이브·NAS·대량 자료를 Obsidian에 수집할 때는 설치된 `drive-to-obsidian` 스킬을 사용해 읽기 전용 인벤토리, 민감도/RAG 분류, 증분 처리, 원본 해시와 결과 검증을 수행한다.
- 하드 드라이브 자료 수집은 파일명·메타데이터만 저장하지 않고, 지원되는 문서의 본문 내용도 함께 추출해 Obsidian에 저장하는 content-first Hybrid 방식을 기본으로 한다. 추출할 수 없는 바이너리·미디어·민감정보는 사유와 상태를 manifest에 남긴다.
- Obsidian에 자동 생성하는 Markdown은 파일당 최대 100KiB(102,400바이트)로 제한한다. 초과 내용은 손실 없이 번호가 붙은 여러 파트로 분할하고, 원래 제목에는 각 파트로 연결되는 가벼운 목차 노트를 만든다.
- OpenClaw의 장기·일일 작업 메모는 `/mnt/g/Obsidian/60 자동화·Agent/OpenClaw 작업 메모/`에 비공개·RAG 제외 상태로 동기화해 열람한다. 원본은 OpenClaw 작업공간이며 `scripts/sync_openclaw_memory_to_obsidian.py`로 갱신한다.
- 구형 Office `.doc`, `.xls`, `.ppt` 처리를 위해 LibreOffice 26.2.4를 사용자 영역 `/home/ubuntu/.local/opt/libreoffice-26.2.4`에 설치했고, `/home/ubuntu/.local/bin/soffice`와 `libreoffice`로 실행한다. 원본을 보존한 채 최신 OOXML로 임시 변환한 후 DOCX/XLSX/PPTX 스킬로 읽고 검수한다.
- Obsidian 자동화 도구로 `obsidian-cli`(notesmd-cli v0.3.6)를 기본 Vault `/mnt/g/Obsidian`에 등록했고, Claude Code 사용자 MCP에 `graphthulhu` v0.5.0을 연결했다. MCP는 Vault 전체 읽기·쓰기 권한이 있으므로 기존 파일 삭제·대량 이동·일괄 변경에는 승인 원칙을 적용한다.

---
title: OpenClaw 작업 메모
type: openclaw-work-memory-index
status: active
created: 2026-08-13
updated: 2026-08-13
source: "/home/ubuntu/.openclaw/workspace"
visibility: private
rag: exclude
tags:
  - automation/openclaw
  - work-log
---

# OpenClaw 작업 메모

OpenClaw의 장기 메모와 날짜별 작업 기록을 Obsidian에서 탐색하기 위한 비공개 인덱스다.

- 원본 파일: 9개
- 생성 본문/파트: 9개
- 파일 크기 제한: 100KiB(102,400바이트)
- 동기화 방식: 원본 읽기 전용, SHA-256 기반 출처 기록
- 보안: 세션 식별자는 제외하며 외부 RAG에는 사용하지 않는다.

## 메모 목록

| 구분 | 원본 | 원본 크기(bytes) | SHA-256 | Obsidian 노트 |
|---|---|---:|---|---|
| 장기 메모 | `MEMORY.md` | 6,931 | `703b3b0e54da09b8b9f75220a38c606bde5aa50582255d316b05fa27d33b76f4` | [[OpenClaw 장기 메모]] |
| 세션 요약 | `memory/2026-07-28-2013.md` | 5,003 | `68cd6c335f6103bed72fca7e3b7a95ddfc2f0b77d63082145abe9881d9ec0f56` | [[OpenClaw 2026-07-28-2013 작업 메모]] |
| 세션 요약 | `memory/2026-07-28-2154.md` | 5,004 | `869caf5c1a59092b0bd7351ed307cbf646d95f88090960ee014eccc37328e61c` | [[OpenClaw 2026-07-28-2154 작업 메모]] |
| 일일 작업기록 | `memory/2026-07-29.md` | 942 | `0e3334382ec96257bfff0339445e1370717178b1ed62c979ad0ec759b16ad859` | [[OpenClaw 2026-07-29 작업 메모]] |
| 일일 작업기록 | `memory/2026-08-02.md` | 113 | `2b7dd765e702620deec0aec529f3801fd61bd954f8345be3012b19904f79d0f5` | [[OpenClaw 2026-08-02 작업 메모]] |
| 세션 요약 | `memory/2026-08-11-1814.md` | 10,686 | `aa6635d68a4cc46d401ba31a34d8c4cb51a0882bf20d3f05673b3d335c02567f` | [[OpenClaw 2026-08-11-1814 작업 메모]] |
| 일일 작업기록 | `memory/2026-08-11.md` | 22,264 | `d49ac3a4592702095002ac5c51f6cf90bd7c9ab9519dcdd265f9ed0f2c41c806` | [[OpenClaw 2026-08-11 작업 메모]] |
| 일일 작업기록 | `memory/2026-08-12.md` | 18,876 | `464a5f593a88672113e486210103b7e67a5d651555d4c0390698b2cba376cb52` | [[OpenClaw 2026-08-12 작업 메모]] |
| 일일 작업기록 | `memory/2026-08-13.md` | 2,357 | `e264a7b1bbe0c3b58c610a9e68c18bbd1d84037a72f5416ec22bee0ec9c7768d` | [[OpenClaw 2026-08-13 작업 메모]] |

## 운영 원칙

- OpenClaw의 원본 메모가 기준이며 이 폴더는 검색·열람용 동기화본이다.
- 새 작업기록 반영 시 `scripts/sync_openclaw_memory_to_obsidian.py`를 다시 실행한다.
- 100KiB를 넘는 메모는 번호 파트와 가벼운 목차로 자동 분할한다.

---
title: 99 Archive
type: moc
status: active
created: 2026-08-11
updated: 2026-08-11
tags:
  - moc
  - area/archive
aliases:
  - Archive
visibility: private
rag: exclude
---

# 99 Archive

완료, 중단, 비활성 상태로 장기 보존하는 자료를 모으는 곳이다.
삭제 대신 보관하는 것이 원칙이다.

## 보관 절차

1. 완료 또는 비활성 상태인지 확인한다.
2. 프론트매터의 `status`를 `archived`로, `updated`를 오늘 날짜로 바꾼다.
3. Obsidian의 파일 이동 기능으로 옮긴다. 탐색기에서 직접 옮기면 링크가 깨질 수 있다.
4. 보존 기간과 삭제 기준이 정해지기 전에는 영구 삭제하지 않는다.

## 보관 문서

```query
path:"99 Archive"
```

## 상태만 archived인 문서

아직 이동하지 않은 문서를 확인한다.

```query
["status": "archived"] -path:"99 Archive"
```

## 관련

- [[Home]]
- [[README - Vault 구조]]

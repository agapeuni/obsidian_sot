---
title: "2025-10-06 224033495101 네이밍 규칙 - snake, camel, pascal, kebab"
type: blog-archive
status: active
created: 2025-10-06
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=224033495101&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 224033495101
published: "2025. 10. 6. 19:46"
body_hash: 84c4644a6fb37ed35730c152db79aa3a8fa07a62d65e89da7c3ebed28b7f46bb
visibility: private
rag: exclude
---
# 2025-10-06 224033495101 네이밍 규칙 - snake, camel, pascal, kebab

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=224033495101&categoryNo=982
- 게시일: 2025. 10. 6. 19:46

## 본문

![](https://postfiles.pstatic.net/MjAyNjA1MTdfMjY3/MDAxNzc4OTkwOTkxMjg1.O-bRaFinGGVLqhapSpeeLLzieiAkKWwELgZJBnIyntIg.3YJuJdWpAjMRhueaXPLQtWgScNaVrbO-ouzFReaUNVUg.PNG/%EA%B0%9C%EB%B0%9C%EC%96%B8%EC%96%B4-%ED%8A%B8%EB%A0%8C%EB%93%9C-001_\(1\).png?type=w80_blur)

​

프로그래밍 서적을 보면 종종 등장하는 케이스 스타일을 정리해 본다.

​

1\. snake_case

  * 단어 사이를 밑줄(_)로 연결. 

  * 뱀(snake) 이 기어가는 모양처럼 보여서 붙은 이름

  * 밑줄이 읽기 쉬워서 긴 이름에도 직관적. 

  * Python의 PEP8 스타일 가이드 표준.

​

예시: user_name, get_user_info

user_name = "길한" get_user_info() 

주로 쓰이는 곳

  * Python 변수명, 함수명

  * 데이터베이스 컬럼명

  * 파일명 (특히 Python 프로젝트나 UNIX 계열)

​

2\. camelCase

  * 첫 단어는 소문자, 그다음 단어는 대문자로 시작. 

  * 중간이 낙타 등처럼 올라가 있어서 camel(낙타) 케이스라고 불람. 

  * 간결하면서도 코드 자동완성 시 직관적. 

  * 웹 프론트엔드에서 거의 표준처럼 쓰임.

​

예시: userName, getUserInfo

let userName = "길한"; function getUserInfo() { ... }

주로 쓰이는 곳

  * JavaScript 변수명, 함수명

  * Java / Kotlin / Swift 의 로컬 변수명, 함수명

  * JSON key (API 데이터 필드)

​

3\. PascalCase

모든 단어를 대문자로 시작. 

주로 **클래스나 컴포넌트 이름에 사용.**

첫 글자가 대문자라 “정의체(클래스, 타입)”임을 쉽게 구분 가능.

​

예시: UserName, GetUserInfo

function UserProfileCard() { return <div>안녕하세요!</div>; } 

주로 쓰이는 곳

  * 클래스명, 타입명, 컴포넌트명

  * 예: React 컴포넌트 <UserProfileCard />

  * C#, Java, TypeScript 등에서 클래스나 인터페이스 이름

​

4\. kebab-case

  * 단어 사이를 **하이픈(-)** 으로 연결.

  * 하이픈은 HTML/CSS에서 자연스럽고, 대문자를 쓸 수 없는 환경에서도 가독성이 좋음.

  * URL-friendly (대소문자 구분 없는 환경에서도 문제 없음).

​

예시: user-name, get-user-info

<div class="user-profile-card"></div> .user-profile-card { color: blue; }

주로 쓰이는 곳

  * HTML 속성명 (data-user-id)

  * CSS 클래스/ID 이름

  * 파일명, URL 경로

​

​

case style 요약

표기법 |  예시 |  설명 |  특징  
---|---|---|---  
snake_case |  item_list. apple_banana |  단어 사이를 밑줄(_)로 연결 |  읽기 쉬움, 전통적 스타일  
camelCase |  itemList, appleBanana |  두 번째 단어부터 대문자로 시작 |  함수·변수에 일반적  
PascalCase |  ItemList, AppleBanana |  모든 단어를 대문자로 시작 |  클래스·컴포넌트 이름  
kebab-case |  item-list, apple-banana |  단어 사이를 하이픈(-)으로 연결 |  하이픈 연결, 웹 친화적  
  
​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#프로그래밍 #코딩기초 #코딩공부 #개발자블로그 #케이스스타일 #snake_case #camelCase #PascalCase #kebab-case #네이밍규칙 #코드컨벤션 #프로그래밍입문 #코딩초보 #파이썬공부 #자바스크립트공부 #HTML기초 #CSS기초 #리액트공부 #TypeScript #코딩팁 #웹개발 #프론트엔드개발 #백엔드개발 #개발자상식 #PEP8 #API개발 #프로그래밍스타일 #코딩베스트프랙티스 #AI활용

![](https://postfiles.pstatic.net/MjAyNTEwMDZfMjcy/MDAxNzU5NzQ2ODgzMjQ2.HTCv66UpQDlART2wGRAMuaGIMLWNvlLeM5G6g5nFbQsg.b_hd_ZPtYZ_NMoz5xPtBjE6e-qJlQ_AUVDAyoORbipAg.PNG/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

_​_

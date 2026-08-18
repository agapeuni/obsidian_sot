---
title: "2023-10-01 223225812698 textarea 속성 - cols, rows, overflow, wrap,"
type: blog-archive
status: active
created: 2023-10-01
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223225812698&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223225812698
published: "2023. 10. 1. 21:15"
body_hash: 61f6c857e2758ddb4936d7b5fb1183f199e05f47ab446ad936b314b45a7eab1c
visibility: private
rag: exclude
---
# 2023-10-01 223225812698 textarea 속성 - cols, rows, overflow, wrap,

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223225812698&categoryNo=982
- 게시일: 2023. 10. 1. 21:15

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTNfMTQ0/MDAxNzQ0NDczMDI2Njcw.mAiuFYV0nVs1NtpXJubbP2g54qP99B5rz82Za-jJX18g.bI-uSyO6FlKE-6ebzpa6dw5vud31eeRoqnUuSfLEJj8g.PNG/HTML-001_\(4\).png?type=w80_blur)

​

<textarea> 태그는 여러 줄의 텍스트를 입력하거나 표시할 때 사용한다. 글을 입력하다 보면 Enter를 치게 되고 지정한 영역을 입력한 글이 넘치는 경우가 있다. 이럴 때 <textarea>의 스크롤 표시와 Enter 처리에 관한 속성을 알아보자.

<textarea name="memo" cols="50" rows="5" style="overflow:hidden" wrap="hard"> TEST 1 TEST 2 TEST 3 TEST 4 TEST 5 TEST 6 TEST 7 TEST 8 </textarea>

결과 화면

![](https://postfiles.pstatic.net/MjAyMzEwMDFfMjkz/MDAxNjk2MTYyNDQ1MDI1.eIl8d8Ul1gKHFsg4CPKQuh8GoIYLDhPL1JqBBfVei3Mg.DCKvuxWX2zd57b5oYZ9h5XL_svmMR5DSatI5UNOPyTEg.PNG.agapeuni/image.png?type=w80_blur)

​

**cols 속성**

<textarea> 영역의 너비를 조절

​

**rows 속성**

<textarea> 영역의 라인수를 명시하여 높이를 조절

**style의 overflow 속성**

overflow:auto 내용이 넘치면 세로 스크롤이 생김

overflow:visible 크기와 상관없이 모두 표시

overflow:hidden 지정된 크기의 넘치는 내용은 숨김

overflow:scoll 무조건 스크롤을 표시

​

**wrap 속성**

폼 데이터를 제출할 때 입력한 텍스트의 줄바꿈 방식을 정의한다. 

값 |  설명  
---|---  
OFF  |  WRAP 속성을 사용하지 않은 것과 같이 줄 바꿈을 하지 않고 가로 스크롤바가 생겨난다. ENTER 키 입력을 엔터 기호를 추가하지 않고 서버로 보낸다.  
SOFT |  화면상으로는 줄 바꿈을 하지만 "ENTER"를 입력하지 않은 것으로 취급한다. 글 입력 시 자동 줄바꿈을 하지만 엔터 기호를 추가하지 않고 서버로 보낸다.  
HARD  |  화면상에 줄 바꿈을 하면서 "ENTER"가 입력된 것과 같은 결과가 된다. 이 HARD 속성을 사용했을 때 일반 화면의 입력 영역에 입력된 모습 그대로 출력된다. Enter 키 입력을 엔터 기호를 추가하여 서버로 보낸다.  
PHYSICAL  |  글 입력 시 자동 줄바꿈을 하고 엔터 기호를 추가하여 서버로 보낸다.  
  
​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#HTML #웹개발 #프론트엔드 #텍스트영역 #textarea #CSS #웹디자인 #입력폼 #사용자입력 #스크롤바 #줄바꿈 #overflow #폼데이터 #웹폼 #HTML태그 #개발자 #프로그래밍 #웹기술 #개발팁 #프론트엔드개발 #UI디자인 #UX디자인 #JavaScript #반응형웹 #크로스브라우징 #웹표준 #코딩 #웹애플리케이션 #텍스트처리 #웹개발자

![](https://postfiles.pstatic.net/MjAyMzEwMDFfNzQg/MDAxNjk2MTYyMzE3MzAw.3dI8Hs2bxaRF80r6SWYzG6c96QH7dNVAEgsNNQdIr_kg.7E55NqZheES4GCBB0Ugx2fcbu5Rp9fu_b951OY0lWrMg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

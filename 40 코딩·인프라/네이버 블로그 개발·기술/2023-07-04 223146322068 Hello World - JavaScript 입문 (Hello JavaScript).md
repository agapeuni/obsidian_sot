---
title: "2023-07-04 223146322068 Hello World - JavaScript 입문 (Hello JavaScript)"
type: blog-archive
status: active
created: 2023-07-04
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223146322068&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223146322068
published: "2023. 7. 4. 10:59"
body_hash: 840b230a0247a7c2cf17df900624c4901af6cda953fba55db209c4f29be287fe
visibility: private
rag: exclude
---
# 2023-07-04 223146322068 Hello World - JavaScript 입문 (Hello JavaScript)

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223146322068&categoryNo=982
- 게시일: 2023. 7. 4. 10:59

## 본문

![](https://postfiles.pstatic.net/MjAyNTA3MTlfODYg/MDAxNzUyODk1MDA4Nzkz.eQcox42T4iu-ykInJSBXZ5ZD3uHt5mzn9qm57JG0j0Ag.Y4RX7yTm_Jz64og3Ubpti6bun-l2StWa4N0bkyrej6wg.PNG/JavaScrfipt-001_\(1\).png?type=w80_blur)

1\. Hello JavaScript 출력

컴퓨터 언어를 배우기 시작할 때 우리는 해당 언어로 "Hello World"를 찍어보고 시작한다. 자바스크립트를 사용하여 브라우저 화면에 출력하도록 구현해 본다. 버튼에 이벤트를 부여하여 클릭하면 "Hello JavaScript. *^^*"를 표시한다. 

▣ HelloJavaScript.html

<html> <head> <title>Hello</title> <script language="JavaScript"> function clickMe() { var v_hello = "Hello JavaScript. *^^*"; document.title = v_hello; document.getElementById('hello').innerHTML = v_hello; } </script> </head> <body> <h1><span id="hello">Here. *^^*</span></h1> <input type="button" id="clickme" value="Click Me. *^^*" onClick="clickMe()"> </body> </html>

​

▣ 실행화면

![](https://postfiles.pstatic.net/MjAyMzA3MDRfMTg4/MDAxNjg4NDM1MTk1Njcz.e3b9f6elPh4wGr1Pb75UNRqcqhUAHhhNhZcb0wN2SF4g.Mzz48z-mGvleEpqa2SSdJRbIOEXZRUekHhUsb_KkxhEg.PNG.agapeuni/image.png?type=w80_blur)

버튼 클릭 후

![](https://postfiles.pstatic.net/MjAyMzA3MDRfMTcw/MDAxNjg4NDM1MzI5OTA2.7HX2mTbffUzwYrc25Lz6zqzwQ7VVnSrp7tn_HTfeL7Mg.NyMEX6PkAxZqrZUDGmlUBhEs8dvxRSuefvPqh0ys74sg.PNG.agapeuni/image.png?type=w80_blur)

​

​

2\. 'script' 태그

자바스크립트를 작성할 때 'script' 태그를 사용한다. HTML 문서에서 script 태그는 자바스크립트 코드를 작성하는 데 사용되며, script 태그는 head 태그 내부 또는 body 태그 내부에 배치된다. 

<!DOCTYPE HTML> <html> <head> <title>Hello World</title> <script src="main.js"> // 외부 자바스크립트 코드 </script> </head> <body> <script> // 내부 자바스크립트 코드 </script> </body> </html>

자바스크립트에서는 HelloWorld를 표시하기 위한 3가지 방법이 있다.

<script> // cosole.log 사용하기 console.log('Hello World'); </script>

<script> // document.write 사용하기 document.write('Hello World'); </script>

<script> // alert 사용하기 alert('Hello World'); </script>

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#JavaScript #HelloWorld #웹개발 #프로그래밍 #HTML #자바스크립트기초 #웹기술 #코드예제 #버튼클릭이벤트 #프론트엔드개발 #웹디자인 #소프트웨어개발 #스크립트태그 #코드실습 #개발자 #기술블로그 #웹프로그래밍 #프로그래밍공부 #자바스크립트기법 #HTML5 #웹사이트개발 #콘솔로그 #알림창 #문서쓰기 #프로그래밍언어 #자바스크립트이해하기 #코드러닝 #기본코딩 #기술문서 #HTML자바스크립트

![](https://postfiles.pstatic.net/MjAyMzA3MDRfMTgw/MDAxNjg4NDM1MDk2NzA2.X5mmkOLx0PbhnfyU0rfZAc7v7pdY2_WYsX9o0g3Cf1wg.4IwUyY5buZoXyjI66fxwow5YQyVdDwAv0eTu-IlEuvUg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

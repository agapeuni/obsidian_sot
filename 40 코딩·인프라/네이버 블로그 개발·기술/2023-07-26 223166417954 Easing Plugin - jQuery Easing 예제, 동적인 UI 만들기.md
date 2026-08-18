---
title: "2023-07-26 223166417954 Easing Plugin - jQuery Easing 예제, 동적인 UI 만들기"
type: blog-archive
status: active
created: 2023-07-26
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223166417954&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223166417954
published: "2023. 7. 26. 10:54"
body_hash: 749e5083dbe0985c47efcfc949a3bab52e51b1ab7e4476412b9594ce37dc9cfe
visibility: private
rag: exclude
---
# 2023-07-26 223166417954 Easing Plugin - jQuery Easing 예제, 동적인 UI 만들기

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223166417954&categoryNo=982
- 게시일: 2023. 7. 26. 10:54

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTJfMTI3/MDAxNzQ0NDU1NjAwODQy.Xv0LsZH8dYXMUYPbisXkBpReZb3Ydbfs1Quk_seRsXMg.u4xovw2zGi-zHqeC_l6d0h6maMOQXyr-qmToRXh_IZcg.PNG/jQuery-001_\(7\).png?type=w80_blur)

​

1\. 개요

jQuery로 Animate를 적용하면 움직임을 표현할 수 있다. 움직임에 동적인 효과를 주기 위해서 Easing Plugin을 적용한다. easing 함수는 애니메이션이 진행되는 속도를 지정한다. jQuery 애니메이션은 일정한 속도로 진행되는 linear와 애니메이션의 시작과 끝에서 약간 느리게 진행되는 swing이 제공된다. 아래의 그래프는 시작부터 종료까지 어떻게 움직이는지 나타낸다. 바로 적용할 수 있어 사용하기 편리하다.

![](https://postfiles.pstatic.net/MjAyMzA3MjZfMjA5/MDAxNjkwMzM2MzkwNzk2.P-06JgdFV3D05ZHYr0Ajctj8teyQ0S56MyyDO6H4KRQg.caRLjtWGZq3nW0jjp5vO8W3x-DJLlSQ3nlGGgc-JfHIg.PNG.agapeuni/img.png?type=w80_blur)

​

2\. 예제

Easing 플러그인을 사용하면 굉장히 다양한 Ease In, Out 기능을 jQuery에서 혼용하여 사용할 수 있다.

$(document).ready(function() { jQuery.easing.def = 'easeOutQuart'; $(".left").click(function() { $("#left").animate({ width : "400px" }, 1500); }); $(".middle").click(function() { $("#middle").animate({ width : "400px" }, 1500); }); $(".both").click(function() { $(".left").add(".middle").click(); }); $(".reset").click(function() { $("div").css({ width : "" }); }); });

​

3\. 참조 URL

<https://api.jqueryui.com/easings/>

[ **Easings | jQuery UI API Documentation** Easings Easing functions specify the speed at which an animation progresses at different points within the animation. jQuery core ships with two easings: linear , which progresses at a constant pace throughout the animation, and swing (jQuery core's default easing), which progresses slightly slower ... api.jqueryui.com ](https://api.jqueryui.com/easings/)

<http://gsgd.co.uk/sandbox/jquery/easing/>

[ **jQuery Easing Plugin** Version 1.4+ use jQuery.easing 1.4+ For jQuery 3.0+ Available at GitHub Documentation for 1.4.x is still @todo Version 1.3 Description A jQuery plugin from GSGD to give advanced easing options. Please note , the easing function names changed in version 1.2. Please also note , you shouldn't really be... gsgd.co.uk ](http://gsgd.co.uk/sandbox/jquery/easing/)

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#jQuery #Animate #easing #웹개발 #애니메이션효과 #동적효과 #Easing플러그인 #프론트엔드개발 #애니메이션속도 #속도조절 #linear #swing #애니메이션이펙트 #코딩 #프로그래밍 #웹디자인 #인터랙티브웹 #디지털디자인 #UI효과 #사용자경험 #UX디자인 #프로그래머 #웹애니메이션 #인터랙션디자인 #자바스크립트 #코딩팁 #웹기술 #개발자팁 #웹인터페이스 #애니메이션제어 #프로그래밍팁

![](https://postfiles.pstatic.net/MjAyMzA3MjZfMjQw/MDAxNjkwMzM2Mjg5MjQ2.LaTd6DK8-Lqm0lXvvvQy2kBdAwmkw174nSO_asHuTukg.lBdmTt1wjL3RkUE-1EGfkCsZZKvaZc4MeJvAsTQYfTsg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

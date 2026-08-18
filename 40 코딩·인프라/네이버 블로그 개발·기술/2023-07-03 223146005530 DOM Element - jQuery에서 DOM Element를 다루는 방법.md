---
title: "2023-07-03 223146005530 DOM Element - jQuery에서 DOM Element를 다루는 방법"
type: blog-archive
status: active
created: 2023-07-03
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223146005530&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223146005530
published: "2023. 7. 3. 23:32"
body_hash: 508bce51402b4af64267532039e518f6f46f4fd439007149eea6a67ed79f5862
visibility: private
rag: exclude
---
# 2023-07-03 223146005530 DOM Element - jQuery에서 DOM Element를 다루는 방법

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223146005530&categoryNo=982
- 게시일: 2023. 7. 3. 23:32

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTJfNzYg/MDAxNzQ0NDU1MjE4MjMy.Y2jEQZaQLRrJ6KhypTn_pbyqHninM9KLeP0T1IOBRKEg.aRZxd0jK-qMhnjGsOK7KSmklJLOUkrcNzGOY8W53ahEg.PNG/jQuery-001_\(2\).png?type=w80_blur)

​

1\. each(callback) 

일치하는 전체의 Element에 대하여 함수를 실행한다. 

일치하는 Element를 찾을 때마다 1번씩 함수가 실행되는 것을 의미한다. 

함수에서 this 포인터는 각 Element를 의미한다.

예제 1 : div를 찾아서 color 프로퍼티를 변경한다.

$(document.body).click(function () { $("div").each(function (i) { if (this.style.color != "blue") { this.style.color = "blue"; } else { this.style.color = ""; } }); });

​

예제 2 : DOM Element 대신 jQuery 오브젝트를 사용하는 경우 $(this)를 기술한다.

$("span").click(function () { $("li").each(function(){ $(this).toggleClass("example"); }); });

예제 3 : id가 stop인 div가 발견된 시점에 false를 반환하여 루프를 빠져나온다.

$("button").click(function () { $("div").each(function (index, domEle) { // domEle == this $(domEle).css("backgroundColor", "yellow"); if ($(this).is("#stop")) { $("span").text("Stopped at div index #" + index); return false; } }); });

2\. eq(position) 

0부터 length-1 가운데 일치하는 위치에 있는 엘리먼트만 찾아온다.

예제 1 : P 태그 집합 중 위치가 2번째인 Element색상을 바꾼다.

$("p").eq(1).css("color","red")

3\. get() 

jQuery 오브젝트가 가지고 있는 Element 전체를 배열 형태로 반환한다. 

DOM Element를 조작하는데 도움이 된다.

예제 1 : div 요소를 get() 배열로 반환한다. 그리고 reverse() 내장함수를 이용하여 배열을 반전 표시한다.

function disp(divs) { var a = []; for (var i = 0; i < divs.length; i++) { a.push(divs[i].innerHTML); } $("span").text(a.join(" ")); } disp( $("div").get().reverse() );

4\. get(index)

DOM Element의 집합으로부터 인덱스를 지정해 하나의 Element를 참조한다. 

이것에 의해 jQuery 오브젝트일 필요가 없는 케이스로 특정의 DOM Element 그 자체를 조작하는 것이 가능하다.

예제 1

$("*", document.body).click(function (e) { e.stopPropagation(); var domEl = $(this).get(0); $("span:first").text("Clicked on - " + domEl.tagName); });

5\. index(subject)

jQuery 오브젝트 내에서 인수로 지정된 Element 인덱스를 리턴한다. 

만약 jQuery 오브젝트 내에 존재하지 않으면 -1을 리턴한다.

예제 1 : 페이지의 div의 인덱스를 리턴한다.

$("div").click(function () { // this is the dom element clicked var index = $("div").index(this); $("span").text("That was div index #" + index); });

6\. length, size()

jQuery 오브젝트 Element 수를 유지한다. size 함수와 같은 값을 리턴한다.

예제 1 : div를 카운팅 하고 div를 추가한다.

$(document.body).click(function () { $(document.body).append($("<div>")); var n = $("div").length; $("span").text("There are " + n + " divs." + "Click to add more."); }).trigger('click'); // trigger the click to start

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#jQuery #each함수 #eq함수 #get함수 #DOM조작 #프론트엔드 #웹개발 #자바스크립트 #프로그래밍기초 #웹디자인 #웹개발팁 #클릭이벤트 #jQuery활용 #Element조작 #JavaScript #웹프로그래밍 #프론트엔드개발 #개발자팁 #코딩기술 #웹사이트기능 #jQuery기능 #jQuery기초 #jQuery메서드 #UI개발 #웹기능 #jQuery코드 #웹퍼블리싱 #이벤트처리 #웹효율성 #웹성능

![](https://postfiles.pstatic.net/MjAyMzA3MDNfMTU5/MDAxNjg4Mzk0MDk1OTk4.-o6_QltWRn-fVuKW0GRCj_1UrfBNYDUYZR6-fg3ttaEg.l4ZYQY_wjYOjGmFIQDJ_Of8nd0OYpNq5TFEMe2rUiuAg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

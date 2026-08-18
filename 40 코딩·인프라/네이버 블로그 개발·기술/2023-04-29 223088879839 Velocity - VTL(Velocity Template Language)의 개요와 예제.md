---
title: "2023-04-29 223088879839 Velocity - VTL(Velocity Template Language)의 개요와 예제"
type: blog-archive
status: active
created: 2023-04-29
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223088879839&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223088879839
published: "2023. 4. 29. 22:07"
body_hash: 364852700676f27fcc82fe5ab802a178f0d40acf16ab8c4c6dbbc2c37c94a44a
visibility: private
rag: exclude
---
# 2023-04-29 223088879839 Velocity - VTL(Velocity Template Language)의 개요와 예제

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223088879839&categoryNo=982
- 게시일: 2023. 4. 29. 22:07

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTJfMjI5/MDAxNzQ0NDIzMjk5OTE3.A7YKK6dar6qABWfaC3h2AoQSyKCmYgdqhTQCMearRy0g.gaBY0GLVwPjZlGv_-HY0TbjfgxqFYgbs8Io3uty66Dsg.PNG/%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC-001_\(1\).png?type=w80_blur)

​

1\. Velocity 개요

Velocity는 Java 기반 템플릿 엔진이다. 동적인 웹 페이지를 생성하는 데 사용한다. 현재 진행하는 프로젝트에서 화면을 표시하는데 Velocity Template을 사용한다. 숙달된 기술로 학습할 필요는 없고 그냥 기본적인 문법 정도만 알면 충분할 것 같다.

​

![](https://postfiles.pstatic.net/MjAyMzA0MjlfOTUg/MDAxNjgyNzczNTc0Njgy.rwQBU9AOXVshPgUjkF5mxLOSaxRmX6nDG7bv1allsFog.UGoPXg9-aC4SU8d2B74dxBzph9aYidRrxu1RgJHUOygg.PNG.agapeuni/image.png?type=w80_blur)

[이미지 출처] [https://velocity.apache.org](https://velocity.apache.org/)/ 한글 번역 캡처

​

다음은 search.vm 템플릿의 일부이다.

#if($currentSpace && !$currentSpace.isEmpty()) #spacelabel($currentSpace) #end <div class="page-wrapper"> <h2> #if ($showParam) #if ($showParam == "questions") $!lang.get("questions.title") #showcount($itemcount.count) #elseif ($showParam == "answers") $!lang.get("answers.title") #showcount($itemcount.count) #elseif ($showParam == "feedback") $!lang.get("feedback.title") #showcount($itemcount.count) #elseif ($showParam == "people") $!lang.get("people.title") #showcount($itemcount.count) #elseif ($showParam == "comments") $!lang.get("comments.title") #showcount($itemcount.count) #end #else $!lang.get("search.title") #end <span class="grey-text text-darken-1 smallText">$!searchQuery</span> </h2> </div> ... (생략) ...

​

​

2\. Velocity 표기법

**변수 표기법:**

$ [ ! ][ { ][ a..z , A..Z ][ a..z , A..Z , 0..9 , - , _ ][ } ]

​

예:

  * 속기 표기법 : $mud-Slinger_9

  * 침묵 속기 표기법 : $!mud-Slinger_9

  * 형식 표기 : ${mud-Slinger_9}

  * 사일런트 형식 표기법 : $!{mud-Slinger_9}

​

**프로퍼티 표기법:**

$ [ { ][ a..z , A..Z ][ a..z , A..Z , 0..9 , - , _ ] _. [ a..z , A..Z ][ a..z , AZ , 0..9 , - , _ ]_ [ } ]

​

예:

  * 일반 표기법 : $customer.Address

  * 공식 표기법 : ${purchase.Total}

​​

**메서드 표기법:**

$ [ { ][ a..z , A..Z ][ a..z , A..Z , 0..9 , - , _ ] _. [ a..z , A..Z ][ a..z , A..Z , 0..9 , - , _ ] ( [ 선택적 매개변수 목록 ...* ] ) [ }_ *]

​

예:

  * 일반 표기법 : $customer.getAddress()

  * 공식 표기법 : ${purchase.getTotal()}

  * 매개변수 목록이 있는 일반 표기법 : $page.setTitle( "My Home Page" )

_​_

 _VTL 속성은 get_ 및 _set_ 을 사용하는 VTL 메서드에 대한 약식 표기법으로 사용할 수 있다._$object.getMethod()_ 또는 _$object.setMethod()는 $object.Method_ 로 축약될 수 있다. 일반적으로 가능한 경우 속성을 사용하는 것이 좋다. 속성과 메서드의 주요 차이점은 메서드에 매개 변수 목록을 지정할 수 있다.

​

​

3\. Velocity 디렉티브

[**#set**](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=set)**\- 참조 값 설정**

형식:

# [ { ] set [ } ] ( $ ref = [ " , ' ]arg[ " , ' ] )

​

용법:

  * _$ref_ \- 할당의 LHS는 변수 참조 또는 속성 참조여야 한다.

  * _arg_ \- 할당의 RHS, _arg_ 는 큰따옴표로 묶인 경우 구문 분석되고 작은따옴표로 묶인 경우 구문 분석되지 않는다.

​

예:

  * 변수 참조 : [#set](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=set)( $monkey = $bill )

  * 문자열 리터럴 : [#set](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=set)( $monkey.Friend = 'monica' )

  * 속성 참조 : [#set](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=set)( $monkey.Blame = $whitehouse.Leak )

  * 메서드 참조 : [#set](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=set)( $monkey.Plan = $spindoctor.weave($web) )

  * 숫자 리터럴 : [#set](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=set)( $monkey.Number = 123 )

  * 범위 연산자 : [#set](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=set)( $monkey.Numbers = [1..3] )

  * 개체 목록 : [#set](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=set)( $monkey.Say = ["Not", $my, "fault"] )

  * 개체 맵 : [#set](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=set)( $monkey.Map = {"banana" : "good", "roast beef" : "bad"})

​

RHS는 다음과 같은 간단한 산술 표현식일 수도 있다.

  * 덧셈 : [#set](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=set)( $value = $foo + 1 )

  * 빼기 : [#set](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=set)( $value = $bar - 1 )

  * 곱셈 : [#set](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=set)( $value = $foo * $bar )

  * 나누기 : [#set](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=set)( $value = $foo / $bar )

  * 나머지 : [#set](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=set)( $value = $foo % $bar )

​

**​**

[**#if**](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=if)**/#elseif/#else - 명령문의 참에 대한 조건부 출력**

형식:

# [ { ] if [ } ] ( [condition] ) [output] [# [ { ] elseif [ } ] ( [condition] ) [output] ]* [# [ { ] else [ } ] [output] ] # [ { ] end [ } ]

​

용법:

  * _condition_ \- 조건이 부울이면 true/false 일 때 true로 간주된다. 부울이 아니면 null이 아닌 경우 true로 간주된다.

  * _출력_ \- VTL을 포함할 수 있습니다.

오퍼레이터 이름 |  상징 |  대체 기호 |  예시  
---|---|---|---  
숫자와 같음 |  == |  eq |  #if( $foo == 42 )  
같음 문자열 |  == |  eq |  #if( $foo == "bar" )  
객체 동등성 |  == |  eq |  #if( $foo == $bar )  
같지 않음 |  != |  ne |  #if( $foo != $bar )  
보다 큰 |  > |  gt |  #if( $foo > 42 )  
미만 |  < |  lt |  #if( $foo < 42 )  
크거나 같음 |  >= |  ge |  #if( $foo >= 42 )  
작거나 같음 |  <= |  le |  #if( $foo <= 42 )  
부울 NOT |  ! |  not |  #if( !$foo )  
  
메모:

  1. == 연산자는 숫자, 문자열, 같은 클래스의 개체 또는 다른 클래스의 개체를 비교하는 데 사용할 수 있다. 마지막 경우(객체의 클래스가 다른 경우) 각 객체에 대해 toString() 메서드가 호출되고 결과 문자열이 비교된다.

  2. 대괄호를 사용하여 지시문을 구분할 수도 있다. 이것은 텍스트가 [#else](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=else) 지시문 바로 다음에 올 때 특히 유용하다.

​

​

[**#foreach**](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=foreach)**\- 객체 목록을 반복**

형식:

# [ { ] foreach [ } ] ( _$ref_ in _arg_ ) _statement_ # [ { ] end [ } ]

​

용법:

  * _$ref_ \- 첫 번째 변수 참조는 항목이다

  *  _arg_ \- 목록에 대한 참조(예: 객체 배열, 컬렉션 또는 맵), 배열 목록 또는 범위 연산자 중 하나일 수 있다.

  * _statement - Velocity가 위에 arg_ 로 표시된 목록에서 유효한 항목을 찾을 때마다 출력되는 내용이다. 이 출력은 유효한 VTL이며 루프가 반복될 때마다 렌더링 된다.

​

명령문 블록을 생략한 [#foreach](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=foreach)()의 예:

  * 참조 : [#foreach](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=foreach) ( $item in $items )

  * 배열 목록 : [#foreach](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=foreach) ( $item in ["Not", $my, "fault"] )

  * 범위 연산자 : [#foreach](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=foreach) ( $item in [1..3] )

​

Velocity는 루프 카운터를 얻는 쉬운 방법을 제공하므로 다음과 같은 작업을 수행할 수 있다.

<table> #foreach( $customer in $customerList ) <tr><td>$foreach.count</td><td>$customer.Name</td></tr> #end </table>

또한 루프 반복의 최대 허용 횟수는 엔진 전체에서 제어할 수 있다. 기본적으로 제한이 없다.

# 허용되는 최대 루프 수 directive.foreach.maxloops = -1

​

​

[**#include**](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=include)**\- Velocity로 구문 분석되지 않은 로컬 파일을 렌더링 한다.**

형식:

# [ { ] include [ } ] ( arg[ arg2 ... argn] )

​

용법:

  * _arg_ \- TEMPLATE_ROOT 아래의 유효한 파일을 참조한다.

​

예:

  * 문자열 : [#include](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=include)( "disclaimer.txt" "opinion.txt" )+

  * 변수 : [#include](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=include)( $foo $bar )

​

​

[**#parse**](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=parse)**\- Velocity로 구문 분석되는 로컬 템플릿을 렌더링 한다.**

형식:

# [ { ] parse [ } ] ( arg )

​

용법:

  * _arg_ \- TEMPLATE_ROOT 아래의 템플릿을 참조한다.

​

예:

  * 문자열 : [#parse](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=parse)( "lecorbusier.vm" )

  * 변수 : [#parse](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=parse)( $foo )

재귀가 허용된다. 구문 분석 깊이에서 변경하려면 _parse_directive.maxdepth_ 를 참조.

​

​

[**#stop**](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=stop)**\- 템플릿 엔진을 중지한다.**

형식:

# [ { ] stop [ } ]

​

용법:

이렇게 하면 현재 템플릿의 실행이 중지된다. 템플릿 디버깅에 유용하다.

​

​

[**#break**](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=break)**\- 현재 지시문 중지**

형식:

# [ { ] break [ } ]

​

용법:

이렇게 하면 현재 콘텐츠 지시문 실행이 중단된다. [#foreach](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=foreach) 루프를 일찍 종료하는 데 유용하지만 다른 범위에서도 작동한다. 특정 외부 범위에 대한 범위 제어 참조를 전달하여 지정된 범위 외부로 모든 범위의 실행을 중단할 수도 있다.

​

​

[**#evaluate**](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=evaluate)**\- 문자열이나 참조를 동적으로 평가**

형식:

# [ { ] evaluate [ } ] ( arg )

​

용법:

  * _arg_ \- 동적으로 평가할 문자열 리터럴 또는 참조입니다.

​

예:

  * 문자열 : [#evaluate](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=evaluate)( 'string with VTL [#if](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=if)(true)will be displayed#end' )

  * 변수 : [#evaluate](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=evaluate)( $foo )

​

​

[**#define**](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=define)**\- VTL 블록을 참조에 할당**

형식:

# [ { ] define [ } ] ( _$ref_ ) statement# [ { ] end [ } ]

​

용법:

  * _$ref_ \- VTL 블록이 값으로 할당된 참조.

  * _statement_ \- 참조에 할당된 명령문.

​

예시:

  * [#define](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=define)( $hello ) Hello $who [#end](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=end) [#set](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=set)( $who = "World!") $hello ## displays Hello World!

​

​

[**#macro**](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=macro)**\- 사용자가 필요에 따라 VTL 템플릿의 반복 세그먼트인 Velocimacro(VM)를 정의할 수 있다**

형식:

# [ { ] macro [ } ] ( vmname $arg1 [ $arg2 $arg3 ... $argn ] ) [ VM VTL code ... ] # [ { ] end [ } ]

​

용법:

  * _vmname_ \- VM을 호출하는 데 사용되는 이름( [_#vmname_](https://blog.naver.com/PostListByTagName.naver?blogId=agapeuni&encodedTagName=vmname) )

  * _$arg1 $arg2 [ ... ]_ \- VM에 대한 인수. 인수의 수에는 제한이 없지만 호출 시 사용된 수는 정의에 지정된 수와 일치해야 한다.

  * _[ VM VTL code... ]_ \- 템플릿에 넣을 수 있는 모든 유효한 VTL 코드를 VM에 넣을 수 있다.

​

정의된 VM은 템플릿의 다른 VTL 지시문처럼 사용된다.

#vmname( $arg1 $arg2 )

단 , 바디가 있는 VM을 호출하려면 VM 이름에 @를 접두사로 붙여야 한다. 해당 본문의 내용은 $!bodyContent를 통해 매크로 정의에서 원하는 만큼 여러 번 또는 몇 번 참조할 수 있다.

#@vmname( $arg1 $arg2 ) here is the body#end​

​

4\. Velocity 주석

주석은 런타임에 렌더링 되지 않는다. 주석을 사용하면 템플릿 엔진의 출력에 배치되지 않은 설명 텍스트를 포함할 수 있다. 주석은 자신을 상기시키고 VTL 문이 무엇을 하는지 다른 사람에게 설명하거나 유용하다고 생각하는 다른 목적을 설명하는 유용한 방법이다.

​

**한 줄 주석**

한줄 주석은 ## 시작한다.

## This is a comment.**

​

**여러 줄 주석**

#* This is a multiline comment. This is the second line. *#

​

**VTL 주석**

이 주석 블록은 템플릿에서 추적하려는 모든 종류의 추가 정보(예: javadoc 스타일 작성자 및 버전 정보)를 저장하는 데 사용할 수 있다.

#** This is a VTL comment block and may be used to store such information as the document author and versioning information: @author John Doe @version 5 *#

​

​

5\. 참조 URL

보다 자세한 내용은 아래의 URL을 참고한다.

​

<https://velocity.apache.org/engine/1.7/user-guide.html>

[ ![](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fwww.apache.org%2Fimages%2Fasf_logo.gif%22&type=ff120) ](https://velocity.apache.org/engine/1.7/user-guide.html) [ **Apache Velocity Engine - User Guide** User Guide - Contents User Guide - Contents About this Guide What is Velocity? What can Velocity do for me? The Mud Store Example Velocity Template Language (VTL): An Introduction Hello Velocity World! Comments References Variables Properties Methods Property Lookup Rules Rendering Index Notation Fo... velocity.apache.org ](https://velocity.apache.org/engine/1.7/user-guide.html)

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#Velocity #JavaTemplateEngine #JavaVelocity #템플릿엔진 #Java개발 #웹페이지템플릿 #Java웹개발 #Velocity사용법 #템플릿엔진활용 #동적웹페이지 #프론트엔드개발 #Velocity디렉티브 #Velocity문법 #템플릿언어 #웹개발 #Java템플릿 #동적컨텐츠생성 #Velocity프로퍼티 #Java프로퍼티 #Java템플릿코드 #템플릿문법 #웹템플릿엔진 #템플릿엔진설명 #VelocityTutorial #JavaVelocityTemplate #웹개발도구 #템플릿 #템플릿활용 #웹페이지코딩 #프로그래밍 #Java

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

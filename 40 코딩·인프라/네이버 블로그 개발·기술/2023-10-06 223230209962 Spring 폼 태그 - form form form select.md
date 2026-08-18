---
title: "2023-10-06 223230209962 Spring 폼 태그 - form form form select"
type: blog-archive
status: active
created: 2023-10-06
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223230209962&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223230209962
published: "2023. 10. 6. 23:47"
body_hash: fded416c259c427178270e43708f1962a30ba7c92cc67f40783c0e48f2f8a498
visibility: private
rag: exclude
---
# 2023-10-06 223230209962 Spring 폼 태그 - form form form select

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223230209962&categoryNo=982
- 게시일: 2023. 10. 6. 23:47

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTZfOTQg/MDAxNzQ0ODAzODExODkz._juObjNgonXzCPJsPnL5RjK3WZdlhu4nkuVywUgNP1Yg.j_4F2hoN1pUX--8G_Wb5iFPHfkeWj1_VOSZqI9CZgykg.PNG/Spring-001_\(8\).png?type=w80_blur)

​

스프링에서 Form을 사용할 경우 <fom:form>형태로 사용되는 form tag를 자주 보게 된다. 

스프링에서 제공하는 tag에 대해 간단히 정리해 본다. 

​

**1. <form:form> 태그**

spring 폼 태그를 사용하기 위해서는 spring-form.tld 파일이 필요하고 이는 spring-webmvc-2.5.2.jar 파일에 포함되어 있다. 이 폼 태그를 사용하기 위해서는 JSP 페이지에 taglib을 추가해 줘야 한다.

<%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>

'form'태그는 데이터 바인딩을 위해 태그 안에 바인딩 path를 지정해 줄 수 있다. 이 패스를 처음 보면 많이 이상한데 사용하다 보면 상당히 편한 기능이다. path에 해당되는 값은 도메인 모델의 Bean 객체를 의미한다.

사용 예는 다음과 같다.

<form:form commandName="user"> userId : <form:input path="userId" /> </form:form>

또한 spring form 태그를 이용하기 위해서는 각각의 입력 path 값에 매칭될 도메인 객체를 지정해 줘야 하는데 form 태그 안에 commandName 속성으로 다음과 같이 지정해 줄 수 있다.

<% request.setAttribute("user", sample.services.UserVO())%>

​

이러한 commandName의 기본값은 "command"이며 input 값들과 매칭될 도메인 객체를 request 값으로 세팅해 줘야 한다.

이 값은 SimpleFormController를 사용할 경우 FormBackingObject() 메서드에서 지정해 줄 수도 있다.

protected Object formBackingObject(HttpServletRequest request) throws Exception { UserVO vo = new UserVO(); request.setAttribute("user", vo); return new UserVO(); }

**2. <form:select> 태그 ******

select tag도 위의 checkboxes tag나 radiobuttons tag처럼

items 속성을 이용하여 formBackingObject에서 넘겨주는 값으로 자동 매핑 시켜줄 수 있다.

protected Object formBackingObject(HttpServletRequest request) throws Exception { UserVO vo = new UserVO(); Map address = new HashMap(); address.put("seoul", "서울"); address.put("daegu", "대구"); address.put("busan", "부산"); request.setAttribute("address", address); request.setAttribute("user", vo); return new UserVO(); }

​

HTML에서는 다음과 같이 사용한다.

<tr> <td>주소</td> <td><form:select path="address" items="${address}" /></td> </tr>

** <form:option> 태그 이용**

<tr> <td>주소</td> <td> <form:select path="address"> <form:option value="seoul" label="서울" /> <form:option value="daegu" label="대구" /> <form:option value="busan" label="부산" /> </form:select> </td> </tr>

**< form:options> 태그**

<tr> <td>주소</td> <td> <form:select path="address"> <form:options items="${address}" /> </form:select> </td> </tr>

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#Spring #SpringMVC #폼태그 #formTag #formForm #springFormTLD #데이터바인딩 #commandName #UserVO #formInput #formSelect #formOption #formOptions #HTML #웹개발 #JavaWeb #프로그래밍 #백엔드개발 #JSP #ModelBinding #SpringFramework #소프트웨어개발 #유저인터페이스 #프론트엔드 #스프링폼 #입력양식 #폼처리 #개발자 #IT기술 #개발블로그 #Java

![](https://postfiles.pstatic.net/MjAyMzEwMDZfMjI4/MDAxNjk2NjAzNDkzMDky.-y-5hpR8QbqU7BEvitSCrB9Eyc8jqsaPgspwlwRV3D0g.DgsJQavBctRl73KS6gx3_VvX60bOUG9p9BUM3mv5ju4g.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

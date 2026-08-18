---
title: "2023-07-17 223158399535 Spring 설정파일 - Spring 환경에서 ContextLoader 설정"
type: blog-archive
status: active
created: 2023-07-17
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223158399535&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223158399535
published: "2023. 7. 17. 12:24"
body_hash: d4096d3b23022e391c3c78e35d0a1bb6377e6fd694c35032e9950c49358999cb
visibility: private
rag: exclude
---
# 2023-07-17 223158399535 Spring 설정파일 - Spring 환경에서 ContextLoader 설정

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223158399535&categoryNo=982
- 게시일: 2023. 7. 17. 12:24

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTZfMjM2/MDAxNzQ0NzkxMjg3NTg2.36bbHjfEA85oCBFvIG3Z21nsId6Fqy4F54crIlChLJgg.52YB9UhnsawFOYRmDpyHdHFXPllL4yYD_LyD2T2D4zUg.PNG/Spring-001_\(1\).png?type=w80_blur)

​

Spring Framework를 웹 애플리케이션에 적용할 때, 애플리케이션 컨텍스트(ApplicationContext)를 초기화하기 위한 설정이 필요하다. 이 역할을 담당하는 주요 컴포넌트로는 ContextLoaderServlet과 ContextLoaderListener가 있으며, 사용하는 Servlet 스펙에 따라 등록 방식이 달라진다.

​

Servlet 2.3 스펙부터는 ContextLoaderListener를 지원하지만, 그 이전 버전에서는 이를 사용할 수 없기 때문에 ContextLoaderServlet을 사용해야 한다. 따라서, 보다 넓은 호환성을 확보하기 위해서는 ContextLoaderServlet을 사용하는 방식이 유리하다. 다만, 현재 사용하는 Servlet 버전에 따라 적절한 컴포넌트를 선택하여 등록하는 것이 중요하다.

​

​

**1\. ContextLoaderServlet 등록 (Servlet 2.2 이하 대응)**

Servlet 2.2 이전 스펙을 사용하는 경우에는 다음과 같이 web.xml에 ContextLoaderServlet을 등록한다. <load-on-startup> 설정은 해당 서블릿을 애플리케이션 시작 시점에 초기화하도록 지정한다.

<servlet> <servlet-name>context</servlet-name> <servlet-class> org.springframework.web.context.ContextLoaderServlet </servlet-class> <load-on-startup>1</load-on-startup> </servlet>

​

**2\. ContextLoaderListener 등록 (Servlet 2.3 이상)**

Servlet 2.3 이상의 스펙을 사용할 경우, 다음과 같이 ContextLoaderListener를 등록한다. 리스너 방식은 서블릿 컨텍스트의 생명주기를 감지하여 ApplicationContext를 보다 효율적으로 관리할 수 있다는 장점이 있다.

<listener> <listener-class> org.springframework.web.context.ContextLoaderListener </listener-class> </listener>

​

**3\. Spring 설정 파일 지정**

Spring 설정 파일은 contextConfigLocation 파라미터를 통해 지정할 수 있으며, 이는 공통적으로 다음과 같이 설정한다. 해당 파라미터는 Spring이 로딩할 설정 파일의 경로를 지정하는 역할을 하며, 일반적으로 WEB-INF 디렉토리 하위에 위치한 XML 파일을 지정한다.

<context-param> <param-value>contextConfigLocation</param-value> <param-value>/WEB-INF/chimera-services.xml</param-value> </context-param>

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#Servlet #ContextLoader #Spring #SpringFramework #JavaEE #웹개발 #Java개발 #ContextLoaderServlet #ContextLoaderListener #Servlet설정 #Spring설정 #JavaServlet #웹애플리케이션 #Java코드 #Spring부트 #Java프로그래밍 #웹서버 #스프링프레임워크 #JavaWeb #Java기술 #ServletAPI #SpringContext #XML설정 #서블릿 #ContextConfiguration #스프링설정파일 #Java개발자 #웹개발기술 #JavaEE개발 #Servlet2_3 #Spring프레임워크설정

![](https://postfiles.pstatic.net/MjAyMzA3MTdfMTE3/MDAxNjg5NTYyOTEyNTAz.BhCHOJCeavpXjusTZ4g7T22jV8HA-FUCrN_lYnSPr-Ag.VJ5fq4b7hRNy8R_mKgdCBZMlS2OfykFmSEsalz2QMvwg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

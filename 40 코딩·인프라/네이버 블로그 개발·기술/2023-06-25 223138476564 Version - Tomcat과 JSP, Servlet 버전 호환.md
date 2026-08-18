---
title: "2023-06-25 223138476564 Version - Tomcat과 JSP, Servlet 버전 호환"
type: blog-archive
status: active
created: 2023-06-25
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223138476564&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223138476564
published: "2023. 6. 25. 22:00"
body_hash: 4f771a78cf44596ada1c5022aed12e3822adc5c62c4e074a185f5c8ad1224d6a
visibility: private
rag: exclude
---
# 2023-06-25 223138476564 Version - Tomcat과 JSP, Servlet 버전 호환

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223138476564&categoryNo=982
- 게시일: 2023. 6. 25. 22:00

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTZfNjAg/MDAxNzQ0Nzg5NDAyNDYx.rqy8EyLxgOkb5EHmUFZuERsnypLf5dSsw673oOnKvJog.lgBa1hqzcqw6ENkBZBxuB7oslegxczfA2tWcdkc5CCEg.PNG/JSP-001_\(15\).png?type=w80_blur)

​

1\. 개요

Servlet, JSP, 그리고 Tomcat은 웹 애플리케이션 개발 및 실행을 위해 사용되는 기술이다. 이러한 기술들은 서로 다른 버전을 가질 수 있으며, 서버와 API 간의 호환성을 유지해야 한다. 개발 시에는 사용하는 Servlet, JSP 버전과 Tomcat 버전이 호환되는지 확인하는 것이 중요하다. 

​

​

2\. Servlet 버전

Servlet은 Java 웹 애플리케이션 개발을 위한 표준 API다. Servlet은 서버 측에서 동적인 웹 콘텐츠를 생성하고 처리하기 위해 사용된다. Servlet의 버전은 Servlet API의 버전을 나타낸다.

​

​

3\. JSP 버전

JSP(JavaServer Pages)는 서블릿 기반의 동적 웹 페이지를 작성하기 위한 기술이다. JSP는 HTML 코드에 Java 코드를 삽입하여 동적으로 콘텐츠를 생성할 수 있게 해준다. JSP 버전은 JSP 스펙의 버전을 나타낸다.

​

​

4\. Tomcat 버전

Apache Tomcat은 Java Servlet 및 JSP를 실행하기 위한 오픈 소스 웹 애플리케이션 서버다. Tomcat은 웹 애플리케이션을 실행하고 관리하는 역할을 수행한다. Tomcat 버전은 Apache Tomcat 서버의 릴리스 버전을 나타낸다. 

​

​

5\. 버전 호환 가이드라인

Tomcat 은 Servlet과 JSP 기술을 구현한 오픈소스 소프트웨어다. Servlet 및 JSP 버전은 Tomcat 버전과 관련된 호환성 가이드 라인을 따르는 것이 좋다. Tomcat 버전에 따라 적절한 Servlet과 JSP 사양의 버전을 선택해야 한다. 

서블릿 |  JSP |  EL |  웹소켓 |  인증 (JASIC) |  Apache Tomcat |  최신 버전 |  지원되는 Java 버전  
---|---|---|---|---|---|---|---  
6.1 |  4.0 |  6.0 |  TBD |  TBD |  11.0.x |  11.0.0-M7 |  21 and later  
6.0 |  3.1 |  5.0 |  2.1 |  3.0 |  10.1.x |  10.1.10 |  11 and later  
5.0 |  3.0 |  4.0 |  2.0 |  2.0 |  10.0.x |  10.0.27 |  8 and later  
4.0 |  2.3 |  3.0 |  1.1 |  1.1 |  9.0.x |  9.0.74 |  8 and later  
3.1 |  2.3 |  3.0 |  1.1 |  1.1 |  8.5.x |  8.5.90 |  7 and later  
3.1 |  2.3 |  3.0 |  1.1 |  N/A |  8.0.x |  8.0.53 |  7 and later  
3.0 |  2.2 |  2.2 |  1.1 |  N/A |  7.0.x |  7.0.109 |  6 and later  
2.5 |  2.1 |  2.1 |  N/A |  N/A |  6.0.x |  6.0.53 |  5 and later  
2.4 |  2.0 |  N/A |  N/A |  N/A |  5.5.x |  5.5.36 |  1.4 and later  
2.3 |  1.2 |  N/A |  N/A |  N/A |  4.1.x |  4.1.40 |  1.3 and later  
2.2 |  1.1 |  N/A |  N/A |  N/A |  3.3.x |  3.3.2 |  1.1 and later  
  
가능한 한 최신 안정 버전의 Tomcat을 사용하는 것이 좋지만 서블릿 사양과 JSP 사양과 지원되는 톰캣 버전을 확인해 보아야 한다. Tomcat 11이 출시되었지만 실무에서는 아직 Tomcat 10을 많이 사용하고 있다.

​

​

6\. 참고 URL

보다 자세한 정보는 공식페이지를 참조하자.

<https://tomcat.apache.org/whichversion.html>

[ **Apache Tomcat® - Which Version Do I Want?** Apache Tomcat Versions Apache Tomcat ® is an open source software implementation of a subset of the Jakarta EE (formally Java EE) technologies. Different versions of Apache Tomcat are available for different versions of the specifications. The mapping between the specifications and the respective Ap... tomcat.apache.org ](https://tomcat.apache.org/whichversion.html)

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#Servlet #JSP #Tomcat #Java웹개발 #웹애플리케이션 #ServletAPI #JSPAPI #ApacheTomcat #Tomcat버전 #서블릿버전 #JSP버전 #Tomcat호환성 #웹서버 #동적웹페이지 #Java개발 #서블릿기술 #JSP기술 #Tomcat설치 #Tomcat서버 #웹앱서버 #API호환성 #서버관리 #웹개발환경 #Java서블릿 #오픈소스웹서버 #JSP페이지 #Java웹서버 #Tomcat최신버전 #웹소켓 #Tomcat설정 #Java버전

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

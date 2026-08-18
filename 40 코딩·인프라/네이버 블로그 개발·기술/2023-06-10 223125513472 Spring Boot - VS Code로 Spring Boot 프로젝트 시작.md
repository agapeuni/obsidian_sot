---
title: "2023-06-10 223125513472 Spring Boot - VS Code로 Spring Boot 프로젝트 시작"
type: blog-archive
status: active
created: 2023-06-10
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223125513472&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223125513472
published: "2023. 6. 10. 23:53"
body_hash: 1f5478c80bc4519a3e28752dacf7e19f285b8f23b9ef2d641869eda291ec77ae
visibility: private
rag: exclude
---
# 2023-06-10 223125513472 Spring Boot - VS Code로 Spring Boot 프로젝트 시작

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223125513472&categoryNo=982
- 게시일: 2023. 6. 10. 23:53

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTlfMjQ5/MDAxNzQ1MDE1NTc0NjEx.K9kbe2IBe7y8mTGyHIQM_AjnQg_4K1PGUb9bpY_qr9Ig._klq82kF5H1ahcFj1gIbRKdD4XANY6KhAIB9319awnEg.PNG/%EA%B0%9C%EB%B0%9C%ED%99%98%EA%B2%BD-001_\(16\).png?type=w80_blur)

​

1\. Visual Studio Code

개인적으로는 Spring Tool Suite 보다 Visual Studio Code가 가볍고 빠르게 느껴진다. Visual Studio Code가 개발자를 위한 여러 가지 기능들을 지원하고 있어 작업하는데 많은 편리함을 제공한다. Visual Studio Code에서 Spring Boot를 실행하기 위해 "Java Extensions Pack"과 "Spring Boot Extention Pack"을 설치한다.

​

먼저 "Java Extention Pack"을 설치한다. "Java Extention Pack"은 Java 개발에 필요한 기능을 지원한다.

![](https://postfiles.pstatic.net/MjAyMzA2MTBfMTY3/MDAxNjg2NDA4NTY2NzEz.CbR4tHZIzdWlM5zoDQGMyHVoYP6pW2lmvn8YM0BGRM4g.RToGe-4RdyUxjuAmRn5kTLDhDa3L2IJGEYWvqs-qvWcg.PNG.agapeuni/img.png?type=w80_blur)

​

"Spring Boot Extension Pack"은 Spring Boot 애플리케이션 개발을 용이하게 할 수 있는 확장 팩입니다. 이 팩은 Spring Boot 애플리케이션을 개발하고 관리하기 위한 여러 유용한 도구와 기능을 제공한다.

![](https://postfiles.pstatic.net/MjAyMzA2MTBfMjYx/MDAxNjg2NDA4NTQwMzI3.JaV-_ZVr1JWFKCWreev_G1_ZtnV-ukj9iEhzACU90x8g.R-ThTxaJ2oO3sKRJfMd28AnFU7AoTKiOynUZpTvrU38g.PNG.agapeuni/img.png?type=w80_blur)

​

​

2\. Spring Boot

Spring Boot는 Java 애플리케이션을 빠르고 쉽게 개발하기 위한 도구다. Spring Boot는 Java 기술과 Spring 프레임워크의 기능을 활용하여 스프링 애플리케이션을 간편하게 구축할 수 있도록 도와준다. 개발자는 복잡한 설정 작업 없이도 빠르게 실행 가능한 독립적인 애플리케이션을 개발할 수 있다.

​

Spring Boot는 애플리케이션의 클래스 패스와 설정을 기반으로 자동 구성을 제공한다. 이는 개발자가 별도의 설정 없이도 애플리케이션을 시작할 수 있다. Spring Boot는 설정을 위한 기본적인 의견을 제공한다. 개발자가 쉽게 설정을 변경하거나 대체할 수 있다.

​

Spring Boot는 Tomcat, Jetty, Undertow와 같은 내장 서버를 제공하여 애플리케이션을 독립적으로 실행할 수 있다. Spring Boot는 JUnit 또는 기타 테스트 프레임워크와 통합하여 테스트를 작성하고 실행하기 용이하도록 지원한다.

​

​

3\. Spring Initializr

Spring Initializr는 Spring Boot 프로젝트를 시작하기 위한 웹 기반 도구다. 이 도구를 사용하면 Spring Boot 프로젝트의 초기 설정을 쉽게 생성할 수 있고 프로젝트의 기본 구성을 선택할 수 있다. 프로젝트의 빌드 도구 (Maven 또는 Gradle), 프로젝트 언어 (Java, Kotlin), 스프링 부트 버전 등을 선택할 수 있다.

​

사용하려는 기술 스택에 맞게 필요한 의존성을 선택하여 프로젝트에 추가할 수 있다. 예를 들어, 웹 애플리케이션을 개발하려면 Spring Web 의존성을 추가할 수 있다. 이렇게 선택된 의존성은 프로젝트의 pom.xml (Maven) 또는 build.gradle (Gradle) 파일에 자동으로 추가된다.

​

Spring Initializr는 [https://start.spring.io/](https://start.spring.io/%C2%A0) 에서 웹으로 사용가능 하다. 이 웹 사이트에서는 상기 언급된 기능들을 사용하여 새로운 Spring Boot 프로젝트를 빠르게 생성할 수 있다. 설정된 프로젝트는 IDE에서 가져와 추가적인 개발 및 구현을 시작할 수 있다.

​

Spring Initializr에서 다음과 같이 항목을 선택하고 "GENERATE" 버튼을 클릭하여 파일을 다운로드한다. "EXPLORE" 버튼을 클릭하면 코드를 브라우저에서 미리 확인할 수 있다.

![](https://postfiles.pstatic.net/MjAyMzA2MTBfMjYx/MDAxNjg2NDA4NTQ0NjI4.sqJ99f5hbVqhe9S3mR9Ir0G-XclgYKeH9lUdr6R6xqcg.nd0u9M477GlLTo396Edr2of_Ff5p5KTeeXXYOVYQI20g.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA2MTBfMjkz/MDAxNjg2NDA4NTUwNzkw.MRMcNzQDRreGQi_nVq2b7t8yiMuqkXpvKbS33aItcxQg.GaLX2eEy0ipxt2411Gdat_wDgRyHhx-M_p0PRgHOzwIg.PNG.agapeuni/img.png?type=w80_blur)

​

​

4\. VS Code에서 열기

내려받은 압축파일을 적당한 위치에 압축 해제하고 VS Code에서 해당 폴더를 오픈한다. 기본적인 소스코드와 pom.xml도 담겨있다.

![](https://postfiles.pstatic.net/MjAyMzA2MTBfMjAy/MDAxNjg2NDA4NTYyNTgy.UOvQdPHDjhyaH1iqHq635gP9_3dJ_YMd3Or3xh6pGcQg.pZB8UmBQ0KygQwz58W2sesqzsWDcpnoJAOcmzNWXR60g.PNG.agapeuni/img.png?type=w80_blur)

​

​

5\. Spring Boot 실행

DemoApplication 클래스를 열고 실행을 하면 Spring Boot가 정상적으로 실행된다.

![](https://postfiles.pstatic.net/MjAyMzA2MTBfMTQ1/MDAxNjg2NDA4NTcwMTU5.CqxlkDpIOhPgRmXSP-pTqpW_VLKpTJmX9dr2Jlq7oQog.TBH32qjwtGUJXo0cQzvADPe_qKI625WO3E-TjMbwQ6Ig.PNG.agapeuni/img.png?type=w80_blur)

​

DemoApplication 클래스에 @RestController 어노테이션을 추가한다. "/hello"를 위한 메서드를 만들어 "Hello Spring Boot" 문자열을 반환한다.

package com.example.demo; import org.springframework.boot.SpringApplication; import org.springframework.boot.autoconfigure.SpringBootApplication; import org.springframework.web.bind.annotation.GetMapping; import org.springframework.web.bind.annotation.RestController; @SpringBootApplication @RestController public class DemoApplication { public static void main(String[] args) { SpringApplication.run(DemoApplication.class, args); } @GetMapping("/hello") public String hello() { return "Hello Spring Boot"; } }

​

브라우저에서 확인해 보자.

<http://localhost:8080/hello>

![](https://postfiles.pstatic.net/MjAyMzA2MTBfMTAz/MDAxNjg2NDA4NTc0ODA5.xJHdA5zYq7GJ12GtcQsyMrhKaXqRRgYwL_afKhbvYL4g.c3I8HpQL6-5eEi9DmDSCI69IwJll8djzLLpQ4kqYx7og.PNG.agapeuni/img.png?type=w80_blur)

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#비주얼스튜디오코드 #VSCode #스프링부트 #스프링이니셜라이저 #자바 #스프링툴스위트 #자바익스텐션팩 #스프링부트익스텐션팩 #스프링프레임워크 #스프링웹 #스프링애플리케이션 #스프링REST컨트롤러 #톰캣 #제티 #언더토우 #메이븐 #그레이들 #JUnit #IDE #자바개발 #웹애플리케이션 #스프링설정 #스타트스프링IO #스프링프로젝트 #데모애플리케이션 #소프트웨어개발 #백엔드개발 #스프링통합 #코드에디터 #프로그래밍 #RESTAPI

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

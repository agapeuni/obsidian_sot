---
title: "2023-10-07 223230261386 SpringBoot - Gradle 프로젝트 생성부터 HelloController 까지"
type: blog-archive
status: active
created: 2023-10-07
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223230261386&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223230261386
published: "2023. 10. 7. 1:12"
body_hash: fb66a3c3c86b09f074e40f8675d1f65a24afe35da74a5d4234a9f0fbf1995981
visibility: private
rag: exclude
---
# 2023-10-07 223230261386 SpringBoot - Gradle 프로젝트 생성부터 HelloController 까지

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223230261386&categoryNo=982
- 게시일: 2023. 10. 7. 1:12

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTZfNTMg/MDAxNzQ0ODA0MDE1NjE0.oCTmh70uzp_zSHh1KzUnxB5YcDnzQ-WLdx604vae-iQg.IOrP0XfwDT5aB5C9qHZ10mEsXZ3e_YulzrecEe9ANK4g.PNG/Spring-001_\(10\).png?type=w80_blur)

​

신규 프로젝트를 생성하기 위해 "Create New Project"를 선택한다.

![](https://postfiles.pstatic.net/MjAyMzEwMDdfNTQg/MDAxNjk2NjA4NTg2Njc3.CbhMs4IXBKtLKimlqRYdFUg6SylIEE0GVqXlbsvpKgsg.UYfwDz0saTXampz1peIjfFHC_ptEcdWlujuR2hBDBzkg.PNG.agapeuni/img.png?type=w80_blur)

​

"Gradle - Java"를 선택하고 "Next" 클릭.

![](https://postfiles.pstatic.net/MjAyMzEwMDdfMTIx/MDAxNjk2NjA4NTkwOTE5.JKxt7JYvHRBNlruvnMWsOhL19sNIyA6mX_Fud8XQD6Qg.9vf2CekmzCDQnxCTuNw9yWhVyk3v6NjOcV42JPCkDXEg.PNG.agapeuni/img.png?type=w80_blur)

​

다음과 같이 프로젝트 정보를 입력하고 "Finish"를 클릭.

![](https://postfiles.pstatic.net/MjAyMzEwMDdfNDEg/MDAxNjk2NjA4NTk0NzU3.W5-afS-DotCOFESMIxnXzeE5k_nDjZCcl4GGh4KDPrUg.rMq2zFEL6RDYfeLQGSmJSzQjCREQG1zdiz0AbH54V2cg.PNG.agapeuni/img.png?type=w80_blur)

​

얼마간의 시간이 지나면 아래와 같이 프로젝트 환경이 구성된다.

![](https://postfiles.pstatic.net/MjAyMzEwMDdfMjI4/MDAxNjk2NjA4NTk4NjQz.wBEzdJaS8yOvvZw143hg6vbYJ6oo4e2IF7wjoiB24p8g.W24-ENTn6H74wo6EyUxuZ5freguWLdj15S6RpKrmsWAg.PNG.agapeuni/img.png?type=w80_blur)

​

build.gradle

buildscript { ext { springBootVersion = '2.1.9.RELEASE' } repositories { mavenCentral() jcenter() } dependencies { classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}") } } apply plugin: 'java' apply plugin: 'eclipse' apply plugin: 'org.springframework.boot' apply plugin: 'io.spring.dependency-management' group 'org.oneway' version '1.0-SNAPSHOT' sourceCompatibility = 1.8 repositories { mavenCentral() jcenter() } dependencies { compile('org.springframework.boot:spring-boot-starter-web') testCompile('org.springframework.boot:spring-boot-starter-test') }

​

![](https://postfiles.pstatic.net/MjAyMzEwMDdfMTA5/MDAxNjk2NjA4NjM4Mjkx.im6YPMRvK7xcIuIGMQm8D7aJKMnTI7Ma_ly8qEMRm0wg.5gIuAoWpqqcXSPEGjdPcKOHG8Dtx2dmIcMw6bg94Th8g.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzEwMDdfMjg1/MDAxNjk2NjA4NjQ0MDM0.rXGn2YOMZyYBvjwQNbnsEWs9xc411bKpBC0ZudB82LYg.CsFmfhtuG8cdUto7s6j80-cOoYcNN1gtPMQt6atfLOQg.PNG.agapeuni/img.png?type=w80_blur)

​

build.gradle을 저장하고 환경 구성이 완료되면 Gradle Dependencies에서 확인할 수 있다.

![](https://postfiles.pstatic.net/MjAyMzEwMDdfMzgg/MDAxNjk2NjA4NjQ4NDk5.OhhFy9oqOg6v0Wdigpc7vvoSYf_8FYzFnujo6l-u76Mg.p851w11MQJBzruTHwuMH1rB_vGDB5eX6GOC9qwZWDC4g.PNG.agapeuni/img.png?type=w80_blur)

​

Spring Boot를 실행하기 위한 Application 클래스 생성

package com.oneway; import org.springframework.boot.SpringApplication; import org.springframework.boot.autoconfigure.SpringBootApplication; @SpringBootApplication public class Application { public static void main(String[] args) { SpringApplication.run(Application.class, args); } }

![](https://postfiles.pstatic.net/MjAyMzEwMDdfMTQw/MDAxNjk2NjA4NjY0NDcx.6rqVxtcrR8W0u9xYdNGCynDoruMMZyJH5CDufKd-bVAg.lK2jNkQt9VUTNAB5NOQwF4cwD6DXnSR72GQjLvtSOskg.PNG.agapeuni/img.png?type=w80_blur)

​

"Hello SpringBoot"를 리턴하는 HelloController 클래스 생성하고 실행.

package com.oneway.web; import com.oneway.web.dto.HelloResponseDto; import org.springframework.web.bind.annotation.GetMapping; import org.springframework.web.bind.annotation.RequestParam; import org.springframework.web.bind.annotation.RestController; @RestController public class HelloController { @GetMapping("/hello") public String hello() { return "Hello SpringBoot"; } @GetMapping("/hello/dto") public HelloResponseDto helloDto(@RequestParam("name") String name, @RequestParam("age") int age) { return new HelloResponseDto(name, age); } }

![](https://postfiles.pstatic.net/MjAyMzEwMDdfMTUz/MDAxNjk2NjA4Njg3MDEw.WuUnCePChhONyiQXBNoNk8lToT85E2XmEu2yPGk8WZog.tUfs5jtkG6rnSt414ZwjER5_yMhTlZbta7V2ZteDlssg.PNG.agapeuni/img.png?type=w80_blur)

​

**HelloControllerTest 코드**

package com.oneway.web; import org.junit.Test; import org.junit.runner.RunWith; import org.springframework.beans.factory.annotation.Autowired; import org.springframework.boot.test.autoconfigure.web.servlet.WebMvcTest; import org.springframework.test.context.junit4.SpringRunner; import org.springframework.test.web.servlet.MockMvc; import static org.hamcrest.Matchers.is; import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.get; import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.*; @RunWith(SpringRunner.class) @WebMvcTest public class HelloControllerTest { @Autowired private MockMvc mvc; @Test public void testHello() throws Exception { String hello = "Hello SpringBoot"; mvc.perform(get("/hello")) .andExpect(status().isOk()) .andExpect(content().string(hello)); } @Test public void testHelloDto() throws Exception { String name = "OneWay"; int age = 47; mvc.perform( get("/hello/dto").param("name", name).param("age", String.valueOf(age))) .andExpect(status().isOk()) .andExpect(jsonPath("$.name", is(name))) .andExpect(jsonPath("$.age", is(age))); } }

![](https://postfiles.pstatic.net/MjAyMzEwMDdfOTMg/MDAxNjk2NjA4NzA3Njc0.DdwrclPJyqew6-PABQk3iE1Fz-HOwfk8CK3tjbHWwcYg.8RDXp2CTLhl1jC-y8GuS91iOHrUxq6tOTxlLdnsEREAg.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzEwMDdfOTcg/MDAxNjk2NjA4NzExODc4.GH7VYLcTUl2rvDpEgwphiCCX0UOJLxUYsMw1ybAxQDgg.xNpFC_4rEKe5Mm0U3qrZTINbdJ5Vm0mQgl_Y_pDSYHUg.PNG.agapeuni/img.png?type=w80_blur)

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#SpringBoot #Gradle #Java #웹개발 #SpringFramework #Application #HelloWorld #RESTAPI #컨트롤러 #테스트코드 #JUnit #MockMvc #API개발 #스프링부트프로젝트 #GradleDependencies #SpringBootStarter #SpringBootApplication #HelloController #DTO #코드리뷰 #프로그래밍 #소프트웨어개발 #백엔드개발 #IT기술 #프로그래밍블로그 #개발자 #SpringBootTest #API테스트 #개발환경설정 #SpringMVC

![](https://postfiles.pstatic.net/MjAyMzEwMDdfMjA3/MDAxNjk2NjA4MzgxNTk1.R412gcM4cYW0GDhNYnttZ9D4NMvsaA6hzm8lQw1i97Qg.MT3-gN1RF-531qrwRqBvI6uGOuliFIVONqq1C4WrPucg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

---
title: "2023-07-17 223158932421 Spring MVC - 애플리케이션 만들기, View와 Controller"
type: blog-archive
status: active
created: 2023-07-17
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223158932421&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223158932421
published: "2023. 7. 17. 23:16"
body_hash: 9a7e4d1208f342b5f8803d3e40dd134eae39383969340c6c7c743af58a28cd2a
visibility: private
rag: exclude
---
# 2023-07-17 223158932421 Spring MVC - 애플리케이션 만들기, View와 Controller

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223158932421&categoryNo=982
- 게시일: 2023. 7. 17. 23:16

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTZfMjQy/MDAxNzQ0ODAzNTQ2MDUw.nFuWvfmbpCMS-tOVdjiQ9QvB1K2S-pR1BY02VgMneWkg.ET_CcLgPlZND1b4tc8gIzprTPaUzhfK18l4W3VVpGwgg.PNG/Spring-001_\(4\).png?type=w80_blur)

​

**1\. JSTL 설정과 JSP 헤더 파일 추가**

JSTL을 사용하여 View를 구성하게 될 것이므로, spring-framework-2.5/lib/j2ee 폴더에 있는 jstl.jar 와 jakarta-taglibs 폴더에 있는 standard.jar 파일을 /WEB-INF/lib 폴더에 복사한다. 

​

이제, 모든 jsp 페이지에 포함하게 될 헤더 파일을 만들어보자. 사용하게 될 태그 라이브러리를 설정하는 단순한 include 파일이다. /WEB-INF 폴더 아래 /jsp 폴더 생성해서 모든 jsp 파일은 이곳으로 놓게 될 것이다. 이러한 형태는 애플리케이션 서버에 따라 적용이 안될 수도 있다. /WEB-INF/jsp로 구성할 수 없는 서버에서는 그냥 해당 context에 /jsp 폴더를 만들어서 해도 된다.

/WBE-INF/jsp/include.jsp 파일

<%@ page session="false"%> <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %> <%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>

파일을 저장한 후, 프로젝트 Refresh. 이전 만들었던 index.jsp 파일을 jstl을 이용하도록 수정한다. 

<%@ include file="/WEB-INF/jsp/include.jsp" %> <c:redirect url="/hello.htm"/>

hello.jsp 파일을 /WEB-INF/jsp 폴더로 옮긴다. 

index.jsp와 동일하게 헤더 파일 include.

<c:out/> JSTL 태그를 사용해서 model에서 전달받은 현재 시간을 출력한다. 

<%@ include file="/WEB-INF/jsp/include.jsp" %> <html> <head><title>Hello :: Spring Application</title></head> <body> <h1>Hello - Spring Application</h1> <p>Greetings, it is now <c:out value="${now}"/></p> </body> </html>

**2\. Controller 만들기**

컨트롤러를 수정하기 전에, 이전 만들었던 테스트를 먼저 수정해서 확인해 본다.

package springapp.web; import org.springframework.web.servlet.ModelAndView; import springapp.web.HelloController; import junit.framework.TestCase; public class HelloControllerTests extends TestCase { public void testHandleRequestView() throws Exception { HelloController controller = new HelloController(); ModelAndView modelAndView = controller.handleRequest(null, null); assertEquals("WEB-INF/jsp/hello.jsp", modelAndView.getViewName()); assertNotNull(modelAndView.getModel()); String nowValue = (String) modelAndView.getModel().get("now"); assertNotNull(nowValue); } }

HelloController를 수정한다.

hello.jsp 파일의 경로가 달라졌고, 시간을 생성해서 now로 매핑해서 ModelAndView를 리턴한다.

package springapp.web; import org.springframework.web.servlet.mvc.Controller; import org.springframework.web.servlet.ModelAndView; import javax.servlet.ServletException; import javax.servlet.http.HttpServletRequest; import javax.servlet.http.HttpServletResponse; import org.apache.commons.logging.Log; import org.apache.commons.logging.LogFactory; import java.io.IOException; import java.util.Date; public class HelloController implements Controller { protected final Log logger = LogFactory.getLog(getClass()); public ModelAndView handleRequest(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException { String now = (new Date()).toString(); logger.info("Returning hello view with " + now); return new ModelAndView("WEB-INF/jsp/hello.jsp", "now", now); } }

**3\. 컨트롤러에서 뷰 분리하기**

HelloController에서 뷰의 URL이 포함되어서 구현되어 있지만, 이를 분리할 필요가 있다.

springapp-servlet.xml 파일 수정하기. 

<?xml version="1.0" encoding="UTF-8"?> <beans xmlns="http://www.springframework.org/schema/beans" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-2.0.xsd"> <!-- the application context definition for the springapp DispatcherServlet --> <bean name="/hello.htm" class="springapp.web.HelloController"/> <bean id="viewResolver" class="org.springframework.web.servlet.view.InternalResourceViewResolver"> <property name="viewClass" value="org.springframework.web.servlet.view.JstlView"></property> <property name="prefix" value="/WEB-INF/jsp/"></property> <property name="suffix" value=".jsp"></property> </bean> </beans>

테스트를 위해 HelloControllerTests.java 파일 수정 

package springapp.web; import org.springframework.web.servlet.ModelAndView; import springapp.web.HelloController; import junit.framework.TestCase; public class HelloControllerTests extends TestCase { public void testHandleRequestView() throws Exception { HelloController controller = new HelloController(); ModelAndView modelAndView = controller.handleRequest(null, null); assertEquals("hello", modelAndView.getViewName()); assertNotNull(modelAndView.getModel()); String nowValue = (String) modelAndView.getModel().get("now"); assertNotNull(nowValue); } }

HelloController.java 

package springapp.web; import org.springframework.web.servlet.mvc.Controller; import org.springframework.web.servlet.ModelAndView; import javax.servlet.ServletException; import javax.servlet.http.HttpServletRequest; import javax.servlet.http.HttpServletResponse; import org.apache.commons.logging.Log; import org.apache.commons.logging.LogFactory; import java.io.IOException; import java.util.Date; public class HelloController implements Controller { protected final Log logger = LogFactory.getLog(getClass()); public ModelAndView handleRequest(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException { String now = (new Date()).toString(); logger.info("Returning hello view with " + now); return new ModelAndView("hello", "now", now); } }

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#JSTL #스프링프레임워크 #JSP헤더파일 #동적웹페이지 #HelloController #모델과뷰 #웹개발 #자바개발 #스프링MVC #애플리케이션구성 #indexjsp #hellojsp #컨트롤러개발 #테스트유닛 #JUnit #웹XML설정 #JSTL설정 #jsp태그라이브러리 #SpringApplication #ViewResolver #내부리소스뷰리졸버 #프로그래밍 #Spring #JavaWebDevelopment #ModelAndView #실시간출력 #개발자 #스프링기초 #웹프레임워크 #애플리케이션개발 #JSP파일

![](https://postfiles.pstatic.net/MjAyMzA3MTdfMTA5/MDAxNjg5NTk4NzI4NDk5.LXG8QSAnx4ER5fVh3ghOTDsbLoDU0Jq4QyQOIGI7y4cg.VHAB3KYLsPDmqV4K6CVGxkRgETs0_0QgXaMzhra_Tt8g.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

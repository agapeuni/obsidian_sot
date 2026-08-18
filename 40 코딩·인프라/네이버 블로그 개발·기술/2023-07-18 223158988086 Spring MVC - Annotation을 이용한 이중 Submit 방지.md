---
title: "2023-07-18 223158988086 Spring MVC - Annotation을 이용한 이중 Submit 방지"
type: blog-archive
status: active
created: 2023-07-18
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223158988086&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223158988086
published: "2023. 7. 18. 3:00"
body_hash: 0a3cc006865b31b96348d179997fca63911add71a9aabb60f23d465156b66061
visibility: private
rag: exclude
---
# 2023-07-18 223158988086 Spring MVC - Annotation을 이용한 이중 Submit 방지

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223158988086&categoryNo=982
- 게시일: 2023. 7. 18. 3:00

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTZfMTc2/MDAxNzQ0ODAzNTkyNjAz.uG8nJGXGXkN1sl2z_E5dZckulxsk2Fm-_WNqjArUpSIg.twEPmKEb7-GbgtZ0IJCVuNfBBmIkTMbax_6FxdtWHjog.PNG/Spring-001_\(5\).png?type=w80_blur)

​

Spring MVC에서는 이중 submit을 방지하기 위해 AbstractFormController를 제공한다. 폼 컨트롤러를 구현 시에 사용하는 SimpleFormController 또한 AbstractFormController를 상속받았기 때문에 위와 같은 처리가 가능하다. 

Annotation을 사용하여 다른 클래스를 상속받지 않고도 double submit 방지 기능을 구현하는 방법에 대해서 자세히 알아본다. Annotation을 이용한 Double Submit 방지는 다음과 같은 원리로 구현된다.

**■ Double submission을 방지하고자 하는 form 객체를 model로 저장**

다음 예제와 같이 ModelAndView, ModelMap 등을 이용하여 저장한다.

@RequestMapping(params = "param=addView") public ModelAndView addUserView() { ModelAndView mnv = new ModelAndView("/jsp/user/userForm.jsp"); mnv.addObject("user", new User()); return mnv; } @RequestMapping(params = "param=addView") public String addUserView(ModelMap map) { map.addAttribute("user", new User()); return "/jsp/user/userForm.jsp"; }

​

**■ 저장한 model을 @SessionAttributes로 정의**

다음 예제와 같이 컨트롤러 클래스 선언부에 @SessionAttributes("user")로 정의한다.

@Controller @RequestMapping("/user.do") @SessionAttributes("user") public class EditUserController { ...중략... }

​

**■ 컨트롤러 메서드에서 폼 처리 완료 후 Session status 변경**

@RequestMapping(params = "param=add") public String addUser(HttpServletRequest request, @ModelAttribute("user") User user, BindingResult result, SessionStatus status) throws Exception { userService.addUser(user); status.setComplete(); return "/userList.do"; }

​

**■ status.setComplete()는 session에서 저장된 model을 삭제하는 이벤트 발생**

따라서, 이후에 다시 submit 요청이 온 경우 session에 저장된 model이 삭제되었기 때문에 

아래와 같이 org.springframework.web.HttpSessionRequiredException 발생

org.springframework.web.HttpSessionRequiredException: Session attribute 'dept' required - not found in session

​

**■ 단, 여러 thread가 동시에 Session에 접근할 수 있는 경우**

반드시 AnnotationMethodHandlerAdapter의 synchronizeOnSession 속성을 true로 설정해야만 위와 같은 결과를 얻을 수 있다.

<bean id="annotationHandlerAdaptor" class="org.springframework.web.servlet.mvc.annotation.AnnotationMethodHandlerAdapter"> <property name="synchronizeOnSession" value="true" /> </bean>

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#SpringMVC #DoubleSubmit방지 #AbstractFormController #SimpleFormController #모델저장 #ModelAndView #ModelMap #@SessionAttributes #EditUserController #SessionStatus #BindingResult #유저폼 #스프링안노테이션 #HTTP요청 #SpringFramework #웹개발 #JavaWebDevelopment #SpringController #폼처리 #HttpSessionRequiredException #동시성제어 #스프링구성 #AnnotationMethodHandlerAdapter #웹프레임워크 #자바개발 #웹애플리케이션 #유저관리 #세션관리 #서버사이드 #개발자 #프로그래밍

![](https://postfiles.pstatic.net/MjAyMzA3MTdfMTE4/MDAxNjg5NjAyMTIyNjY2.f9HPwqLeB4gAKc4PKvjZNgW-SWxIySp5m92llB-nGaog.CuZGS8jYP8BdAhgA5vIuhokl3OpnBVZygI4uS7xE3PYg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

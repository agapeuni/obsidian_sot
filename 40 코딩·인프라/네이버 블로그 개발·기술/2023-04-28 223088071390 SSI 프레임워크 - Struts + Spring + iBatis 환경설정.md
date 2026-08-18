---
title: "2023-04-28 223088071390 SSI 프레임워크 - Struts + Spring + iBatis 환경설정"
type: blog-archive
status: active
created: 2023-04-28
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223088071390&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223088071390
published: "2023. 4. 28. 21:14"
body_hash: c3eba66f1bfb6659f75b815ee7427726f7e03ba167984b253b95e8f459ec3f01
visibility: private
rag: exclude
---
# 2023-04-28 223088071390 SSI 프레임워크 - Struts + Spring + iBatis 환경설정

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223088071390&categoryNo=982
- 게시일: 2023. 4. 28. 21:14

## 본문

![](https://postfiles.pstatic.net/MjAyMzA2MzBfMjg0/MDAxNjg4MTE1MjI2NDAw.SHtdB037a8v0OfAtkAx3aNDxuyAnSN7mLSU_qaoLQegg.eAWUVtUngaB0w5v5kt-J1324W_2927GBDlNg0GgkHsgg.PNG.agapeuni/Front_End-001_\(8\).png?type=w80_blur)

​

아주 오래전에 프로젝트 진행할 때 Struts를 사용하기도 했다. 

그런 레거시 시스템이 아직까지 살아남아 골동품처럼 관리되고 있는 현장도 있다.

​

**▣ /webroot/WEB-INF/web.xml**

web.xml에 Struts와 Spring 설정을 한다. 

<?xml version="1.0" encoding="UTF-8"?> <web-app version="2.4" xmlns="http://java.sun.com/xml/ns/j2ee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://java.sun.com/xml/ns/j2ee http://java.sun.com/xml/ns/j2ee/web-app_2_4.xsd"> <display-name>Struts Demo</display-name> <!-- struts2 --> <filter> <filter-name>struts</filter-name> <filter-class>org.apache.struts2.dispatcher.FilterDispatcher</filter-class> </filter> <filter-mapping> <filter-name>struts</filter-name> <url-pattern>/*</url-pattern> </filter-mapping> <!-- spring --> <listener> <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class> </listener> <context-param> <param-name>contextConfigLocation</param-name> <param-value>/WEB-INF/config/applicationContext*.xml</param-value> </context-param> <!-- welcome --> <welcome-file-list> <welcome-file>index.jsp</welcome-file> <welcome-file>index.html</welcome-file> </welcome-file-list> </web-app>

**▣ /webroot/WEB-INF/src/struts.properties**

Struts 프로퍼티

struts.locale=ko_KR struts.devMode=true struts.i18n.reload=true struts.configuration.xml.reload=true struts.continuations.package = org.apache.struts2.showcase struts.custom.i18n.resources=globalMessages #struts.action.extension=action struts.url.http.port = 8088 #struts.freemarker.manager.classname=customFreemarkerManager struts.serve.static=true struts.serve.static.browserCache=false # struts.multipart.parser=cos # struts.multipart.parser=pell struts.multipart.parser=jakarta # uses javax.servlet.context.tempdir by default struts.multipart.saveDir= struts.multipart.maxSize=2097152 #struts.objectFactory=org.apache.struts2.spring.StrutsSpringObjectFactory

**▣ /webroot/WEB-INF/src/struts.xml**

Struts 설정 파일

<?xml version="1.0" encoding="UTF-8" ?> <!DOCTYPE struts PUBLIC "-//Apache Software Foundation//DTD Struts Configuration 2.0//EN" "http://struts.apache.org/dtds/struts-2.0.dtd"> <struts> <package name="default" extends="struts-default" namespace=""> <!-- global --> <global-results> <result name="error">/error.jsp</result> </global-results> <global-exception-mappings> <exception-mapping result="error" exception="java.lang.Exception" /> </global-exception-mappings> <!-- demo.hello.HelloAction --> <action name="listHello" class="demo.hello.HelloAction" method="listHello"> <result>/demo/hello/listHello.jsp</result> </action> <action name="viewHello" class="demo.hello.HelloAction" method="viewHello"> <result>/demo/hello/viewHello.jsp</result> </action> <action name="addHello" class="demo.hello.HelloAction" method="addHello"> <result>/demo/hello/editHello.jsp</result> </action> <action name="editHello" class="demo.hello.HelloAction" method="editHello"> <result>/demo/hello/editHello.jsp</result> </action> <action name="saveHello" class="demo.hello.HelloAction" method="saveHello"> <result type="chain">listHello</result> </action> <action name="deleteHello" class="demo.hello.HelloAction" method="deleteHello"> <result type="redirect">/listHello.action</result> </action> <!-- demo.member.MemberAction --> <action name="listMember" class="demo.member.MemberAction" method="listMember"> <result>/demo/member/listMember.jsp</result> </action> <action name="viewMember" class="demo.member.MemberAction" method="viewMember"> <result>/demo/member/viewMember.jsp</result> </action> <action name="addMember" class="demo.member.MemberAction" method="addMember"> <result>/demo/member/editMember.jsp</result> </action> <action name="editMember" class="demo.member.MemberAction" method="editMember"> <result>/demo/member/editMember.jsp</result> </action> <action name="saveMember" class="demo.member.MemberAction" method="saveMember"> <result type="chain">listMember</result> </action> <action name="deleteMember" class="demo.member.MemberAction" method="deleteMember"> <result type="redirect">/listMember.action</result> </action> </package> </struts>

**▣ /webroot/WEB-INF/config/spring.properties**

Spring 프로퍼티

############################################# # JDBC (Oracle) # driver=oracle.jdbc.driver.OracleDriver # url=jdbc:oracle:thin:@10.10.10.10:1521:test # username=root # password=1234 ############################################# # JDBC (MySql) driver=com.mysql.jdbc.Driver url=jdbc:mysql://localhost:3306/test username=root password=1234

**▣ /webroot/WEB-INF/config/applicationContext.xml**

String 설정파일

<?xml version="1.0" encoding="UTF-8"?> <beans default-autowire="no" default-lazy-init="false" default-dependency-check="none" xmlns="http://www.springframework.org/schema/beans" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:aop="http://www.springframework.org/schema/aop" xmlns:tx="http://www.springframework.org/schema/tx" xmlns:jee="http://www.springframework.org/schema/jee" xsi:schemaLocation=" http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-2.0.xsd http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx-2.0.xsd http://www.springframework.org/schema/aop http://www.springframework.org/schema/aop/spring-aop-2.0.xsd http://www.springframework.org/schema/jee http://www.springframework.org/schema/jee/spring-jee-2.0.xsd"> <bean id="propertyConfigurer" class="org.springframework.beans.factory.config.PropertyPlaceholderConfigurer"> <property name="locations"> <list> <value>classpath:/spring.properties</value> </list> </property> <property name="fileEncoding"> <value>UTF-8</value> </property> </bean> <bean id="dataSource" class="org.apache.commons.dbcp.BasicDataSource"> <property name="driverClassName"> <value>${driver}</value> </property> <property name="url"> <value>${url}</value> </property> <property name="username"> <value>${username}</value> </property> <property name="password"> <value>${password}</value> </property> </bean> <bean id="sqlMapClient" class="org.springframework.orm.ibatis.SqlMapClientFactoryBean"> <property name="configLocation"> <value>/WEB-INF/config/SqlMapConfig.xml</value> </property> <property name="dataSource"> <ref bean="dataSource" /> </property> </bean> <!-- hello --> <bean id="helloService" class="demo.hello.HelloServiceImpl"> <property name="helloDao" ref="helloDao" /> </bean> <bean id="helloDao" class="demo.hello.HelloDaoImpl"> <property name="sqlMapClient" ref="sqlMapClient" /> </bean> <!-- member --> <bean id="memberService" class="demo.member.MemberServiceImpl"> <property name="memberDao" ref="memberDao" /> </bean> <bean id="memberDao" class="demo.member.MemberDaoImpl"> <property name="sqlMapClient" ref="sqlMapClient" /> </bean> </beans>

**▣ Member.sql**

Member 테이블 생성

CREATE TABLE `member` ( `id` varchar(12) NOT NULL, `name` varchar(20) default NULL, `city` varchar(20) default NULL, PRIMARY KEY (`id`) )

**▣ /webroot/WEB-INF/config/SqlMapConfig.xml**

<?xml version="1.0" encoding="UTF-8" ?> <!DOCTYPE sqlMapConfig PUBLIC "-//ibatis.apache.org//DTD SQL Map Config 2.0//EN" "http://ibatis.apache.org/dtd/sql-map-config-2.dtd"> <sqlMapConfig> <settings cacheModelsEnabled="true" /> <sqlMap resource="demo/member/MemberSqlMap.xml" /> </sqlMapConfig>

**▣ /webroot/WEB-INF/src/demo/member/MemberSqlMap.xml**

<?xml version="1.0" encoding="UTF-8" ?> <!DOCTYPE sqlMap PUBLIC "-//iBATIS.com//DTD SQL Map 2.0//EN" "http://www.ibatis.com/dtd/sql-map-2.dtd"> <sqlMap namespace="member"> <typeAlias alias="member" type="demo.member.Member" /> <resultMap id="member-resultMap" class="member"> <result property="id" column="id" /> <result property="name" column="name" /> <result property="city" column="city" /> </resultMap> <statement id="getMemberList" resultMap="member-resultMap">SELECT id, name, city FROM MEMBER</statement> <statement id="getMember" parameterClass="string" resultMap="member-resultMap"> SELECT id, name, city FROM MEMBER WHERE id = #id# </statement> <statement id="insertMember" parameterClass="member"> INSERT INTO MEMBER( id, name, city ) VALUES(#id#, #name#, #city#) </statement> <statement id="updateMember" parameterClass="member"> UPDATE MEMBER SET name = #name#, city =#city# WHERE id = #id# </statement> <statement id="deleteMember" parameterClass="string">DELETE FROM MEMBER WHERE id = #id#</statement> </sqlMap>

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#Struts #Spring #웹개발 #레거시시스템 #Java #프레임워크 #웹애플리케이션 #XML설정 #JDBC #MySQL #Oracle #데이터베이스 #개발자 #Java개발 #서버사이드프로그래밍 #iBATIS #SQL #프로젝트관리 #코드샘플 #API설정 #소프트웨어개발 #개발팁 #프로그램구조 #배포환경 #웹서버 #프레임워크설정 #커뮤니티 #오픈소스 #데이터관리 #프로그래밍공부

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

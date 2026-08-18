---
title: "2023-10-07 223230267016 SpringBoot - Spring Initializer로 프로젝트를 생성"
type: blog-archive
status: active
created: 2023-10-07
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223230267016&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223230267016
published: "2023. 10. 7. 2:30"
body_hash: 951f3f96c7110e6848aa93cfda7371914ce964b1838d3529eb95ba712a020397
visibility: private
rag: exclude
---
# 2023-10-07 223230267016 SpringBoot - Spring Initializer로 프로젝트를 생성

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223230267016&categoryNo=982
- 게시일: 2023. 10. 7. 2:30

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTZfNjcg/MDAxNzQ0ODA0MTg4MzUz.LW4oJ7E-8YooitRMK58TKApQfO2PW9vm8qOaKCUEtXog.PuMAXaqiUDWFXzHZO3wxuEtLTB41w5lJouXW4fPeY5sg.PNG/Spring-001_\(12\).png?type=w80_blur)

​

**1\. 개요**

Spring Initializer 사이트에서 Spring Boot 프로젝트 템플릿을 쉽게 만들 수 있다. Spring Boot 버전과 Maven/Gradle을 선택할 수 있고 프로젝트 메타데이터(Project Metadata)를 입력하고 패키징 타입과 자바 버전을 선택하면 된다. 마지막으로 "ADD DEPENDENCIES..." 버튼을 클릭해 의존성 라이브러리를 추가한다. 입력과 선택을 마치고 나서 "GENERATE" 버튼을 클릭하면 zip 파일이 다운로드된다.

​

<https://start.spring.io/>

![](https://postfiles.pstatic.net/MjAyMzEwMDdfMTk0/MDAxNjk2NjA5MzgxOTM5.oIbwMpXJKlTu7ruhK3_5GTjQSVXYOtKmHw9TPs2GW3Eg.6SBGd1FvGTBgUKvPz1PRkX24otOpCbDYbasYogsqrsAg.PNG.agapeuni/img.png?type=w80_blur)

​

​

**2\. 준비**

Spring Initializer 사이트에서 다음과 같이 입력을 하였다.

Dependencies는 Lombook, Thymeleaf, Spring Data JPA, Spring Web, MySQL Driver를 선택했다.

![](https://postfiles.pstatic.net/MjAyMzEwMDdfMTI5/MDAxNjk2NjA5Mzg2OTIy.7eytJMJGqq68ed4Xsm65mzzS026pxMQYDxCt22ebuFkg.nYyJbAbW7h1LGDhsm4bhRtagnd1Fmc28il2b4JkNvn8g.PNG.agapeuni/img.png?type=w80_blur)

​

"GENERATE" 버튼을 클릭하면 demo.zip 파일이 다운로드 된다. 해당 파일을 이클립스 workspace에 압축 해제하고서 Maven Project를 import 한다. 프로젝트명은 SpringDemo로 변경했다.

![](https://postfiles.pstatic.net/MjAyMzEwMDdfODcg/MDAxNjk2NjA5MzkzMTI0.ovCXbRVrlEuzxNw2-cj0KHB9zHFOVZlj2rM2-J2zH34g.ZMFpVI4rn-PgzxMmj21X0DNjWJsGej2WUKcsBnDK0d8g.PNG.agapeuni/img.png?type=w80_blur)

​

Spring Boot 프로젝트 템플릿이 잘 적용되었다.

![](https://postfiles.pstatic.net/MjAyMzEwMDdfODIg/MDAxNjk2NjA5NDAwODgz.j_6nnQu-ieRZdHe5oUu5OKXJYvT_4-REu8AYVi08OxEg.i23fGu7UbqWc7fFnLwQIy152ixNjTBnqEAuhcDANXd8g.PNG.agapeuni/img.png?type=w80_blur)

​

application.properties를 다음과 같이 작성한다. 애플리케이션 포트는 다른 서비스와 충돌 나지 않게 8070으로 하고 데이터베이스는 MySQL을 연결한다. 실행되는 쿼리를 화면에 출력하기 위한 설정과 출력되는 쿼리를 읽기 좋은 포맷으로 설정한다.

server.port = 8070 spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver spring.datasource.url=jdbc:mysql://localhost:3306/demo?serverTimezone=UTC spring.datasource.username=root spring.datasource.password=1234 spring.jpa.properties.hibernate.show_sql=true spring.jpa.properties.hibernate.format_sql=true logging.level.org.hibernate.type.descriptor.sql=trace spring.jpa.hibernate.ddl-auto=create spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect

이제 필요한 로직을 추가해 나가면 된다.

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#SpringBoot #SpringInitializer #Maven #Gradle #Java #Thymeleaf #Lombok #SpringDataJPA #MySQL #애플리케이션설정 #applicationproperties #Hibernate #RESTAPI #프로그래밍 #백엔드개발 #데이터베이스 #쿼리출력 #개발환경설정 #IT기술 #소프트웨어개발 #프로그래밍블로그 #이클립스 #MavenProject #SpringWeb #개발자 #코드샘플 #SpringBoot프로젝트 #Java개발 #개발툴 #SpringFramework

![](https://postfiles.pstatic.net/MjAyMzEwMDdfMjIg/MDAxNjk2NjA5MjYwMTQ1.K3AfYcAg7OPXsTzlqfTHXPx7_XqCJXNESWLHJqfdQQkg.xYAtbScLwoMzc7AwdOoeQGoGSatTI0SQYBFmnVF01pgg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

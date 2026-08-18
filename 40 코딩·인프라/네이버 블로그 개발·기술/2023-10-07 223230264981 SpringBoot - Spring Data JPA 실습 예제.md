---
title: "2023-10-07 223230264981 SpringBoot - Spring Data JPA 실습 예제"
type: blog-archive
status: active
created: 2023-10-07
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223230264981&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223230264981
published: "2023. 10. 7. 1:50"
body_hash: 536939d772c2dbd3a93acb787702188a84abbc0dac301fbc3f24ca67b9050d13
visibility: private
rag: exclude
---
# 2023-10-07 223230264981 SpringBoot - Spring Data JPA 실습 예제

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223230264981&categoryNo=982
- 게시일: 2023. 10. 7. 1:50

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTZfMjAx/MDAxNzQ0ODA0MTEzNDc5.VeNU55g6cSOV_xHTBybzYi-TCwL-VK3nC3qixJXWQh0g.WSgMOmOC1LxHNRbNP_FJXVWtP-S5epCfAvjexpJrLGcg.PNG/Spring-001_\(11\).png?type=w80_blur)

​

Spring Data JPA는 관계형 데이터베이스를 사용하기 위해 Java에서 바로 접근하는 기술이다. Java에서 JPA로 구현해 두면 데이터베이스의 교체를 쉽게 할 수 있다. 여기서는 간단한 예제를 통하여 살펴보기로 한다.

buildscript { ext { springBootVersion = '2.1.9.RELEASE' } repositories { mavenCentral() jcenter() } dependencies { classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}") } } apply plugin: 'java' apply plugin: 'eclipse' apply plugin: 'org.springframework.boot' apply plugin: 'io.spring.dependency-management' group 'org.oneway' version '1.0-SNAPSHOT' sourceCompatibility = 1.8 repositories { mavenCentral() jcenter() } dependencies { compile('org.springframework.boot:spring-boot-starter-web') compile('org.springframework.boot:spring-boot-starter-data-jpa') compile('com.h2database:h2') testCompile('org.springframework.boot:spring-boot-starter-test') }

​

Spring Data JPA 구성을 하고 라이브러리가 추가되고 나서 다음과 같이 Board 클래스를 생성한다.

@Entity는 엔티티 클래스를 나타내는 JPA의 어노테이션이다. @Id를 PK를 나타내며 @Column은 테이블의 칼럼을 나타낸다.

​

*** Board.java**

package com.oneway.board.entity; import javax.persistence.*; @Entity public class Board { @Id @GeneratedValue(strategy = GenerationType.IDENTITY) private Long id; @Column(length = 200, nullable = false) private String title; @Column(columnDefinition = "TEXT", nullable = false) private String content; private String writer; public Board() { } public Board(String title, String content, String writer) { this.title = title; this.content = content; this.writer = writer; } public Long getId() { return id; } public void setId(Long id) { this.id = id; } public String getTitle() { return title; } public void setTitle(String title) { this.title = title; } public String getContent() { return content; } public void setContent(String content) { this.content = content; } public String getWriter() { return writer; } public void setWriter(String writer) { this.writer = writer; } }

​

Board 엔티티 클래스 작성을 하고 나서 데이터베이스에 접근하기 위한 JpaRepository를 생성한다.

JpaRepository<엔티티 클래스, PK>를 상속하면 기본적인 CRUD 기능이 자동으로 제공된다.

​

*** BoardRepository**

package com.oneway.board.entity; import org.springframework.data.jpa.repository.JpaRepository; import org.springframework.data.jpa.repository.Query; import java.util.List; public interface BoardRepository extends JpaRepository<Board, Long> { @Query("SELECT b FROM Board b ORDER BY b.id DESC") List<Board> findAllDesc(); }

![](https://postfiles.pstatic.net/MjAyMzEwMDdfMTMg/MDAxNjk2NjA5MDQxMzY4.f4ulLEYTuK988cAsXHpa97702GphZI1p-1JNv7GPBEcg.IyRR9dD01s361ZuukcP6kiNFOOfygVHfm7uIoAmKDZQg.PNG.agapeuni/img.png?type=w80_blur)

​

​

Spring Data JPA를 테스트하기 위한 코드를 작성한다. 게시글을 하나 만들어 저장하고서 조회하여 온 값과 같은지 비교하는 코드이다.

​

*** BoardRepositoryTest 클래스**

package com.oneway.board; import com.oneway.board.entity.Board; import com.oneway.board.entity.BoardRepository; import org.junit.After; import org.junit.Test; import org.junit.runner.RunWith; import org.springframework.beans.factory.annotation.Autowired; import org.springframework.boot.test.context.SpringBootTest; import org.springframework.test.context.junit4.SpringRunner; import java.util.List; import static org.assertj.core.api.Assertions.assertThat; @RunWith(SpringRunner.class) @SpringBootTest public class BoardRepositoryTest { @Autowired BoardRepository boardRepository; @Test public void testBoardSave() { String title = "title"; String content = "content"; String writer = "writer"; Board board = new Board(); board.setTitle(title); board.setContent(content); board.setWriter(writer); boardRepository.save(board); List<Board> boardList = boardRepository.findAll(); board = boardList.get(0); assertThat(board.getTitle()).isEqualTo(title); assertThat(board.getContent()).isEqualTo(content); assertThat(board.getWriter()).isEqualTo(writer); } @After public void cleanup() { boardRepository.deleteAll(); } }

![](https://postfiles.pstatic.net/MjAyMzEwMDdfMjY1/MDAxNjk2NjA5MDcyMjI5.8hwlfepyPcmuD3htq8RMlCvpllh_0_bz8CN36qQrEEIg.650fDgKXASn34A9J-Vmw75RppU_3sUxnWsrPPhm8GLsg.PNG.agapeuni/img.png?type=w80_blur)

​

​

BoardRepository 클래스에서 구현한 적이 없는 메서드를 사용하였는데 해당 메서드들은 JpaRepository 인터페이스에 정의되어 있다.

​

\- boardRepository.save(board);

\- boardRepository.findAll();

\- boardRepository.deleteAll();

​

​

*** JpaRepository 인터페이스**

package org.springframework.data.jpa.repository; import java.util.List; import javax.persistence.EntityManager; import org.springframework.data.domain.Example; import org.springframework.data.domain.Sort; import org.springframework.data.repository.NoRepositoryBean; import org.springframework.data.repository.PagingAndSortingRepository; import org.springframework.data.repository.query.QueryByExampleExecutor; @NoRepositoryBean public interface JpaRepository<T, ID> extends PagingAndSortingRepository<T, ID>, QueryByExampleExecutor<T> { List<T> findAll(); List<T> findAll(Sort sort); List<T> findAllById(Iterable<ID> ids); <S extends T> List<S> saveAll(Iterable<S> entities); void flush(); <S extends T> S saveAndFlush(S entity); void deleteInBatch(Iterable<T> entities); void deleteAllInBatch(); T getOne(ID id); <S extends T> List<S> findAll(Example<S> example); <S extends T> List<S> findAll(Example<S> example, Sort sort); }

​

테스트 결과로그

Testing started at 오후 03:02 ... > Task :cleanTest > Task :compileJava UP-TO-DATE > Task :processResources UP-TO-DATE > Task :classes UP-TO-DATE > Task :compileTestJava UP-TO-DATE > Task :processTestResources NO-SOURCE > Task :testClasses UP-TO-DATE > Task :test 15:02:36.373 [Test worker] DEBUG org.springframework.test.context.junit4.SpringJUnit4ClassRunner - SpringJUnit4ClassRunner constructor called with [class com.oneway.board.BoardRepositoryTest] 15:02:36.388 [Test worker] DEBUG org.springframework.test.context.BootstrapUtils - Instantiating CacheAwareContextLoaderDelegate from class [org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate] 15:02:36.398 [Test worker] DEBUG org.springframework.test.context.BootstrapUtils - Instantiating BootstrapContext using constructor [public org.springframework.test.context.support.DefaultBootstrapContext(java.lang.Class,org.springframework.test.context.CacheAwareContextLoaderDelegate)] 15:02:36.421 [Test worker] DEBUG org.springframework.test.context.BootstrapUtils - Instantiating TestContextBootstrapper for test class [com.oneway.board.BoardRepositoryTest] from class [org.springframework.boot.test.context.SpringBootTestContextBootstrapper] 15:02:36.442 [Test worker] INFO org.springframework.boot.test.context.SpringBootTestContextBootstrapper - Neither @ContextConfiguration nor @ContextHierarchy found for test class [com.oneway.board.BoardRepositoryTest], using SpringBootContextLoader 15:02:36.447 [Test worker] DEBUG org.springframework.test.context.support.AbstractContextLoader - Did not detect default resource location for test class [com.oneway.board.BoardRepositoryTest]: class path resource [com/oneway/board/BoardRepositoryTest-context.xml] does not exist 15:02:36.449 [Test worker] DEBUG org.springframework.test.context.support.AbstractContextLoader - Did not detect default resource location for test class [com.oneway.board.BoardRepositoryTest]: class path resource [com/oneway/board/BoardRepositoryTestContext.groovy] does not exist 15:02:36.449 [Test worker] INFO org.springframework.test.context.support.AbstractContextLoader - Could not detect default resource locations for test class [com.oneway.board.BoardRepositoryTest]: no resource found for suffixes {-context.xml, Context.groovy}. ...(중략)... schema as part of SessionFactory shut-down' Hibernate: drop table if exists board 2023-10-06 15:02:42.655 INFO 15024 --- [ Thread-4] com.zaxxer.hikari.HikariDataSource : HikariPool-1 - Shutdown initiated... 2023-10-06 15:02:42.671 INFO 15024 --- [ Thread-4] com.zaxxer.hikari.HikariDataSource : HikariPool-1 - Shutdown completed. BUILD SUCCESSFUL in 8s 5 actionable tasks: 2 executed, 3 up-to-date 오후 3:02:42: Tasks execution finished ':cleanTest :test --tests "com.oneway.board.BoardRepositoryTest"'.

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#SpringDataJPA #JPA #Java #스프링부트 #Gradle #관계형데이터베이스 #엔티티 #CRUD #JpaRepository #테스트코드 #Board클래스 #데이터베이스접근 #SpringBootApplication #스프링프레임워크 #H2Database #API개발 #Java개발 #소프트웨어개발 #백엔드개발 #IT기술 #프로그래밍 #개발자 #SpringBootTest #JUnit #MockMvc #코드리뷰 #데이터베이스 #엔티티설계 #프로그래밍블로그 #개발환경설정 #코드샘플

![](https://postfiles.pstatic.net/MjAyMzEwMDdfOTAg/MDAxNjk2NjA4OTA0NzM1.Mu975Z5c1GwAz06PUHsJxXsISKq6IzgJVmftFPBA-xsg.D23lUP9nepHq0OTz0q7RtMfTC-lpnfjzGcojWzZFvcAg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

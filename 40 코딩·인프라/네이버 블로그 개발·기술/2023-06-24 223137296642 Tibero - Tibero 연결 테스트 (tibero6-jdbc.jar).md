---
title: "2023-06-24 223137296642 Tibero - Tibero 연결 테스트 (tibero6-jdbc.jar)"
type: blog-archive
status: active
created: 2023-06-24
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223137296642&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223137296642
published: "2023. 6. 24. 1:43"
body_hash: 005a3e096be33339a06fff23a5c56b4e5ab0dc43f5ffc4504bb7cfb3be57d958
visibility: private
rag: exclude
---
# 2023-06-24 223137296642 Tibero - Tibero 연결 테스트 (tibero6-jdbc.jar)

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223137296642&categoryNo=982
- 게시일: 2023. 6. 24. 1:43

## 본문

![](https://postfiles.pstatic.net/MjAyNDA1MTJfMzMg/MDAxNzE1NDQ2NDcxMzQw.IWKMeR5HGEWtDj_NVTGKhEA6PvSj8_1YDAzC6mcYw4kg.tHIJc4gGMtnj4--Hz7dNTdVfybGob3dUEVgsFfZL1iAg.PNG/Database-001.png?type=w80_blur)

​

**1\. JDBC(Java Database Connectivity)**

JDBC는 Java로 개발된 프로그램 안에서 SQL 문장을 실행하기 위해 데이터베이스를 연결해 주는 API(Application Program Interface)이다. Tibero에서는 JDBC 표준을 준수하고 관련 API를 제공하고 있다. 이렇게 구성된 API를 **tbJDBC**(Tibero의 Java Database Connectivity)라 한다.

​

​

**2\. Tibero 데이터베이스**

![](https://postfiles.pstatic.net/MjAyMzA2MzBfMTM4/MDAxNjg4MDk0Mjg2NDA1.hcdwNSgs41qBySdknWsBshUDy6Kvm3n-gbcOsK8u_R0g.gqeewuGwC1_q0JyPIchYYT43oLrQjs06GchWEnuAOFEg.PNG.agapeuni/image.png?type=w80_blur)

Tibero 데이터베이스 연결 테스트용 자바를 구현해 본다. Tibero 데이터베이스 연결을 위해 tibero6-jdbc.jar 라이브러리(JDK 6이상)를 사용하였다. 아래의 코드에서 dbUrl, dbUser와 dbPassword는 자신의 환경에 맞추어 변경하면 된다.

**첨부파일**

tibero6-jdbc.jar

[ 파일 다운로드 ](https://download.blog.naver.com/open/ed78f14a506667d3f7197b4d7491e69e37679b2a/EFsQbrdMxrvO9dlQLuoSggWaFwbSq-VhdkQGNWY5_gMuEY27UXUk6Pa8A4UO52gsqxenbl3--mfeh8vhq52AQnQY0U4vTHc/tibero6-jdbc.jar)

​

**▣ 소스 코드**

import java.sql.Connection; import java.sql.DriverManager; import java.sql.ResultSet; import java.sql.SQLException; import java.sql.Statement; public class TestTibero { public static void main(String[] args) { String dbUrl = "jdbc:tibero:thin:@ip:port:SID"; String dbUser = "tibero"; String dbPassword = "max"; Connection conn = null; Statement stmt = null; ResultSet rs = null; try { Class.forName("com.tmax.tibero.jdbc.TbDriver"); System.out.println("DriverLoading OK. *^^*"); } catch (ClassNotFoundException e) { System.out.println("DriverLoading Error. ^^;"); e.printStackTrace(); return; } try { conn = DriverManager.getConnection(dbUrl, dbUser, dbPassword); System.out.println("DriverConnection OK. *^^*"); } catch (SQLException e) { System.out.println("DriverConnection Error. ^^;"); e.printStackTrace(); return; } try { stmt = conn.createStatement(); rs = stmt.executeQuery("SELECT 1 AS A, 2 AS B FROM DUAL"); while (rs.next()) { System.out.println(rs.getString(1) + " - " + rs.getString(2)); } } catch (SQLException e) { System.out.println("executeQuery()Error. ^^;"); e.printStackTrace(); } release(conn, stmt, rs); } private static void release(Connection conn, Statement stmt, ResultSet rs) { try { if (rs != null) { rs.close(); } if (stmt != null) { stmt.close(); } if (conn != null) { conn.close(); } } catch (SQLException e) { e.printStackTrace(); } } }

**▣ 실행결과**

Driver Loading OK. *^^* Driver Connection OK. *^^* 1 - 2

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#JDBC #Java #Tibero #TiberoJDBC #DatabaseConnectivity #JavaDatabase #SQL #JDBCAPI #TiberoDB #데이터베이스연결 #JavaSQL #tbJDBC #데이터베이스테스트 #JDBC드라이버 #JDBC연결 #TiberoJDBCDriver #Tibero연결 #Java코딩 #데이터베이스구현 #SQL쿼리 #JDBC연동 #드라이버설치 #JDBC연결오류 #TiberoDatabase #SQL조회 #DB연결테스트 #JDBC라이브러리 #TiberoJDBCTesting #TiberoJDBC설정 #Tibero6JDBC #SQL실행 #자바SQL

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

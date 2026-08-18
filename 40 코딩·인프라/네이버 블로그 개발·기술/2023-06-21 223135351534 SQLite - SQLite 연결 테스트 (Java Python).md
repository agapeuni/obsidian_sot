---
title: "2023-06-21 223135351534 SQLite - SQLite 연결 테스트 (Java Python)"
type: blog-archive
status: active
created: 2023-06-21
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223135351534&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223135351534
published: "2023. 6. 21. 23:48"
body_hash: 3fc20f7b65dbb66eecb1d8cef1f26baa629fdff831af04b56c0874c5ec1fdaa1
visibility: private
rag: exclude
---
# 2023-06-21 223135351534 SQLite - SQLite 연결 테스트 (Java Python)

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223135351534&categoryNo=982
- 게시일: 2023. 6. 21. 23:48

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTJfMTAw/MDAxNzQ0NDY4MDAzOTQy.6o7uo_mUWQEiayKo-1IndwphsjH67S0xJP6hbBgHidMg.hrAYPiapEGWnb4ocYJzOyEHEJxuxrp0-HOzsUO_7rPMg.PNG/Database-001_\(1\).png?type=w80_blur)

​

**1\. SQLite 개요**

SQLite는 별도의 서버 프로세스가 없는 단일 파일의 데이터베이스이다. 대규모 작업에는 적합하지 않지만 가볍고 다루기 쉽다. Java와 Python으로 SQLite 데이터베이스를 연결하는 코드를 작성해 본다.

![](https://postfiles.pstatic.net/MjAyMzA2MjFfMjAx/MDAxNjg3MzU4NTkxOTE0.TIk8aYI8lxf0A6G86SIjnfXYXX3cDaNJf6099YnMpL4g.BJZzkZlTinZGxObeUEclaFCO_x8pzMnCRGAU3nzhGm0g.PNG.agapeuni/img.png?type=w80_blur)

**[이미지 출처]**[**https://devopedia.org/sqlite**](https://devopedia.org/sqlite)

**​**

**2\. SQLite JDBC**

sqlite-jdbc 다운로드

SQLite JDBC는 Java에서 SQLite 데이터베이스 파일에 액세스 하고 생성하기 위한 라이브러리이다. 

Java에서 실행하기 위해서는 해당 라이브러리가 필요하다. 아래의 경로에서 다운로드 할 수 있다.

<https://repo1.maven.org/maven2/org/xerial/sqlite-jdbc/3.40.0.0/>

[ **Central Repository: org/xerial/sqlite-jdbc/3.40.0.0** org/xerial/sqlite-jdbc/3.40.0.0 ../ sqlite-jdbc-3.40.0.0-javadoc.jar 2022-11-22 02:46 1017823 sqlite-jdbc-3.40.0.0-javadoc.jar.asc 2022-11-22 02:46 228 sqlite-jdbc-3.40.0.0-javadoc.jar.md5 2022-11-22 02:46 32 sqlite-jdbc-3.40.0.0-javadoc.jar.sha1 2022-11-22 02:46 40 sqlite-jdbc... repo1.maven.org ](https://repo1.maven.org/maven2/org/xerial/sqlite-jdbc/3.40.0.0/)

​

**3\. 연결 테스트 with Java**

import java.sql.Connection; import java.sql.DriverManager; import java.sql.PreparedStatement; import java.sql.ResultSet; import java.sql.SQLException; import java.sql.Statement; public class TestSqlLite { public static void main(String[] args) throws Exception { Connection conn = null; Statement stmt = null; String dbUrl = "jdbc:sqlite:/D:/db/sqlite.db"; try { Class.forName("org.sqlite.JDBC"); } catch (ClassNotFoundException e) { System.out.println(e.toString()); return; } try { conn = DriverManager.getConnection(dbUrl); } catch (SQLException e) { System.out.println(e.toString()); return; } try { stmt = conn.createStatement(); stmt.executeUpdate("drop table if exists people;"); stmt.executeUpdate("create table people (name, job);"); } catch (SQLException e) { System.out.println(e.toString()); } try { stmt = conn.createStatement(); String sql = "insert into people (name, job) values ('Park ChunSam', 'Public servant');"; stmt.executeUpdate(sql); } catch (SQLException e) { System.out.println(e.toString()); } try { PreparedStatement prep = conn.prepareStatement("insert into people values (?, ?);"); prep.setString(1, "Moon DolSik"); prep.setString(2, "Pilot"); prep.addBatch(); prep.setString(1, "Ko GilDong"); prep.setString(2, "Youtuber"); prep.addBatch(); prep.setString(1, "OneWay"); prep.setString(2, "Programmer"); prep.addBatch(); prep.setString(1, "TwoWay"); prep.setString(2, "Programmer"); prep.addBatch(); conn.setAutoCommit(false); prep.executeBatch(); conn.setAutoCommit(true); } catch (SQLException e) { System.out.println(e.toString()); } try { ResultSet rs = stmt.executeQuery("select * from people;"); while (rs.next()) { System.out.println(rs.getString("name") + " - " + rs.getString("job")); } rs.close(); System.out.println(); stmt = conn.createStatement(); stmt.executeUpdate("delete from people where name='TwoWay';"); rs = stmt.executeQuery("select * from people;"); while (rs.next()) { System.out.println(rs.getString("name") + " - " + rs.getString("job")); } rs.close(); } catch (SQLException e) { System.out.println(e.toString()); } try { if (stmt != null) { stmt.close(); } if (conn != null) { conn.close(); } } catch (SQLException e) { System.out.println(e.toString()); } } }

실행결과

Park ChunSam - Public servant Moon DolSik - Pilot Ko GilDong - Youtuber OneWay - Programmer TwoWay - Programmer Park ChunSam - Public servant Moon DolSik - Pilot Ko GilDong - Youtuber OneWay - Programmer

​

**4\. 연결 테스트 with Python**

import sqlite3 conn = sqlite3.connect("sqlite.db") cursor = conn.cursor() cursor.executescript( """ DROP TABLE IF EXISTS people; CREATE TABLE people ( id integer primary key autoincrement, name text, job text ); DELETE FROM people; """ ) conn.commit() # Parameterized 방식으로 데이터 추가 sql = "INSERT INTO people (name, job) VALUES (?, ?)" people = ('Park ChunSam', 'Public servant') cursor.execute(sql, people) # 데이터 조회 sql = "SELECT * FROM people" cursor.execute(sql) print(cursor.fetchone()) print() # Named Placeholder 방식으로 데이터 추가 sql = "INSERT INTO people (name, job) VALUES (:name, :job)" people = {"name": "Moon DolSik", "job": "Pilot"} cursor.execute(sql, people) # 데이터 추가 sql = "INSERT INTO people (name, job) VALUES (?, ?)" peoples = [ ("Ko GilDong", "Youtuber"), ("OneWay", "Programmer"), ("TwoWay", "Programmer"), ] cursor.executemany(sql, peoples) # 데이터 조회 cursor.execute("SELECT * FROM people") rows = cursor.fetchall() for row in rows: print(row) print() # 데이터 삭제 sql = "DELETE FROM people WHERE name = ?" cursor.execute(sql, ("TwoWay",)) print("delete count = ", cursor.rowcount) print() # 데이터 조회 cursor.execute("SELECT * FROM people") for row in cursor: print(row) print() conn.commit() conn.close()

실행결과

(1, 'Park ChunSam', 'Public servant') (1, 'Park ChunSam', 'Public servant') (2, 'Moon DolSik', 'Pilot') (3, 'Ko GilDong', 'Youtuber') (4, 'OneWay', 'Programmer') (5, 'TwoWay', 'Programmer') delete count = 1 (1, 'Park ChunSam', 'Public servant') (2, 'Moon DolSik', 'Pilot') (3, 'Ko GilDong', 'Youtuber') (4, 'OneWay', 'Programmer')

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#SQLite #SQLiteJDBC #JavaSQLite #PythonSQLite #SQLite연결 #데이터베이스 #JDBC라이브러리 #Java프로그래밍 #Python프로그래밍 #SQLite테스트 #데이터베이스연동 #프로그래밍튜토리얼 #SQLite설치 #데이터베이스쿼리 #SQL실습 #JavaSQL #PythonSQL #SQLite예제 #코딩연습 #데이터베이스관리 #DB연동 #SQLite사용법 #프로그래밍기초 #SQL #코드예제 #프론트엔드백엔드 #데이터베이스설계 #SQL쿼리 #SQL자동화 #개발자팁 #SQLite활용 #프로그래밍

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

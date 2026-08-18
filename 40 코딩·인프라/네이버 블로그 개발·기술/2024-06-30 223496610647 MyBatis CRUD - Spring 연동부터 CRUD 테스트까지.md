---
title: "2024-06-30 223496610647 MyBatis CRUD - Spring 연동부터 CRUD 테스트까지"
type: blog-archive
status: active
created: 2024-06-30
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223496610647&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223496610647
published: "2024. 6. 30. 22:04"
body_hash: 182c390b4c2ca501857ef6338099a10690c64c2a8d98ef40dc2f30bf6b3113e3
visibility: private
rag: exclude
---
# 2024-06-30 223496610647 MyBatis CRUD - Spring 연동부터 CRUD 테스트까지

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223496610647&categoryNo=982
- 게시일: 2024. 6. 30. 22:04

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTZfMjMz/MDAxNzQ0NzgyNTYxNjMz.ddLPs1V30spq8zem5g2xXNf8umLZplVdo9A3V0HuZj0g.iwxpVyXJUJt9GL7ykUfIW5Rute0xSoNOaBl20J5Gcsgg.PNG/MyBatis-001_\(1\).png?type=w80_blur)

​

MyBatis는 iBATIS의 새로운 버전으로 국내에서 가장 많이 사용되는 ORM Framework 중 하나이다. MyBatis는 문서화가 잘 되어 있다고 하지만 막상 실전에 적용시키기에는 이전 버전인 iBATIS에 비해 예제가 부족하다. 그래서 자료도 정리할 겸 간단한 에제를 작성하며 레퍼런스를 만들어 볼까 한다. 우선 MyBatis를 설정하고 간단한 예제를 만들어 본 다음, Spring 3로 Bean을 등록하는 예제로 확장시켜 볼 예정이다.

​

​

**MySQL Table**

CREATE TABLE user ( id INT(5) NOT NULL PRIMARY KEY AUTO_INCREMENT, username VARCHAR(16) NOT NULL, password VARCHAR(16) NOT NULL, level INT(2) NOT NULL DEFAULT '0', reg_date DATE NOT NULL );

​

​

**Configuration**

development.properties

url=jdbc:mysql://localhost/development?characterEncoding=utf-8 driver=com.mysql.jdbc.Driver user=development pass=test123

​

mysql-config.xml

<?xml version="1.0" encoding="UTF-8"?> <!DOCTYPE configuration PUBLIC "-//mybatis.org//DTD Config 3.0//EN" "http://mybatis.org/dtd/mybatis-3-config.dtd"> <configuration> <properties resource="exercise/mybatis3/persistence/development.properties"/> <settings> <setting name="defaultExecutorType" value="REUSE"/> <setting name="useGeneratedKeys" value="true"/> </settings> <typeAliases> <!-- Type Aliases List --> </typeAliases> <environments default="development"> <environment id="development"> <transactionManager type="JDBC"/> <dataSource type="JNDI"> <property name="initial_context" value="java:comp/env" /> <property name="data_source" value="jdbc/insure"/> </dataSource> </environment> <environment id="testing"> <transactionManager type="MANAGED"> <property name="closeConnection" value="false"/> </transactionManager> <dataSource type="POOLED"> <property name="driver" value="${driver}" /> <property name="url" value="${url}" /> <property name="username" value="${user}" /> <property name="password" value="${pass}" /> </dataSource> </environment> </environments> <mappers> <!-- Mapper List --> </mappers> </configuration>

​

**SQL Mapper**

UserMapper.xml

<?xml version="1.0" encoding="UTF-8"?> <!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd"> <mapper namespace="exercise.mybatis3.persistence.UserMapper"> <insert id="add" parameterType="User" useGeneratedKeys="true" keyProperty="id"> INSERT INTO user (username, password, level, reg_date) VALUES (#{username}, #{password}, 1, NOW()) </insert> <select id="count" resultType="int"> SELECT COUNT(*) FROM user </select> </mapper>

​

UserMapper.java

package exercise.mybatis3.persistence; import exercise.mybatis3.domain.User; public interface UserMapper { public void add(User user); public int count(); }

​

**Domain Object**

User.java

package exercise.mybatis3.domain; import java.io.Serializable; public class User implements Serializable { private static final long serialVersionUID = 1L; private Integer id; private String username; private String password; private Integer level; private String regDate; public User() { // TODO Auto-generated constructor stub } public User(String username, String password) { this.username = username; this.password = password; } public Integer getId() { return id; } public void setId(Integer id) { this.id = id; } public String getUsername() { return username; } public void setUsername(String username) { this.username = username; } public String getPassword() { return password; } public void setPassword(String password) { this.password = password; } public Integer getLevel() { return level; } public void setLevel(Integer level) { this.level = level; } public String getRegDate() { return regDate; } public void setRegDate(String regDate) { this.regDate = regDate; } }

​

**Unit Test**

TestUserMapper.java

package exercise.mybatis3.test; import static org.junit.Assert.assertThat; import static org.hamcrest.CoreMatchers.is; import java.io.Reader; import org.apache.ibatis.io.Resources; import org.apache.ibatis.session.SqlSession; import org.apache.ibatis.session.SqlSessionFactory; import org.apache.ibatis.session.SqlSessionFactoryBuilder; import org.junit.Before; import org.junit.BeforeClass; import org.junit.Test; import exercise.mybatis3.domain.User; import exercise.mybatis3.persistence.UserMapper; public class TestUserMapper { static SqlSessionFactory sf; User user; @BeforeClass public static void setUpBeforeClass() throws Exception { String resource = "exercise/mybatis3/persistence/mybatis-config.xml"; Reader reader = Resources.getResourceAsReader(resource); sf = new SqlSessionFactoryBuilder().build(reader, "testing"); } @Before public void setUp() { user = new User("user1", "1234"); } @Test public void testAdd() { SqlSession session = sf.openSession(); try { UserMapper mapper = session.getMapper(UserMapper.class); mapper.add(user); assertThat(1, is(mapper.count())); } finally { session.close(); } } }

​

**SQL Mapper (CRUD)**

UserMapper.xml

<mapper namespace="exercise.mybatis3.persistence.UserMapper"> <insert id="add" parameterType="User" useGeneratedKeys="true" keyProperty="id"> INSERT INTO user (username, password, level, reg_date) VALUES (#{username}, #{password}, #{level}, #{regDate}) </insert> <select id="get" parameterType="int" resultType="User"> SELECT id, username, password, level, reg_date AS 'regDate' FROM user WHERE id = #{id} </select> <select id="getAll" resultType="User"> SELECT id, username, password, level, reg_date AS 'regDate' FROM user </select> <delete id="delete" parameterType="int"> DELETE FROM user WHERE id = #{id} </delete> <delete id="deleteAll"> DELETE FROM user </delete> <select id="count" resultType="int"> SELECT COUNT(*) FROM user </select> <select id="lastId" resultType="int"> SELECT id FROM user ORDER BY id DESC LIMIT 1 </select> </mapper>

​

**Mapper Interface Class (CRUD)**

UserMapper.java

public interface UserMapper { public void add(User user); public User get(int id); public List<user> getAll(); public void delete(int id); public void deleteAll(); public int count(); public int lastId(); }

**Domain Object**

User.java

public class User implements Serializable { private static final long serialVersionUID = 1L; private Integer id; private String username; private String password; private Integer level; private String regDate; public User() { // TODO Auto-generated constructor stub } public User(String username, String password, Integer level, String regDate) { this.username = username; this.password = password; this.level = level; this.regDate = regDate; } public Integer getId() { return id; } public void setId(Integer id) { this.id = id; } public String getUsername() { return username; } public void setUsername(String username) { this.username = username; } public String getPassword() { return password; } public void setPassword(String password) { this.password = password; } public Integer getLevel() { return level; } public void setLevel(Integer level) { this.level = level; } public String getRegDate() { return regDate; } public void setRegDate(String regDate) { this.regDate = regDate; } @Override public boolean equals(Object comp) { User target = (User) comp; if (this.id.equals(target.id) && this.username.equals(target.username) && this.password.equals(target.password) && this.level.equals(target.level) && this.regDate.equals(target.regDate)) return true; else return false; } }

​

**Unit test (CRUD)**

TestUserMapper.java

public class TestUserMapper { static SqlSessionFactory sf; List<user> users; @BeforeClass public static void setUpBeforeClass() throws Exception { String resource = "exercise/mybatis3/persistence/mybatis-config.xml"; Reader reader = Resources.getResourceAsReader(resource); sf = new SqlSessionFactoryBuilder().build(reader, "testing"); } @Before public void setUp() { users = Arrays.asList( new User("user1", "1234", 1, "2012-11-09"), new User("user2", "1234", 1, "2012-11-09"), new User("user3", "1234", 1, "2012-11-09") ); } @Test public void testAdd() { SqlSession session = sf.openSession(); try { UserMapper mapper = session.getMapper(UserMapper.class); mapper.deleteAll(); mapper.add(users.get(0)); assertThat(1, is(mapper.count())); } finally { session.close(); } } @Test public void testGet() { SqlSession session = sf.openSession(); try { UserMapper mapper = session.getMapper(UserMapper.class); mapper.deleteAll(); mapper.add(users.get(0)); User user = mapper.get(mapper.lastId()); assertTrue((users.get(0)).equals(user)); } finally { session.close(); } } @Test public void testGetAll() { SqlSession session = sf.openSession(); try { UserMapper mapper = session.getMapper(UserMapper.class); mapper.deleteAll(); for (User user : users) { mapper.add(user); } assertThat(users.size(), is(mapper.count())); } finally { session.close(); } } @Test public void testDelete() { SqlSession session = sf.openSession(); try { UserMapper mapper = session.getMapper(UserMapper.class); mapper.deleteAll(); for (User user : users) { mapper.add(user); } mapper.delete(mapper.lastId()); assertThat(users.size() - 1, is(mapper.count())); } finally { session.close(); } } } }

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#MyBatis #ORM #iBATIS #스프링프레임워크 #자바 #자바개발 #데이터베이스 #MySQL #SQL #자바매퍼 #사용자관리 #CRUD #단위테스트 #소프트웨어개발 #프로그래밍 #웹개발 #자바애플리케이션 #영속성계층 #데이터접근 #자바빈 #구성 #매퍼XML #개발속성 #자바직렬화 #소프트웨어공학 #애자일개발 #코딩예제 #DevOps #기술블로그 #백엔드개발 #자바커뮤니티

![](https://postfiles.pstatic.net/MjAyNDA2MzBfMTcy/MDAxNzE5NzUyMTcwNjQ1.fxhivRGHKFSMDkr95vEhG_3hYhz4PjsQpiIZOAa4wDgg.WgxX1SPGLPN_GA4dTdwXkVgT4-_RZz2MwMvZo-YL6dsg.PNG/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

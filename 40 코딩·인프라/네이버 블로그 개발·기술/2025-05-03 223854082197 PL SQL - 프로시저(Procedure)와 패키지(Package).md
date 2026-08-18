---
title: "2025-05-03 223854082197 PL SQL - 프로시저(Procedure)와 패키지(Package)"
type: blog-archive
status: active
created: 2025-05-03
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223854082197&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223854082197
published: "2025. 5. 3. 9:24"
body_hash: 668bae4fad394dd8e49589ea28e2cfee219a33f84f3c83091823f95ca4950d67
visibility: private
rag: exclude
---
# 2025-05-03 223854082197 PL SQL - 프로시저(Procedure)와 패키지(Package)

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223854082197&categoryNo=982
- 게시일: 2025. 5. 3. 9:24

## 본문

![](https://postfiles.pstatic.net/MjAyNTA1MDNfMzcg/MDAxNzQ2MjMwODAxNjE0.qD5y72eELLmXwEudU7YgIVWqTQXu27jnto0jtJiKvYQg.fNwm9gxE4VbLqNQxTUlDi0IIuxRVDeLhncIpUk2EaoQg.PNG/PL_SQL-001.png?type=w80_blur)

​

데이터베이스를 운용하거나 프로그램을 개발하는 과정에서는, 코드의 구조를 체계적으로 구성하고 유지 보수의 효율성을 높이기 위한 다양한 방법이 요구된다. 이러한 목적을 달성하기 위한 대표적인 방법 중 하나가 바로 프로시저(Procedure)와 패키지(Package)의 활용이다.

**​**

**1\. 프로시저와 패키지란 무엇인가?**

**프로시저** 란 특정 작업을 수행하는 명령문들을 하나의 블록으로 묶은 PL/SQL 프로그램 단위이다. 이와 같은 프로시저는 데이터베이스 내에 저장된 후, 필요할 때마다 호출하여 실행할 수 있다. 반복적이거나 일관된 처리가 필요한 작업에 유용하게 사용되며, 코드의 재사용성과 가독성을 크게 향상시킨다. 특정 작업을 반복적으로 수행해야 할 때, 프로시저를 작성해두면 필요할 때마다 호출하여 사용할 수 있어 효율적이다.

​

**패키지** 는 하나 이상의 관련된 프로시저, 함수, 변수 등을 논리적으로 묶어 관리할 수 있도록 하는 구조이다. 관련된 여러 프로시저나 함수, 변수 등을 하나로 묶어 관리할 수 있다. 하나의 패키지 내부에는 여러 개의 프로시저가 포함될 수 있으며, 프로그램의 모듈화를 촉진하고 코드의 구조화를 용이하게 한다. 코드의 논리적 구성과 재사용성을 높이는 데에 매우 유용하다.

**​**

**​**

**2\. 스토어드 프로시저(Stored Procedure)의 정의**

**스토어드 프로시저** 는 데이터베이스에 저장되어 있는 컴파일된 프로시저를 의미한다. 이들은 데이터베이스 오브젝트의 형태로 존재하며, 일반적인 SQL 문과 달리 반복 사용이 가능하고 실행 속도도 빠르다. 사전에 컴파일되어 저장되므로 실행 시 컴파일 과정이 생략되어 성능적인 이점을 제공한다.

**​**

**​**

**3\. 프로시저를 사용하는 이유**

프로시저는 다음과 같은 이유로 데이터베이스 내에서 자주 사용된다.

  * 특정 문제 해결이나 반복 작업의 자동화

  * 논리적으로 구분된 기능 단위의 모듈화

  * 코드의 재사용 가능

  * 테이블에 직접 접근하는 것이 아니라 프로시저를 통해 접근하게 하여 **보안성 향상**

  * 공유된 메모리 자원을 사용함으로써 **시스템 자원의 효율적인 활용**

**​**

**​**

**4\. 프로시저와 함수의 차이점**

프로시저와 함수는 구조적으로 유사하지만, 그 목적과 반환 방식에서 차이를 보인다.

  * **프로시저** 는 다량의 데이터를 처리하거나 복잡한 작업 흐름을 수행하는 데 적합하며, 결과값을 반환하지 않아도 된다.

  * **함수** 는 반드시 하나의 값을 반환해야 하며, 주로 계산 작업에 활용된다.

**구분** |  **프로시저** |  **함수**  
---|---|---  
출력 형식 |  다량의 정보 처리 |  단일 값 반환  
목적 |  작업 수행 중심 |  값 계산 중심  
사용 예 |  데이터 삽입, 갱신 |  총합 계산, 평균 구하기 등  
  
​

​

**5\. 프로시저 생성 방식**

오라클에서 프로시저를 생성하는 기본 구문은 다음과 같다.

CREATE OR REPLACE PROCEDURE 프로시저이름 (IN/OUT/INOUT 파라미터) AS PL/SQL 코드 블록 END 프로시저이름; 

  * OR REPLACE는 동일한 이름의 프로시저가 존재할 경우 기존 것을 덮어쓴다.

  * IN은 외부에서 프로시저로 값을 전달할 때 사용된다.

  * OUT은 프로시저가 실행된 결과값을 외부로 전달할 때 사용된다.

  * INOUT은 입력값도 받고, 결과값도 반환하는 형태이다.

  * RETURN 문은 프로시저가 중간에 종료되어야 할 때 사용된다.

​

​

**6\. 프로시저 예시**

아래는 사용자가 입력한 나이와 일치하는 회원의 나이를 100으로 변경하는 프로시저의 예시이다.

CREATE OR REPLACE PROCEDURE change_ages (i_age IN INTEGER) AS BEGIN UPDATE member SET age = 100 WHERE age = i_age; END change_ages; 

해당 프로시저는 다음과 같이 실행할 수 있다.

EXECUTE change_ages(62); 

이 명령을 실행하면, 나이가 62세인 모든 회원의 나이가 100세로 갱신된다.

​

​

**7\. 파라미터의 개념**

프로시저는 파라미터(Parameter)를 통해 외부와 정보를 주고받는다. 파라미터는 크게 다음과 같이 구분된다.

  * **Actual Parameter (실제 파라미터)** : 프로시저 호출 시 전달하는 값

  * **Formal Parameter (형식 파라미터)** : 프로시저 내부에서 정의된 변수

이 둘은 동일한 데이터 타입을 가져야 하며, 매개변수의 방향(IN, OUT, INOUT)에 따라 정보 전달의 방향이 결정된다.

​

​

**8\. 프로시저의 컴파일 및 재컴파일**

프로시저는 생성 시 자동으로 컴파일되며, 이후 실행 시에는 컴파일 과정 없이 바로 실행된다. 이는 성능 향상에 도움이 된다. 다만, 특정 상황에서는 **ALTER PROCEDURE** 문을 이용하여 명시적으로 재컴파일이 필요할 수 있다. 단, 이 명령은 패키지 내부가 아닌 독립된 프로시저에만 적용된다.

​

오라클에서는 부모 오브젝트가 재컴파일될 경우, 해당 오브젝트에 의존하고 있는 모든 하위 오브젝트가 자동으로 재컴파일된다. 이러한 과정은 시스템 부하를 증가시킬 수 있으므로 주의가 필요하다.

**​**

**​**

**9\. 프로시저 상태 및 오류 확인**

다음과 같은 데이터 딕셔너리 뷰를 통해 프로시저 및 기타 오브젝트의 상태와 오류를 확인할 수 있다.

**뷰 이름** |  **설명**  
---|---  
ALL_ERRORS |  접근 가능한 모든 오브젝트의 오류 목록  
ALL_SOURCE |  접근 가능한 모든 오브젝트의 소스 코드  
USER_OBJECTS |  현재 사용자가 소유한 오브젝트 목록  
USER_ERRORS |  현재 사용자의 오류가 있는 오브젝트 정보  
USER_SOURCE |  현재 사용자에게 속한 모든 오브젝트의 텍스트 소스  
DBA_OBJECTS |  전체 데이터베이스의 오브젝트 목록  
DBA_ERRORS |  전체 데이터베이스의 오류 목록  
DBA_SOURCE |  데이터베이스 전체에 대한 정보  
  
SELECT object_name, object_type, status FROM user_objects WHERE status = 'INVALID'; 

이 쿼리를 통해 오류가 발생했거나 유효하지 않은(INVALID) 상태의 오브젝트를 확인할 수 있다.

​

​

**10\. 기타 프로시저 관련 개념**

  * **프로시저 삭제** : 불필요한 프로시저는 DROP PROCEDURE 프로시저이름; 명령으로 삭제할 수 있다.

  * **프로시저 오버로딩** : 동일한 이름의 프로시저를 매개변수의 개수나 데이터 타입만 다르게 하여 여러 개 정의할 수 있다.

  * **재귀 프로시저** : 자신을 반복적으로 호출하는 프로시저로, 주로 트리 구조 탐색이나 반복 계산 등에 사용된다.

**​**

**​**

프로시저와 패키지는 데이터베이스 응용 프로그램을 구조화하고, 보안성과 성능을 향상시키는 데에 중요한 역할을 수행한다. 반복적인 작업을 효율적으로 처리하고, 모듈화를 통해 유지보수를 용이하게 하며, 데이터 접근에 대한 통제를 강화할 수 있다는 점에서 현대의 데이터베이스 시스템에서 필수적인 구성 요소로 자리 잡고 있다. 프로시저의 개념과 사용법을 올바르게 이해하고 적절히 활용하는 것이 안정적이고 효율적인 시스템 운영의 핵심이라 할 수 있다.

​

​

**11\. 실습 예제**

특정 나이를 가진 회원의 나이를 100으로 변경하는 프로시저이다.

​

**1) 테이블 생성**

먼저 예제를 실습하기 위해 사용할 간단한 회원 테이블을 생성한다.

CREATE TABLE member ( id NUMBER PRIMARY KEY, name VARCHAR2(50), age NUMBER ); 

​

**2) 예제 데이터 삽입**

테이블에 테스트용 데이터를 입력한다.

INSERT INTO member VALUES (1, '홍길동', 25); INSERT INTO member VALUES (2, '김철수', 62); INSERT INTO member VALUES (3, '이영희', 35); INSERT INTO member VALUES (4, '박민수', 62); COMMIT; 

위 데이터 중, age가 **62** 인 회원은 두 명이다.

​

**3) 프로시저 생성**

아래는 특정 나이(i_age)를 가진 회원들의 나이를 **100** 으로 변경하는 프로시이다.

CREATE OR REPLACE PROCEDURE change_ages(i_age IN NUMBER) AS BEGIN UPDATE member SET age = 100 WHERE age = i_age; DBMS_OUTPUT.PUT_LINE(i_age || '세를 가진 회원들의 나이를 100으로 변경하였습니다.'); END change_ages; / 

DBMS_OUTPUT.PUT_LINE은 메시지를 출력하기 위한 구문으로, SQL Developer 또는 TOAD 등의 툴에서 DBMS_OUTPUT 옵션을 활성화해야 확인 가능하다.

**​**

**4) 프로시저 실행**

EXECUTE change_ages(62); 

입력된 62에 해당하는 회원 두 명의 나이가 100으로 변경됩니다.​

**​**

**5) 결과 확인**

SELECT * FROM member; 

**ID** |  **NAME** |  **AGE**  
---|---|---  
1 |  홍길동 |  25  
2 |  김철수 |  100  
3 |  이영희 |  35  
4 |  박민수 |  100  
  
**​**

**6) 프로시저 삭제**

필요가 없어진 경우, 다음과 같이 삭제할 수 있다.

DROP PROCEDURE change_ages; 

**​**

**12\. 추가 예제**

이번에는 특정 나이 이상인 회원 수를 반환하는 프로시저 예제를 소개한다. OUT 파라미터를 이용하여 회원 수를 반환한다.

CREATE OR REPLACE PROCEDURE count_by_age( i_min_age IN NUMBER, o_count OUT NUMBER ) AS BEGIN SELECT COUNT(*) INTO o_count FROM member WHERE age >= i_min_age; DBMS_OUTPUT.PUT_LINE(i_min_age || '세 이상 회원 수: ' || o_count); END count_by_age; / 

실행 예:

VARIABLE v_cnt NUMBER; EXECUTE count_by_age(30, :v_cnt); PRINT v_cnt; 

이 결과는 age >= 30 인 회원 수를 반환하며, v_cnt 변수에 그 값을 저장한다.

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#데이터베이스 #DB개발 #오라클 #PLSQL #프로시저 #스토어드프로시저 #패키지 #SQL개발 #DB보안 #프로시저작성법 #함수와프로시저 #DB튜닝 #데이터관리 #IT개발자 #개발자블로그 #개발팁 #오라클프로시저 #PLSQL패키지 #DB관리자 #쿼리문 #개발공부 #코딩지식 #프로시저예제 #SQL문법 #DB성능 #코딩블로그 #컴파일오류 #파라미터 #코딩기초 #재귀함수

![](https://postfiles.pstatic.net/MjAyNTA1MDNfMTc1/MDAxNzQ2MjI3NDE4MTQ2.-T12IJ1oVCKII90-qkXtWSxV9Tjee9pooFWbgdBgpZYg.Vl69FnHiYIXDxjtsmsAxbcuGHX_gCgtGkErnQZYAyZMg.PNG/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

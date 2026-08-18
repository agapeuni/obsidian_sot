---
title: "2023-08-20 223188752367 집합 연산자 - UNION, UNION ALL, INTERSECT, MINUS"
type: blog-archive
status: active
created: 2023-08-20
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223188752367&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223188752367
published: "2023. 8. 20. 21:50"
body_hash: 924dec43a36dbf1251c63bcab68b9e67248771eacbefe706391d0012714ad951
visibility: private
rag: exclude
---
# 2023-08-20 223188752367 집합 연산자 - UNION, UNION ALL, INTERSECT, MINUS

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223188752367&categoryNo=982
- 게시일: 2023. 8. 20. 21:50

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTZfMjI5/MDAxNzQ0NzY3NjIwNjg4.BcxiXQ50uv4m6RuLWvBRCFxjTm_zul90SpKrNeClNxcg.IoNRoJxSwGC-h2tu0BdABE7jQ5nGX7ERlCNTAAs38d4g.PNG/Oracle-001_\(7\).png?type=w80_blur)

**​**

**1\. UNION**

**UNION** 구문은 첫 번째 쿼리의 모든 행을 두 번째 쿼리의 모든 행과 더하고, 중복된 행을 제거한 후, 결과를 리턴한다.

다음 예를 보면 첫 번째 쿼리에서 EMPLOYEES_ID와 LAST_NAME에서 LAST_NAME 열이 A나 B로 시작하는 직원 레코드를 얻고, 두 번째 쿼리에서는 EMPLOYEES_ID와 LAST_NAME 열에서 LAST_NAME 이 B나 C로 시작하는 직원 레코드를 얻었다. 쉽게 알 수 있겠지만 B로 시작되는 LAST_NAME 열을 가지는 직원 레코드는 첫 번째와 두 번째 쿼리 모두에서 선택되며, 중복되는 행들은 결과셋에서 제외된다.

EX>

**SELECT** EMPLOYEE_ID

, LAST_NAME 

**FROM** EMPLOYEES 

**WHERE** LAST_NAME **LIKE** 'A%'

**OR** LAST_NAME **LIKE** 'B%'

**UNION**

**SELECT** EMPLOYEE_ID

, LAST_NAME 

**FROM** EMPLOYEES 

**WHERE** LAST_NAME **LIKE** 'B%'

**OR** LAST_NAME **LIKE** 'C%'

**2\. UNION ALL**

**UNION** **ALL** 구문은 **UNION** 구문과 매우 비슷하지만 중복되는 행을 제외하지 않는다.

EX>

**SELECT** EMPLOYEE_ID

, LAST_NAME 

**FROM** EMPLOYEES 

**WHERE** LAST_NAME **LIKE** 'A%'

**OR** LAST_NAME **LIKE** 'B%'

**UNION** **ALL**

**SELECT** EMPLOYEE_ID

, LAST_NAME 

**FROM** EMPLOYEES 

**WHERE** LAST_NAME **LIKE** 'B%'

**OR** LAST_NAME **LIKE** 'C%'

**3\. INTERSECT****​**

**INTERSECT** 구문은 두 개의 쿼리를 받고 결과를 모은 다음, 두 결과셋에 모두 존재하는 레코드만을 리턴한다. 첫 번째 쿼리나 두 번째 쿼리에서만 리턴된 행은 결과셋에 포함되지 않는다. 앞에서와 같은 쿼리에 **INTERSECT** 구문을 이용하면 LAST_NAME이 B로 시작하는 직원 레코드만이 리턴될 것임을 예상할 수 있다. 이것은 첫 번째 쿼리나 두 번째 쿼리에만 포함되는 행들이 모두 결과셋에서 제거되기 때문이다.

EX>

**SELECT** EMPLOYEE_ID

, LAST_NAME 

**FROM** EMPLOYEES 

**WHERE** LAST_NAME **LIKE** 'A%'

**OR** LAST_NAME **LIKE** 'B%'

**INTERSECT**

**SELECT** EMPLOYEE_ID

, LAST_NAME 

**FROM** EMPLOYEES 

**WHERE** LAST_NAME **LIKE** 'B%'

**OR** LAST_NAME **LIKE** 'C%'

**4\. MINUS****​**

**MINUS** 집합 연산자는 첫 번째 쿼리에서만 리턴되며, 두 번째 쿼리에서는 리턴되지 않는 레코드만을 리턴한다. 즉, 첫 번째 쿼리에서 LAST_NAME이 A나 B로 시작하는 직원 레코드가 리턴되고, 두 번째 쿼리에서 LAST_NAME이 B나 C로 시작하는 직원 레코드가 리턴된다면, 이 두 쿼리에 MINUS 연산자를 적용한 뒤에는 LAST_NAME이 A로 시작하는 직원 레코드를 얻게 된다.

EX>

**SELECT** EMPLOYEE_ID

, LAST_NAME

**FROM** EMPLOYEES 

**WHERE** LAST_NAME **LIKE** 'A%'

**OR** LAST_NAME **LIKE** 'B%'

**MINUS**

**SELECT** EMPLOYEE_ID

, LAST_NAME 

**FROM** EMPLOYEES 

**WHERE** LAST_NAME **LIKE** 'B%'

**OR** LAST_NAME **LIKE** 'C%'

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#SQL #UNION #UNIONALL #INTERSECT #MINUS #SQL쿼리 #데이터베이스 #쿼리작성 #SQL연산자 #SQL테크닉 #중복제거 #데이터분석 #SQL공부 #프로그래밍 #프로그래밍학습 #SQL예제 #SQL명령어 #데이터추출 #기초SQL #SQL의기초 #SQL프로그래밍 #SQL조작 #데이터관리 #SQL연습 #SQL기초 #SQL쿼리연습 #SQL개념 #SQL실습 #데이터베이스쿼리

![](https://postfiles.pstatic.net/MjAyMzA4MjBfMTcx/MDAxNjkyNTM1NzI0OTM3.VSktoAYnI-jkMzmU4McDAJuP8GFhM95CW0ny0PgGEMEg.uxGRd-KbW9ZKuBJBTzc0MPKnVXA3olC6t1UK4w97jn8g.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

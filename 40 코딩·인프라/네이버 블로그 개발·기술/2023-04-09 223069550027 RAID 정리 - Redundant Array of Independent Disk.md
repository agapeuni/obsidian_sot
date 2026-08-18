---
title: "2023-04-09 223069550027 RAID 정리 - Redundant Array of Independent Disk"
type: blog-archive
status: active
created: 2023-04-09
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223069550027&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223069550027
published: "2023. 4. 9. 21:37"
body_hash: 700fd64bb29e157d87c861add0cb3aaffa51abf6c598518de3b8c996cea7b1c3
visibility: private
rag: exclude
---
# 2023-04-09 223069550027 RAID 정리 - Redundant Array of Independent Disk

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223069550027&categoryNo=982
- 게시일: 2023. 4. 9. 21:37

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTBfMTQ0/MDAxNzQ0MjI3ODU4ODU4.H4PsnhfWffYTYjvb-ICILi6hDgAm0aKg4HZNNUdK11Eg.0La97GLjtsua4ot0SX7MGr8KHqtZCg6U3TkU3Ntl_jYg.PNG/%EC%A3%BC%EB%B3%80%EC%9E%A5%EC%B9%98-001_\(8\).png?type=w80_blur)

​

1\. RAID 개요

RAID는 Redundant Array of Independent Disks의 약어이다. 영어 뜻을 그대로 옮기자면 독립적인 디스크의 중복 배열 정도이다. RAID를 적용하면 여러 개의 디스크를 거대한 하나 드라이브로 사용할 수 있거나 여러 디스크에 데이터를 분산 중복으로 저장하여 드라이브 고장에도 복구가 가능하게 구성할 수 있다.

​

​

2\. RAID 0 (스트라이핑)

데이터를 블록 단위로 분할하여 여러 디스크에 분산으로 저장하여 읽기/쓰기 속도를 향상시킨다. 디스크에 오류가 발생하면 저장된 데이터가 손실된다. 하지만 중복 없이 저장하기 때문에 사용 효율과 성능이 좋다. 속도 면에서는 RAID 버전 중에 가장 빠르다. 2개 이상의 디스크가 필요하며 구성하고 나서 전체 용량에 데이터를 저장할 수 있다.

​

​

3\. RAID 1 (미러링)

동일한 데이터를 두 개의 디스크에 기록하여 한 쪽에 오류가 발생하면 다른 디스크에 데이터가 있어서 손실되지 않는다. 데이터를 보호하는 장점은 있지만 신뢰성을 보장하기 위해 동일한 데이터를 두 개의 디스크에 저장하여 용량은 두 배가 된다. 2개 이상의 디스크가 필요하며 구성하고 나면 전체 용량에서 50% 용량에 데이터를 저장할 수 있다.

​

​

​

4\. RAID 0 + 1

RAID 0과 RAID 1을 조합하여 데이터를 블록 단위로 분할하여 병렬로 기록하고, 두 개의 디스크에 같은 데이터를 저장한다. 동일한 데이터를 두 개의 디스크에 저장하여 신뢰성이 있지만 용량은 두 배가 된다. RAID 0의 성능 이점과 RAID 1의 데이터 보호를 할 수 있다. 4개 이상의 디스크로 구성할 수 있고 전체 용량에서 50% 용량에 데이터를 저장할 수 있다.

​

​

​

5\. RAID 1 + 0

RAID 1과 RAID 0을 조합하여 두 개의 디스크에 같은 데이터를 저장하고 데이터를 블록 단위로 분할하여 병렬로 저장한다. RAID 1의 중복성과 RAID 0의 빠른 속도를 결합한 방식으로 용량 비용이 배가되지만 안전한 RAID 구성이다. 4개 이상의 디스크로 구성할 수 있고 전체 용량에서 50% 용량에 데이터를 저장할 수 있다.

​

​

6\. RAID 5

병렬처리가 가능하여 대량의 작은 크기 데이터 저장에 효율적이고 디스크의 오류에도 복구가 가능하다. 각각의 디스크마다 패리티를 블록 단위로 저장한다. 3개 이상의 디스크로 구성할 수 있고 디스크 1개에 해당하는 용량을 제외하고 데이터를 저장할 수 있다. 두 개 이상이 디스크에서 오류가 발생하는 경우는 복구가 어렵다.

​

​

7\. RAID 6

RAID 5의 패리티를 1개에서 2개로 늘려서 동시에 2 개의 디스크가 고장 난 경우에도 데이터 복구가 가능하다. RAID 5보다 신뢰성은 보다 우수하지만 패리티를 추가해서 저장하기 때문에 디스크 사용 효율은 RAID 5보다 떨어진다. 데이터를 보호하는 장점은 있지만 속도가 느리고 순수하게 저장할 수 있는 데이터 공간이 줄어든다.

.

​

​

![](https://blogfiles.pstatic.net/MjAyNjA2MTdfMTI4/MDAxNzgxNjIzNzc1NzA1.2QYwsPb7SzsAzNxbABqntGpXAscgNcqLRqQrRj6RQL0g.sS1rzJuq4-3ERN9qM8z69dPB5Y6mWd4F-WOitRfYhhEg.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w1)

#RAID #데이터저장 #RAID개요 #RAID0 #RAID1 #RAID5 #RAID6 #RAID0+1 #RAID1+0 #디스크배열 #데이터복구 #데이터보호 #성능향상 #미러링 #스트라이핑 #디스크오류 #패리티 #RAID구성 #중복성 #데이터안전 #대량데이터 #신뢰성 #스토리지 #하드웨어 #IT정보 #컴퓨터관리 #서버관리 #대용량저장 #디스크사용효율 #데이터센터

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._

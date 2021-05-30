---
title: "AWS DynamDB, RDS, Aurora"
category: AWS
date: 2021-05-30 01 : 38 : 47
comments: true
order: 5
---

## AWS DynamoDB

#### What?

Key- value 구조를 가진 NoSQL(Not Only SQL) 데이터베이스

**완전관리형 서비스** 

- 프로비저닝, 복제, 버전 관리, 클러스터 확장 모두 관리해준다.

#### 특징

- 매우 빠른 쿼리 속도

- **Auto-Scaling 기능** 탑재 : 데이터 생성시, 크기가 정해져 있는데, 오토스케일링을 이용하면 확장/축소에 용이하다.

- 테이블 생성시, 스키마 생성 필요 없다 : 실시간으로 들어오는 데이터를 보관하는데 탁월하다.

- **모바일, 웹, IoT데이터** 사용시 추천됨

#### DynamoDB의 구성

![img](https://media.vlpt.us/images/songa29/post/7e8e94b2-207d-4bfd-ba24-a8cb5612b135/image.png)

- **테이블** (Table)
- **아이템** (Items) - 행(row)과 개념과 유사
- **특징** (Attributes) - 열(column)과 유사
- **Key-Value** (Key : 데이터의 이름, Value : 데이터 자신)
  예시) JSON, XML와 같이 Key-Value 형식

#### DynamoDB에서 데이터 읽어오는 방식

1. **Query**

- **Primary Key를 사용**하여 데이터 검색
- Query사용시 모든 데이터(컬럼) 반환
- **ProjectionExpression 파라미터**
  우리가 보고 싶은 컬럼만 볼 수 있도록 수정, 일종의 필터링 역할

2. **Scan**

- 모든 데이터를 불러옴 (**primary key 사용 X**)

- **ProjectionExpression 파라미터**

- 순차적방법 (Sequential)

- 테이블 크기가 상대적으로 크지 않고 테이블에 primary key의 정의가 필요없을 경우 사용


3. **Query VS Scan**

- Query가 Scan보다 훨씬 효율적이다.
- Scan은 데이터의 크기 일정하지 않다.
- 따라서 Query 사용 추천



## AWS RDS(Relational DB Service)

#### what?

- 관계형 데이터베이스

- 완전 관리형 서비스가 아니므로, 스케일링, 복제본 확장 기능은 사용자가 구축해야 한다.

- AWS에서는 Microsoft SQL, Oracle, MySQL, Postgre, Aurora, Maria DB를 제공한다.

- AWS에서 RDMS를 이용할 경우 **EC2 인스턴스에 RDMS를 설치하는 방법**과

- **AWS가 제공하는 RDS를 사용** 2가지가 있다.



## AWS Aurora

#### What?

- RDS와 같은 AWS의 관리형 서비스

- aws에서 Mysql과 PostgreSQL을 클라우드 기반에 맞게 재구성한 DB

- MySQL 및 PostgreSQL과 호환되는 **완전 관리형** 관계형 데이터베이스 엔진

#### 장점

- MySQL, PostgreSQL에 비해 몇 배의 성능을 발휘하는 등 뛰어나다.

- RDS에 비해서도 내구성이 좋고 장애시의 장애 조치 속도 등에서 뛰어나다.
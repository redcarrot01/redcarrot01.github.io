---
title: "REST API"
category: Web
date: 2021-05-29 11:21:05
comments: true
order: 1
---

## What?

### **REST ?** 

- 분산 시스템 설계 위한 아키텍처 스타일로, 

- HTTP **URI**를 통해 **자원**을 표시하고 **HTTP Method**를 통해 자원에 대한 **처리**(CRUD)를 표현


**RESTFUL API?**

- REST를 만족하는 API 

- **사람이 읽을 수 있는 API**라는 것이 특징

- HTTP를 사용하기 때문에 **HTTP의 특성을 그대로 반영**


**장점**

- 또한 **별도의 인프라 구축이 필요없다**.

- 서버와 클라의 역할 명확하게 분리함(REST 서버는 API 제공, 클라이언트는 세션,로그인 등 관리)

- HTTP 프로토콜 따르는 모든 플랫폼에서 사용 가능

**단점**

- 명확한 표준이 존재하지 않는다

- 사용할 수 있는 메소드가 4가지밖에 없다.(POST, GET, PUT, DELETE)

  

## How? (REST 구성 요소)

**1. 자원 : URI**

- 모든 자원에 고유한 ID가 존재하고, 이 자원은 Server에 존재

- 자원을 구별하는 ID는 ‘/groups/:group_id’와 같은 HTTP URI 다.

  > URI (Uniform Resource Identifier) : 자원 식별자
  >
  > URI의 하위 개념으로 URL(네트워크 주소)이 있다.
  >
  > URL (Uniform Resource Locator)
  >
  > 예를 들어,
  >
  > http://opentutorials.org:3000/main?id=HTML&page=12 는 URI인 자원의 식별자
  >
  > http://opentutorials.org:3000/main 은 URL로 자원의 위치
  >
  > ?id=HTML&page=12 은 id가 HTML이고 page 정보를 식별함
  >
  > 

**2. 행위 : HTTP METHOD(POST, GET, PUT, DELETE)**

>| POST   | POST를 통해 해당 URI를 요청하면 리소스를 생성 |
>| ------ | --------------------------------------------- |
>| GET    | GET를 통해 해당 리소스를 조회                 |
>| PUT    | PUT를 통해 해당 리소스를 수정                 |
>| DELETE | DELETE를 통해 리소스를 삭제                   |

**3. 표현**

- 클라가 자원 조작 요청하면, 서버는 이에 응답

- JSON, XML 이런 형태로 표현됨

  

## Why? (REST가 필요한 이유)

- 애플리케이션의 분리 및 통합 : REST API 사용하면 서로 다른 모듈 상호간 통신 가능

- 서버는 다양한 플랫폼 위에서 통신 가능해야함 (웹 , 모바일)

  

## HTTP 응답 상태 코드

| 200  | 요청 정상 수행                                               |
| ---- | ------------------------------------------------------------ |
| 201  | 리소스 성공적으로 생성됨(POST)                               |
| 400  | 요청 부적절한 경우                                           |
| 401  | 클라가 인증되지 않은 상태에서 리소스 요청(로그인 안 했을 때 요청) |
| 405  | 사용 불가능한 메소드 이용한 경우                             |
| 301  | 클라가 요청한 URI가 변경 된 경우                             |
| 500  | 서버에 문제 있는 경우                                        |


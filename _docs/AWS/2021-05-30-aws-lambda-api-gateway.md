---
title: "AWS Lambda, API gateway"
category: AWS
date: 2021-05-30 01 : 33 : 47
comments: true
order: 3
---

## AWS Lambda

**What?**

- 서버리스 구성할 때 핵심 서비스로,

- 개발자는 서버에 대한 걱정 없이 코드를 실행 할 수 있다.(함수 같은 기능)

- 이벤트를 통하여 람다를 실행시키는데, 이벤트랑 '업로드', '삭제' 이런 행위를 말함

**장점**

- nodejs, python, java, go 등 다양한 언어를 지원한다. 

- **Lambda Function이 실행될때만 비용 지불**

- cloud watch(모니터링) : 람다 함수 실행시 모니터링 가능

**사용 예 - 중간 다리 역할**

1. S3 버켓에 파일을 올리는 경우 PutObject라는 이벤트 발생-> 람다함수 실행시킴 -> 람다는 데이터 변환, 불필요한 데이터 삭제 -> 람다는 데이터 베이스에 깨끗한 데이터를 업로드
   ![img](https://media.vlpt.us/images/songa29/post/358019a0-45ce-4db1-80f0-49efe3f6507e/image.png)
2. IoT를 통해 실시간 데이터가 들어오는 경우 topic을 통해 다양한 이벤트들을 관리, 데이터를 보내 람다 함수 호출 -> SNS 실시간 경고 줄 수 있음
   ![img](https://media.vlpt.us/images/songa29/post/65812f83-54d7-431f-aeb7-cd300d388ff7/image.png)



## AWS API GATEWAY

**what?**

- 벡엔드 서비스의 데이터, 기능에 접근할 수 있는 "출입구" 역할 서비스

- RESTFUL API 로 운용할 때,   API 손쉽게 생성, 관리, 모니터링 제공해주는 서비스

- 주로 Lambda를 연결하여 안정적인 트래픽 관리 및 제어를 담당

- 모니터링은 CloudWatch 로그를 통해 확인

- 요금이나 시작 비용은 없고, 전송한 데이터 양에 대한 요금을 결제



## 참고했습니다.

- [https://aws.amazon.com/ko/api-gateway/](https://aws.amazon.com/ko/api-gateway/)

- [https://velog.io/@songa29/AWS-Lambda%EB%9E%80](https://velog.io/@songa29/AWS-Lambda%EB%9E%80)
---
title: "AWS Amplify, Cognito"
category: AWS
date: 2020-05-31 03:47:47
comments: true
order: 6
---



## AWS Amplify

#### What?

웹 및 앱 개발 시에 필수적인 백엔드 구현, 배포, 테스트와 같은 단계를 손쉽게 할 수 있도록 도와주는 개발 플랫폼

 JavaScript, React, Angular, Vue, Next.js 등의 널리 사용되는 웹 프레임워크와 Android, iOS, React Native, Ionic, Flutter 등의 모바일 플랫폼을 지원

#### How? 작동 방식

**개발** : Amplify를 이용하면 full-stack 웹과 모바일의 백엔드를 개발할 수 있다.
Amplify UI나 CLI 통해서 백엔드 설정 -> Amplify 라이브러리를 웹/앱 백엔드와 연결 -> 통합

<img src="https://user-images.githubusercontent.com/38436013/120157472-08fcc700-c22e-11eb-854e-251f185589a5.png" alt="image" style="zoom:67%;" />

**제공** : 정적 페이지 호스팅
amplify 콘솔에 깃에 있는 소스나 파일 업로드 -> 빌드 셋팅 -> amplify 콘솔에서 배포

<img src="https://user-images.githubusercontent.com/38436013/120157499-0e5a1180-c22e-11eb-9044-2be9fb34d821.png" alt="image" style="zoom:67%;" />

**관리** : 사용자와 앱 관리
Amplify 어드민에 접근 권한을 준다 -> 사용자와 컨텐츠 관리한다 

<img src="https://user-images.githubusercontent.com/38436013/120157523-13b75c00-c22e-11eb-85ab-eb2c8bda2b6e.png" alt="image" style="zoom:67%;" />

#### 장점

- 빠른 백엔드 구성 : 인증, 스토리지, 데이터 등 확장 가능한 백엔드
- 원활한 프론트엔드 연결 : 코드 몇줄 만으로 웹, 앱에서 amplify 라이브러리 사용 가능
- 클릭 몇 번만으로 배포 : amplify 콘솔 이용하면 git 기반 CI/CD 워크플로우로 정적 페이지 호스팅(amplify 콘솔에서 애플리케이션 레포 연결만 하면 코드 커밋할 때마다 배포됨)

#### Amplify와 연관된 서비스

<img src="https://user-images.githubusercontent.com/38436013/120157433-faaeab00-c22d-11eb-9bca-61210587732b.png" alt="image" style="zoom:67%;" />

- **AWS AppSync** :  GraphQL을 사용하여 애플리케이션에서 필요로 하는 데이터를 가져올 수 있도록 하는 관리형 서비스, 오프라인 상태에서도 로컬로 데이터 액세스 가능, 온라인 상태가 되면 데이터 동기화 해주는 기능을 제공
- **Amazon Cognito** :  가입, 로그인, 액세스 제어 기능을 갖춘 인증 관리 서비스, Identity Pool 을 통해 Facebook, Google, Amazon과 같은 소셜 로그인과도 연동이 가능
- **Amazon S3** : 데이터 저장하고 검색할 수 있는 간단한 API 제공하는 완전 관리형 스토리지 서비스, IAM 정책이나 S3버킷 정책으로 지정된 대상에게 권한을 줄 수 있다

## AWS Cognito

#### What? 

웹 / 앱에 대한 인증, 권한 부여 서비스를 제공한다. 인증방법으로는 직접 로그인, 소셜 로그인이 있다. 사용자 풀과 자격 증명 풀 두 가지가 있다. 사용자 풀은 앱 사용자의 가입 및 로그인 옵션을 제공하는 사용자 디렉토리다. 자격 증명 풀은 사용자 액세스 권한을 부여할 수 있다.  프리티어로 무료다.

#### How? 동작 방식

사용자 풀과 자격 증명 풀 함께 사용하는 시나리오 : 사용자 인증 후 다른 aws 서비스에 대한 권한 받기

1. 사용자 풀 이용하여 로그인, 토큰 받음
2. 자격 증명 통해 토큰 -> 자격 증명 교환
3. 자격 증명 통해 s3, dynamodb 등 접근

<img src="https://user-images.githubusercontent.com/38436013/120157320-e1a5fa00-c22d-11eb-8c1c-3bc97e4ec16b.png" alt="image" style="zoom:67%;" />



#### 참고했습니다.

- [https://aws.amazon.com/ko/amplify/](https://aws.amazon.com/ko/amplify/)
- [https://dev.classmethod.jp/articles/amplify-android-cognito-auth/](https://dev.classmethod.jp/articles/amplify-android-cognito-auth/)
- [https://docs.aws.amazon.com/ko_kr/cognito/latest/developerguide/what-is-amazon-cognito.html](https://docs.aws.amazon.com/ko_kr/cognito/latest/developerguide/what-is-amazon-cognito.html)
# 멘티 유니온: 성장을 위한 커뮤니티

이 프로젝트는 개인이 기존 스프링 부트로 제작한 프로젝트를 Node진영의 NestJS 프레임워크로 변경하여 새로 구축하며, GPT를 이용해 가상의 팀을 편성하여 제작하는 실험적이면서 실 서비스까지 목표로하는 프로젝트입니다.

## 프로젝트 목표

- 멘티들이 서로 의지하며 성장할 수 있는 커뮤니티 구축
- 지식과 경험 공유를 통한 학습 촉진
- 멘티들의 상호작용을 통해 멘토 역량을 개발하고 인정받을 수 있는 시스템 마련

## 주요 기능

- 커뮤니티 포럼: 멘티들이 질문, 답변, 토론을 통해 정보를 공유할 수 있는 공간
- 세미나 및 워크샵: 멘티들이 자신의 지식을 공유하고, 서로 학습할 수 있는 온라인/오프라인 이벤트 개최
- 레벨링 시스템: 멘티들의 활동에 따라 포인트를 부여하고, 일정 레벨에 도달하면 멘토로 승격
- 멘토-멘티 매칭 시스템: 높은 레벨의 멘티(혹은 멘토)와 멘티 간의 1:1 멘토링 기회 제공
- 리소스 라이브러리: 유용한 자료, 가이드, 튜토리얼 등을 공유하는 자료실

## 커뮤니티 참여 방식

- 멘티 가입: 멘티로 가입하여 커뮤니티 활동 시작
- 활동 기반 포인트 제도: 포럼 참여, 세미나 주최, 자료 공유 등의 활동으로 포인트 획득
- 레벨 업 및 멘토 승격: 일정 포인트 도달 시 자동으로 레벨 업, 특정 레벨에서 멘토로 승격 가능

## 기술 스택

- 웹 프론트엔드: React, Vue.js 등을 활용한 사용자 친화적 인터페이스
- 백엔드: Node.js, Express.js 등 서버 사이드 로직 및 API 개발
- 데이터베이스: MongoDB, MySQL 등 커뮤니티 데이터 관리
- 클라우드 및 배포: AWS, Docker 등을 통한 서비스 호스팅 및 관리

## API 정의

- protocol: https
- host: api.menteeunion.kro.kr
- tls: ✅ (적용)
- type: reverse proxy
- base_path: api
- api_path: https://api.menteeunion.kro.kr/api

토큰 이용 API: `AUTH` 표기

### Users

| method   | uri                               | query | params   | body            | desc                         | auth |
| -------- | --------------------------------- | ----- | -------- | --------------- | ---------------------------- | ---- |
| `GET`    | /users                            |       |          |                 | 전체 조회                    |      |
| `GET`    | /users/:id                        |       | pk       |                 | 단건 조회                    |      |
| `GET`    | /users/profile                    |       |          |                 | 단건 조회                    | ✅   |
| `GET`    | /users/profile/seminars           |       |          |                 | 유저 세미나 정보 조회        | ✅   |
| `GET`    | /users/profile/forums             |       |          |                 | 유저 포럼 정보 조회          | ✅   |
| `GET`    | /users/profile/points             |       |          |                 | 유저 포인트 시스템 정보 조회 | ✅   |
| `GET`    | /users/profile/resource/:filename |       | filename |                 | 유저 프로필 이미지 조회      | ✅   |
| `GET`    | /users/socket/profile             |       |          |                 | 소켓서버 프로필 조회         | ✅   |
| `POST`   | /users                            |       |          | user table 참조 | 회원가입                     | ✅   |
| `POST`   | /users/points/already             |       |          |                 | 이미 추천했는지 여부         | ✅   |
| `POST`   | /users/user-points                |       |          |                 | 특정 사용자 추천             | ✅   |
| `POST`   | /users/check/email                |       |          |                 | 이메일 중복 검증             | ✅   |
| `POST`   | /users/check/username             |       |          |                 | 유저네임 중복 검증           | ✅   |
| `PUT`    | /users/:id                        |       | pk       |                 | 회원정보 수정                | ✅   |
| `PUT`    | /users/profile                    |       | pk       |                 | 회원 프로필 이미지 수정      | ✅   |
| `DELETE` | /users/:id                        |       | pk       |                 | 회원탈퇴                     | ✅   |
| `DELETE` | /users/dormant                    |       | pk       |                 | 회원탈퇴 취소                | ✅   |

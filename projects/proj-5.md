---
layout: post
title: "채팅상담 오피스"
---



**개발기간 　　 ┃** 2022.08 ~

**프로젝트 개요 ┃** 고객 상담용 백오피스 - 상담원 상담, 챗봇 상담 메뉴 개발

**개발환경 　　 ┃** TypeScript, React, GraphQL, RabbitMQ, Redis, ElasticSearch

1. 기존 프로젝트 JavaScript -> TypeScript전환
    - 채팅상담, 챗봇상담
2. 신규개발
    - 채팅상담, 챗봇상담
        - 업무 시작/종료
        - 채팅 상태 변화 알림
        - 상담원 자동 할당 


---
**JavaScript -> TypeScript 전환**
- 기존 프로젝트 JavaScript -> TypeScript 전환
- 팀내 TypeScript convention 논의 및 적용
- 담당 기능: 채팅 상담, 챗봇 상담


**UI 개편에 따른 화면 재개발, 신규 기능 개발**
- 기획자, 디자이너와 소통, 협업 경험
- React, GrpahQL의 Apollo Client를 통한 상태관리
- RabbitMQ 사용하여 pub/sub모델 구현 - 실시간 상태반영
- Atomic 디자인 패턴에 기반한 컴포넌트 개발
- Redis 사용한 캐싱 처리

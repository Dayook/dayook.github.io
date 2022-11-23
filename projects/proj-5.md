---
layout: post
title: "채팅상담 오피스"
---

#### Office

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
프로젝트 구조가 확장됨에 따라, JavaScript로 쓰인 기존의 프로젝트를 TypeScript로 전환하는 작업을 하였습니다. React 컴포넌트와 훅을 TypeScript로 작성하는 방법에 대하여 팀원들과 함께 고민하며 컨벤션을 정의하여 실무에 적용하였습니다.
채팅상담(상담원 상담)과 챗봇상담(메신저로 유입된 챗봇 대화를 모니터링 할 수 있는 메뉴)를 담당하여 기존 기능 TypeScript 전환과 신규 기능 개발을 하였습니다.

**채팅상담, 챗봇상담**
요구사항에 맞춰 신규 개발 및 기존기능 개선을 진행하였습니다.
실시간 반영돼야 하는 상태값들은 대하여 RabbitMQ를 사용한 AMQP통신으로 pub/sub모델을 구현하여 처리하였습니다.
입출력이 빈번한 값들에 대하여 Redis에 캐싱처리를 하고, 받아온 데이터는 React와 ApolloClient로 상태관리를 하여 인터랙티브한 화면을 구현하였습니다.
---
layout: post
title: "채팅상담 메신저"
---

---

{% include brick_carousel.html height="50" unit="%" duration="7" %}
<!-- {% include carousel.html height="50" unit="%" duration="7" %} -->
**개발기간 　　 ┃** 2022.05 ~ 2022.07

**프로젝트 개요 ┃** 고객 상담용 챗봇 메신저 - 고객의 메시지에 챗봇이 응답하여 고객응대를 도울 수 있는 서비스

**개발환경 　　 ┃** React, GraphQL, RabbitMQ, Redis, Node.js, ElasticSearch

**서비스 url** 
- [새창 링크 1](https://chat.brickchat.co.kr/chat/c13977f0-e4bf-43d7-ba0a-426a30fe5907){:target="_blank"}
- [서비스 링크 1](https://smarthippo.kr/){:target="_blank"}
- [서비스 링크 2](https://www.moccasom.co.kr/){:target="_blank"}

해당 서비스는 쇼핑몰 홈페이지 하단에 부착되어, 고객이 메신저 아이콘을 클릭하고 메시지를 전송함에 따라 동작합니다.
모바일 환경에서는, 인트로 아이콘 클릭 시 '새창 링크 1'처럼  쇼핑몰과 분리된 새로운 창에서 메신저를 실행할 수 있습니다.


#### 💡 채팅, 메인, 인트로(메신저 진입) 화면 개빌

- UI 개편에 따른 화면 재개발, 신규 기능 개발
- React, RabbitMQ 사용한 실시간 챗봇 채팅화면 개발
- 상태 관리: GraphQL의 Apollo Client 활용
- Atomic 디자인 패턴에 기반한 컴포넌트 개발
- 크로스 브라우징 대응

#### 💡 검색 기능 개선

- 채팅화면 상담내용 검색 기능 사용성 개선
  - React 기반, 검색상태 저장 모듈 개선
- 날짜검색 기능 신규 개발
  - ElasticSearch 쿼리 개발
<!-- React와 GraphQL의 ApolloClient를 통해 상태를 관리하고 ElasticSearch  -->




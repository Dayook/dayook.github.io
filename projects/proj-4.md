---
layout: post
title: "채팅상담 메신저"
---

---

{% include brick_carousel.html height="50" unit="%" duration="7" %}
<!-- {% include carousel.html height="50" unit="%" duration="7" %} -->
**개발기간 　　 ┃** 2022.05 ~ 2022.07

**프로젝트 개요 ┃** 고객 상담용 챗봇 메신저 - 고객의 메시지에 챗봇이 응답하여 고객응대를 도울 수 있는 서비스

**개발환경 　　 ┃** React, GraphQL, RabbitMQ, Redis, ElasticSearch

**서비스 url** 
- [새창 링크 1](https://chat.brickchat.co.kr/chat/c13977f0-e4bf-43d7-ba0a-426a30fe5907){:target="_blank"}
- [서비스 링크 1](https://smarthippo.kr/){:target="_blank"}
- [서비스 링크 2](https://www.moccasom.co.kr/){:target="_blank"}
- [서비스 링크 3](https://fromdayone.co.kr/){:target="_blank"}

해당 서비스는 쇼핑몰 홈페이지 하단에 부착되어, 고객이 메신저 아이콘을 클릭하고 메시지를 전송함에 따라 동작합니다.
모바일 환경에서는, 인트로 아이콘 클릭 시 '새창 링크 1'처럼  쇼핑몰과 분리된 새로운 창에서 메신저를 실행할 수 있습니다.


**💡 검색 기능 개선** 
상담 내용 검색 시, 검색 결과와 화면의 포커싱이 맞지 않는 이슈를 처리하였습니다.
검색에 필요한 데이터 구조를 파악하고, 이를 고려하여 포커싱에 필요한 상태를 관리하는 모듈을 개선함으로써 문제상황을 해결할 수 있었습니다.

이어서 날짜 검색(대화 내역이 존재하는 날짜에 대해 표시하고, 해당 날짜로 대화창을 이동할 수 있도록 하는 기능)을 신규 개발하였습니다.
<!-- React와 GraphQL의 ApolloClient를 통해 상태를 관리하고 ElasticSearch  -->

**UI 개편에 따른 화면 재개발** 
오픈 이전, UI를 전면 재개편하는 결정이 있었습니다. 그에 따라 기존 프로젝트의 기능들을 새로운 컴포넌트 구조로 옮기는 업무를 진행하였습니다.
인트로, 메인, 채팅 화면을 담담하여 화면 재개발 작업을 하였습니다. 



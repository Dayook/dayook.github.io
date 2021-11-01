---
layout: post
title: "[React] 리액트 이해 - 기본개념들 "
---

- 리액트는 자바스크립트 라이브러리, 사용자 인터페이스를 만드는 데 사용
- 오직 View에만 신경쓰는 라이브러리

#### Rendering

- 사용자 화면에 뷰를 보여주는 것
- 초기 렌더링 : 최초로 실행
  - `render() {...}` : 뷰가 어떻게 생겼고 작동하는지 객체를 반환
- 리렌더링 : 컴포넌트의 데이터 변경으로 다시 실행
  - 새로운 데이터로 render 함수 다시 호출 => 이전에 만든 컴퍼논트와 정보를 비교하고 최소한의 연산으로 DOM 트리를 업데이트.

#### Virtual DOM

- DOM

  - Document Object Model의 약어
  - 객체로 문서 구조를 표현하는 바법으로 XML/ HTML로 자성
  - 트리 형태, 특정 노드를 찾고 수정/제거/삽입 가능
  - 동적 UI에는 부적합, 규모 큰 어플리케이션에는 성능 이슈 발생

- 해결법
  - DOM update를 추상화함으로써 DOM 처리 횟수를 최소화
  - Virtual DOM => 실제 DOM 아닌 이를 추상화한 객체를 구성하여 사용
  - 업데이트 처리 간결성 제공.

출처: 『리액트를 다루는 기술』, 길벗출판사

<!-- 1. 자식 컴포넌트엣어 부모 컴포넌트로 상태 전달
2. onclick 함수 자동으로 실행되는 문제 => const가 아닌 function으로 정의
https://stackoverflow.com/questions/10101899/onclick-event-getting-called-automatically -->

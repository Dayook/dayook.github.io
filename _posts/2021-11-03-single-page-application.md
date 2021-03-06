---
layout: post
title: "[React] SPA의 이해 "
---

SPA - Single Page Application의 약어. 한 개의 페이지로 이루어진 어플리케이션. 기존에는 다른 페이지로 이동할 때마다 새로운 html을 받아 오고, 서버에서 리소스를 전달받아 해석한 뒤 화면에 보여줌(서버 측에서 화면 준비).

하지만 새로운 화면을 보여줘야 할 때마다 서버 측에서 뷰를 준비한다면 트래픽이 많이 나오고 서버에 높은 부하가 걸릴 가능성 有. 특히나 사용자와의 인터랙션이 자주 발생하는 모던 웹 애플리케이션에는 적합하지 않을 수 있음.

바뀌지 않는 부분까지 새로 불러와서 보여 주어야 하므로 불필요한 로딩이 있어 비효율적이기도 함.

=> 뷰 렌더링은 사용자의 브라우저가 담당. 인터랙션이 발생하면 **필요한 부분만 자바스크립트를 사용하여 업데이트**

#### SPA 단점

- 앱 규모 커질 시 자바스크립트 파일 커짐
  - 방문하지 않을 수 있는 페이지 스크립트도 로딩하기 때문
  - 코드 스플리팅 사용 시 라우트별로 파일을 나누어 개선 가능
- 좋지않은 SEO(Search Engine Optimization)
  - body가 비워져있기때문에 검색 어려움 
  - => SSR 도입
  - SSR은 CSR 보다 첫페이지 로딩이 빠르고 SEO 적합
    - 서버 과부하걸릴 가능성
    - TTV TTI 차이 줄이기위해 고민해야
    - React + Next.js로 구현가능  

#### 라우팅

- 다른 주소에 다른 화면을 보여주는 것
- 리액트 라우팅 라이브러리 : react-router
  - 클라이언트 사이드의 라우팅 도우며
  - 서버 사이드 렌더링 시의 컴포넌트들도 제공해줌

  출처: 『리액트를 다루는 기술』, 길벗출판사

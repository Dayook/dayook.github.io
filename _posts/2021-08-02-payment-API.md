---
layout: post
title: "[javascript] 결제 API 사용하기 "
---

수익을 내야하는 모든 사이트의 핵심적인 기능 결제하기. 아임포트라는 서비스가 기존의 복잡한 구현과정 대신
코드 몇 줄 만으로 PG(결제 대행 서비스)사 연동 / 다양한 결제 기능을 가능하게 해주고 있다.

자세한 과정은 [아임포트 기술문서](https://docs.iamport.kr/)에서 직접 확인 가능하다.

#### 0. 결제정보 받을 input form 

#### 1.아임포트 라이브러리 추가
```html
  <!-- jQuery -->
  <script type="text/javascript" src="https://code.jquery.com/jquery-1.12.4.min.js" ></script>
  <!-- iamport.payment.js -->
  <script type="text/javascript" src="https://cdn.iamport.kr/js/iamport.payment-1.1.8.js"></script>
```

#### 
---
layout: post
title: "결제 API 사용하기 - 아임포트 연동 "
---

수익을 내야하는 모든 사이트의 핵심적인 기능 결제하기. 아임포트라는 서비스가 기존의 복잡한 구현과정 대신
코드 몇 줄 만으로 PG(결제 대행 서비스)사 연동 / 다양한 결제 기능을 가능하게 해주고 있다.

#### 0. 결제에 필요한 정보 담는 form 작성

#### 1.아임포트 라이브러리 추가

```html
<!-- jQuery -->
<script
  type="text/javascript"
  src="https://code.jquery.com/jquery-1.12.4.min.js"
></script>
<!-- iamport.payment.js -->
<script
  type="text/javascript"
  src="https://cdn.iamport.kr/js/iamport.payment-1.1.8.js"
></script>
```

#### 2. IMP 객체 초기화, IMP.request_pay 호출

```javascript
    <script>
      //[2] 객체 초기화, IMP.request_pay 호출
      IMP.init("가맹점 식별코드"); // - 아임포트 관리자 페이지에서 확인가능
      function requestPay(form) {
        // 작성한 form에서 결제정보 받아옴
        var now = new Date().getTime(); // 밀리초 단위로 표시한 현재시각=> 결제코드에 사용
        var uEmail = form.uEmail.value;
        var uName = form.uName.value;
        var uPhone = form.uPhone.value;
        var uAddress = form.uAddress.value;
        var price = $(".price").text();
        var pName = $(".pName").text();

        IMP.request_pay({ // param
          pg: "html5_inicis",
          pay_method: "card", // 결제방법
          merchant_uid: "ORD" + now,  // 거래ID
          name: pName + " 결제", // 거래내역에 표시되는 이름
          amount: price,
          buyer_email: uEmail,
          buyer_name: uName,
          buyer_tel: uPhone,
          buyer_addr: uAddress
        }, function (rsp) { // callback
          if (rsp.success) {
            // [3] 결제금액 위변조 검증 필요

            // 결제 성공 시: 결제 승인 또는 가상계좌 발급에 성공한 경우
            //DB에 결제정보 저장하고 사용자 화면 처리 필요
            var msg = '결제가 완료되었습니다.';
		        msg += '고유ID : ' + rsp.imp_uid;
		        msg += '상점 거래ID : ' + rsp.merchant_uid;
		        msg += '결제 금액 : ' + rsp.paid_amount;

          } else{
            // 결제 실패
             var msg = '결제에 실패하였습니다.';
		         msg += '에러내용 : ' + rsp.error_msg;
          }
          alert(msg);
          });
      }
    </script>
```

#### 3. 결제금액 위변조 여부 검증

아임포트 공식문서에는 결제 정보를 전달한 후, 결제금액의 위변조 여부 검증을 것을 권장하고 있다. 스크립트를 조작해 금액을 위변조하여 결제를 요청 할 수 있기 때문. rsp.success 이후 ajax를 통해 imp_uid를 전달하고, 결제 금액과 요청 금액을 확인하는 절차가 필요하다.

참고:

- [아임포트 기술문서](https://docs.iamport.kr/)
- [아임포트 github](https://github.com/iamport)

---
layout: post
title: "[javaScript] Ajax를 통한 댓글 처리"
---

자바스크립트만으로 댓글 등록/수정/삭제/목록 불러오기. 스크립트 코드만 삽입해주면 되므로 편리하다. 
```javascript
var bIdx = "${board.bIdx}";
// commentInsert 버튼에 대한 동작 처리
$("[name=commentsInsertBtn]").click(function () {
  var insertData = $("[name=commentsInsertForm]").serialize();
  insertComments(insertData);
});

//댓글 목록 불러오기
function commentsList() {
  $.ajax({
    url: "/board/commentsList.do",
    type: "get",
    data: { bIdx: bIdx },
    success: function (data) {
      var a = "";
      $.each(data, function (key, value) 
        a +=
          '<div class="areaComments" style="border-bottom:1px solid darkgray; margin-bottom: 15px;">';
        a += '<div class="infoComments' + value.mIdx + '">';
        a +=
          '<div class="comments-pic"> <img src="/resource/img/profile/user_default.png"> </div><span class="nickname"> ' +
          value.uNickname +
          "</span>";
        a +=
          '<a style="float:right" onclick="deleteComments(' +
          value.mIdx +
          ",'" +
          value.mIdx +
          "');\"> 삭제 </a> ";
        a +=
          '<a style="float:right" onclick="updateComments(' +
          value.mIdx +
          ",'" +
          value.cContent +
          "');\"> 수정&nbsp;</a></div>";
        a +=
          '<div class="commentsContent' +
          value.mIdx +
          '"> <p> <span class="regDate">' +
          value.cRegdate +
          "</span></p>";
        a +=
          '<div class="commentsContent' +
          value.mIdx +
          '"> <p> ' +
          value.cContent +
          "</p>";
        a += "</div></div></div></div>";
      });
      $(".commentsList").html(a);
    },
  });
}
```
댓글 입력, 수정 데이터 처리 후에 반드시 위의 댓글 목록 불러오기 기능을 같은 화면에서 실행시켜 사용자가 댓글 처리를 실시간으로 확인할 수 있도록 한다.

```javascript
//댓글 등록
function insertComments(insertData) {
  $.ajax({
    url: "/board/insertComments.do",
    type: "post",
    data: insertData,
    success: function (data) {
      if (data == 1) {
        // 등록 성공 시 댓글 리스트를 불러온다
        commentsList();
        // 댓글 입력창을 초기화한다
        document.getElementById("cContent").value='';
      }
    },
  });
}

//댓글 수정 - 입력칸
function updateComments(mIdx, cContent) {
  var a = "";

  a += '<div class="input-group">';
  a +=
    '<input type="text" class="form-control" name="cContent_' +
    mIdx +
    '" value="' +
    cContent +
    '"/>';
  a +=
    '<span class="input-group-btn"><button class="btn btn-default" type="button" onclick="UpdateCommentsProc(' +
    mIdx +
    ');">수정</button> </span>';
  a += "</div>";

  $(".commentsContent" + mIdx).html(a);
}

//댓글 수정하여 데이터처리
function UpdateCommentsProc(mIdx) {
  var updateComments = $("[name=cContent_" + mIdx + "]").val();

  $.ajax({
    url: "/board/updateComments.do",
    type: "post",
    data: { cContent: updateComments, mIdx: mIdx },
    success: function (data) {
      if (data == 1) commentsList(bIdx);
    },
  });
}

//댓글 삭제
function deleteComments(mIdx) {
  $.ajax({
    url: "/board/deleteComments.do?mIdx=" + mIdx,
    type: "post",
    success: function (data) {
      if (data == 1) commentsList(bIdx);
    },
  });
}
```

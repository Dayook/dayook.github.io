---
layout: post
title: "[javaScript] Ajax를 통한 댓글 처리"
---

####

```javascript
var bIdx = "${board.bIdx}";

$("[name=commentsInsertBtn]").click(function () {
  var insertData = $("[name=commentsInsertForm]").serialize();
  insertComments(insertData);
});

//댓글 목록
function commentsList() {
  $.ajax({
    url: "/board/commentsList.do",
    type: "get",
    data: { bIdx: bIdx },
    success: function (data) {
      var a = "";
      $.each(data, function (key, value) {
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

//댓글 등록
function insertComments(insertData) {
  $.ajax({
    url: "/board/insertComments.do",
    type: "post",
    data: insertData,
    success: function (data) {
      if (data == 1) {
        commentsList();
        $("[name=cContents]").val("");
      }
    },
  });
}

//댓글 수정
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

//댓글 수정
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

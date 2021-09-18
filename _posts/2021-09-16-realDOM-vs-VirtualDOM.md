---
layout: post
title: "[JavaScript] Arrow function(화살표 함수) 표현"
---
#### Arrow function 표현식
기존의 function을 간단하게 대체하지만 제한되어있으며 모든 상황에서 사용할 수는 없다


```javascript
// 기존의 익명 함수
function(a) {
  return a + 100
}

// 화살표 함수 (1)
(a) => {
  return a + 100;
}

// 화살표 함수 (2)
(a) => a + 100;

// 화살표 함수 (3)
a => a + 100;

```
괄호와 return을 항상 생략할 수 있는 것은 아님 코드가 길어질 경우 표시해줘야
```javascript
function (a, b){
  let chuck = 42;
  return a + b + chuck;
}

(a, b) => {
  let chuck = 42;
  return a + b + chuck;
}

```

함수에 이름을 붙일 경우 화살표 함수는 변수처럼 취급한다
```javascript
function bob (a) {
  return a + 100;
}

let bob = a => a + 100;

```

함수 자신의 this를 가지지 않으며, 함수가 정의된 스코프의 this를 가리킴
``` javascript
var obj = {
    num: 100
}
window.num = 2020; // yikes!

// Arrow Function
var add = (a, b, c) => this.num + a + b + c;

// call
console.log(add.call(obj, 1, 2, 3)) // result 2026

// apply
const arr = [1, 2, 3]
console.log(add.apply(obj, arr)) // result 2026

// bind
const bound = add.bind(obj)
console.log(bound(1, 2, 3)) // result 2026

```
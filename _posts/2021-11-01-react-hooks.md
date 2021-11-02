---
layout: post
title: "[React] React Hooks "
---

#### useState

가장 기본적인 Hook으로 상태 관리를 가능하게 함.

- 함수의 파라미터에는 상태의 기본값을 입력
- useState는 하나의 상태 값만 관리할 수 있으므로
- 여러 상태를 관리해야한다면 useState를 여러 번 쓸 것

#### useEffect

렌더링 직후 작업을 설정 클래스형 컴포넌트의 componentDidMout와 componentDidUpdate를 합친 형태

- 마운팅될 때만 실행하고 싶을 때: 함수의 두 번째 파라미터로 비어있는 배열을 넣어줄 것

```javaScript
useEffect(()=>{
  console.log('execute only when mounted');
}. []);
```

- 특정 값 업데이트 시에만 실행하고 싶을 때: 배열 안에 검사하고 싶은 값을 넣어줌

```javaScript
useEffect(()=>{
  console.log(name);
}. [name]);
```

- 뒷정리. 컴포넌트가 언마운트/업데이트 되기 직전에 수행하고 싶은 작업이 있다면 뒷정리(cleanup함수) 반환해주어야.


```javascript
useEffect(() => {
  console.log("effect");
  console.log(name);
  return () => {
    console.log("cleanup");
    console.log(name);
  };
});
```
### useReducer
- 리듀서: 현재 상태, 업데이트를 위해 필요한 정보를 담은 액션 값을 전달받아, 새로운 상태를 반환하는 함수.
- 새로운 상태를 만들 때 반드시 불변성 지켜줘야함
```javaScript
function reducer(state, action){
  return {...};
}
// 액션값의 형태
{ 
  type: 'INCREMENT' 
}

```



<!--
#### 이벤트핸들링
이벤트 : 사용자가 웹 브라우저에서 DOM 요소들과 상호작용하는 것
- 리액트에서 이벤트 이름은 카멜 표기법으로 작성
- ex) onClick, onChange, onKeyUp
- 이벤트에 자바스크립트 코드 X , 함수 형태의 값 전달


#### 라이프사이클
모든 리액트 컴포넌트에는 수명주기가 존재.
- 컴포넌트 업데이트 전후로 어떤 작업 처리해야 하는 경우, 불필요한 업데이트 방지해야 하는 경우
=> *라이프사이클 메서드* 사용, 클래스형 컴포넌트에서 사용. 함수형에서는 Hooks로 대신


- Mount
  - DOM이 생성되고 웹브라우저에 나타나는 것
- Update
  - props가 바뀔 때
  - state가 바뀔 때
  - 부모 컴포넌트가 리렌더링
  - this.forceUpdate로 강제로 렌더링

- Unmount
  - 컴포넌트를 DOM에서 제거

#### 라이프사이클 메서드
- `render() {...}`
  - lifecycle method 중 유일한 필수 메서드
  - this.props, this.state에 접근 가능
  - react 요소 반환
  - 아무것도 반환하고 싶지 않다면 null or false 반환
-  -->

출처: 『리액트를 다루는 기술』, 길벗출판사

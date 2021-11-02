---
layout: post
title: "[React] state "
---

state: 컴포넌트 내부에서 바뀔 수 있는 값
props: 부모 컴포넌트가 설정하는 값. 해당 props는 읽기 전용


- 클래스형 컴포넌트의 state

```javaScript
Class Counter extends Components {
  // state 설정법 (1)
  // constructor 메소드 작성
  // constructor(props){
  //   super(props);
  //   // state의 초기값 설정
  //   this.state = {
  //     number: 0,
  //     fixedNumber:0
  //   }
  // state 설정법 (2)
  state = {
    number :0;,
// - state 객체 안에는 여러 값이 있을 수 있음
    fixedNumber:0
    };
  }

  render(){
    const {number} = this.state;
    return (
      <div> <h1>{number}</h1>
      <button // onClick을 통해 호출될 함수 지정합니다
      onClick={()=>{
        this.setState({number:number + 1,
        // 값 업데이트 뒤 특정 작업 실행하고 싶을 때
        () => {
          console.log('방금 setState가 호출되었습니다.');
         
        })
      }}>+1
    </button></div>
    );}
  }

```

```javaScript
<button onClick={() => {
  this.setState(prevState => {
    return {
      number: prevState.number + 1
    };
  });

  this.setState(prevState => ({
    number: prevState.number + 1
  }))
}}

```

state 사용할 때 주의사항
```javaScript
// 잘못된 코드
this.state.number = this.state.number + 1;
this.state.array = this.array.push(2);

// 올바른 코드 
const object = {a:1, b:2, c:3};
const nextObject = {...object, b:2};

const array = [
  {id: 1, value:true},
  {id: 2, value:true},
  {id: 3, value:false},
];
let nextArray = array.concat({id:4}); // 새항목 추가
nextArray.filter(item=>item.id !==2);
nextArray.map(item=>(item.id === 1{...item, value:false} : item));



```
출처: 『리액트를 다루는 기술』, 길벗출판사

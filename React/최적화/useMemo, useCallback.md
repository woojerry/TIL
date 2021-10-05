### 최적화 
> React에서 컴포넌트를 실행하여 React.element를 만들어내는 과정인 ```렌더링```은 컴포넌트 내 state가 변경되었을 때나 props값이 바뀌었을 때이다. 


### React.memo
> React는 컴포넌트에 있는 props나 state가 변경되면 그것을 사용하는 HTML 전부 재렌더링된다. 그럴 때, props가 변경되지 않은 컴포넌트는 재렌더링 하지 않도록 하게 하는 것
```import {memo} from 'react';```

- 원래 코드
```jsx
function Child2(){
  useEffect( ()=>{ console.log('렌더링됨2') } );
  return <div>2222</div>
}
```
- memo 적용 코드
```jsx
let Child2 = memo(function() { // memo로 감싸진 컴포넌트는 재렌더링 되지 않는다.
  useEffect( ()=>{ console.log('렌더링됨2') } );
  return <div>2222</div>
})  
```

- 하지만 props가 매우 방대하고 큰 경우엔 오히려 손해일 수 있다. memo로 감싼 컴포넌트는 헛되게 재렌더링을 안시키려고 기존 props와 바뀐 props를 비교하는 연산이 추가로 진행된다. 그러므로props가 크고 복잡하면 이거 자체로도 부담이 될 수도 있다.

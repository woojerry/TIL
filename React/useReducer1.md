### Reducer
> 현재 상태와 액션 객체를 파라미터로 받아와서 새로운 상태를 반환해주는 함수
```jsx
function reducer(state, action) {
  // 새로운 상태를 만드는 로직
  // const nextState = ...
  return nextState;
}
```
## useReducer
> 상태를 관리할 때 ```useState```외에 사용하는 방법으로 컴포넌트에서 관리하는 값이 여러개가 되어서 상태의 구조가 복잡해졌을 때 쓰면 유용한 Hook
```jsx
const [state, dispatch] = useReducer(reducer, initialState);
// state는 컴포넌트에서 사용할 수 있는 상태
// dispatch는 action을 발생시키는 함수
// reducer는 reducer함수
// initialState는 초기 상태
```

- 예제 
```jsx  
import React, { useReducer } from 'react';

function reducer(state, action) {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1;
    case 'DECREMENT':
      return state - 1;
    default:
      return state;
  }
}

function Counter() {
  const [number, dispatch] = useReducer(reducer, 0);

  const onIncrease = () => {
    dispatch({ type: 'INCREMENT' });
  };

  const onDecrease = () => {
    dispatch({ type: 'DECREMENT' });
  };

  return (
    <div>
      <h1>{number}</h1>
      <button onClick={onIncrease}>+1</button>
      <button onClick={onDecrease}>-1</button>
    </div>
  );
}

export default Counter;
```

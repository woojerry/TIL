### Reducer
> 현재 상태와 액션 객체를 파라미터로 받아와서 새로운 상태를 반환해주는 함수
```jsx
function reducer(state, action) { // state는 상태, action객체를 통해서 state에 변화를 준다.
  // 새로운 상태를 만드는 로직
  // const nextState = ...
  return nextState;
}
```
## useReducer
> 상태를 업데이트하고 관리할 때 ```useState```를 사용하는 것과 같은 방법의 컴포넌트의 상태 업데이트 로직을 컴포넌트에서 분리시킬 수 있는 Hook
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
### useState vs useReducer
> 컴포넌트에서 관리하는 값이 딱 하나고, 그 값이 단순한 숫자, 문자열 또는 boolean 값이라면 확실히 useState 로 관리하는게 편리
- 컴포넌트에서 관리하는 값이 여러개가 되어서 상태의 구조가 복잡해진다면 useReducer로 관리하는 것이 편리. 결정은 편한대로 본인이 하면 된다.


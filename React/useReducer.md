## useReducer
> 상태를 업데이트하고 관리할 때 ```useState```를 사용하는 것과 같은 방법에 컴포넌트의 상태 업데이트 로직을 컴포넌트에서 분리시킬 수 있는 Hook

### Reducer
> reducer 는 현재 상태와 액션 객체를 파라미터로 받아와서 새로운 상태를 반환해주는 함수
```jsx
function reducer(state, action) {
  // 새로운 상태를 만드는 로직
  // const nextState = ...
  return nextState;
}
```
- useReducer 사용법: ```const [state, dispatch] = useReducer(reducer, initialState);```

### useReducer vs useState
> 컴포넌트에서 관리하는 값이 딱 하나고, 그 값이 단순한 숫자, 문자열 또는 boolean 값이라면 확실히 useState 로 관리하는게 편리
- 컴포넌트에서 관리하는 값이 여러개가 되어서 상태의 구조가 복잡해진다면 useReducer로 관리하는 것이 편리. 결정은 편한대로 본인이 하면 된다.


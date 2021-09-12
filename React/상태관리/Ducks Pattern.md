## Ducks Pattern
> 평소 redux를 활용해 상태관리를 진행할 때 action, reducer, saga 등을 각각의 폴더에 구분해 관리하면 수정 시 여러 개의 파일을 수정해야하는 번거로움이 생길 수 있다. 
> 이러한 불편함을 개선하고자 나온 것이 Ducks 패턴
- 구조중심이 아니라 **기능중심으로 파일을 나눈다.**
- 즉, action type, action생성자 함수, saga, reducer를 **하나의 파일**에서 관리하는 것.
- Ducks 패턴에서 각각의 액션/액션함수/리듀서를 모아둔 것을 **module**이라 부른다.

1. **reducer**는 **export default로 내보낸다.**
2. action 함수는 export로 내보낸다.
3. **액션타입을 정의할 때 reducer/ACTION_TYPE형태로** 적어줘야 한다. 이렇게 접두사를 붙여줘 서로 다른 리듀서에서 **액션이름이 중첩되는 것을 방지.**

```js
// widgets.js

// Actions
const LOAD   = 'my-app/widgets/LOAD';
const CREATE = 'my-app/widgets/CREATE';
const UPDATE = 'my-app/widgets/UPDATE';
const REMOVE = 'my-app/widgets/REMOVE';

// Reducer
export default function reducer(state = {}, action = {}) {
  switch (action.type) {
    // do reducer stuff
    default: return state;
  }
}

// Action Creators
export function loadWidgets() {
  return { type: LOAD };
}

export function createWidget(widget) {
  return { type: CREATE, widget };
}

export function updateWidget(widget) {
  return { type: UPDATE, widget };
}

export function removeWidget(widget) {
  return { type: REMOVE, widget };
}

// side effects, only as applicable
// e.g. thunks, epics, etc
export function getWidget () {
  return dispatch => get('/widget').then(widget => dispatch(updateWidget(widget)))
}
```

참고 https://github.com/erikras/ducks-modular-redux

![redux](https://user-images.githubusercontent.com/50645183/105139663-e1884600-5b39-11eb-81f1-e041e6aebe2b.PNG)


## Keywords

### 액션(Action)
> 상태에 어떠한 변화가 필요하게 될 땐, 우리는 액션이란 것을 발생시킨다.
```jsx
{
  type: "ADD_TODO",
  data: {
    id: 0,
    text: "리덕스 배우기"
  }
}
```

### 액션 생성함수
> 파라미터를 받아와 액션 객체 형태로 만들어주는, 액션을 만드는 함수
- 리덕스를 사용 할 때 액션 생성함수를 사용하는것이 필수적이진 않다. 액션을 발생 시킬 때마다 직접 액션 객체를 작성할수도 있다.
```jsx
export function addTodo(data) {
  return {
    type: "ADD_TODO",
    data
  };
}

// 화살표 함수로도 만들 수 있다.
export const changeInput = text => ({ 
  type: "CHANGE_INPUT",
  text
});
```


### 리듀서(Reducer)
> 변화를 일으키는 함수. 두가지의 파라미터를 받아온다.
```jsx
function reducer(state, action) {
  // 상태 업데이트 로직
  return alteredState;
}
```
```jsx
function counter(state, action) {
  switch (action.type) {
    case 'INCREASE':
      return state + 1;
    case 'DECREASE':
      return state - 1;
    default:
      return state;
  }
}
```
### 스토어 (Store)
> 리덕스에서는 한 애플리케이션당 하나의 스토어를 만들게 된다. 스토어 안에는, 현재의 앱 상태와, 리듀서가 들어가있고, 추가적으로 몇가지 내장 함수들이 있다.

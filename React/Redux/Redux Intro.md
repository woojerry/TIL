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

### 디스패치(dispatch)
>  액션을 발생 시키는 것. 파라미터로 action을 전달
```jsx
 const dispatch = useDispatch();
 const onCreate = (text) => dispatch(addTodo(text)); // addTodo(text)가 action
```
### 구독(subscribe)
> 원래는 ```subscrbie```함수를 통해, 예전에는 ```connect```를 사용했으나 요즘은 ```useSelector```를 활용해 리덕스의 상태값을 조회하는 것
```jsx
const { number, diff } = useSelector(state => ({ // 이런식으로 하면 상태가 바뀌지 않아도 전체가 리랜더링
    number: state.counter.number,
    diff: state.counter.diff
  }));
```
```jsx 
const number = useSelector((state) => state.counter.number); // useSelector를 여러번 사용해 바뀐 상태의 부분만 리랜더링
const diff = useSelector((state) => state.counter.diff);
```

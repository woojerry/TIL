## Context API
> 모든 하위 컴포넌트들이 props 없이도 state를 사용가능하게 만들어주는 문법
- 간단한 데이터 전송은 props가 더 편하다. 컴포넌트가 여러개 중첩돼있는 경우에 사용
```
1. React.createContext()로 같은 변수값을 공유할 범위 생성
2. 값 공유를 원하는 HTML을 <범위.Provider>로 감싸고 value={공유원하는값}
3. useContext훅을 사용해 공유된 값 사용하기
   - useContext(범위이름)
```
```jsx
import React, { useState, useContext } from 'react';

let 재고context = React.createContext(); // 범위 생성


function App() {
 let [재고, 재고변경] = useState([10,11,12]);
  return(
    <재고context.Provider value={재고}> // 범위.Provider로 감싸기 + value = 공유 원하는 값
        <div className="row">{
          shoes.map((a,i)=> {
            return <Card shoes = {shoes[i]} i ={i} key={i}/>
          })
        }

      </div>
        </재고context.Provider>
        );
        }
        
 function Card() {

    let 재고 = useContext(재고context); // useContext훅 사용
    return (
        <div className="col-md4">
          <img src={'https://codingapple1.github.io/shop/shoes' + (props.i+1) + '.jpg'} />
          <h4>{props.shoes.title}</h4>
          <p>{props.shoes.content} & {props.shoes.price} </p>
          {재고[0]}
        </div>

    )
  }
```
- 다른파일에 공유하고 싶을 때 : 똑같이 범위로 감싸고, 범위 export 하고 사용하고 싶은 파일에서 import해주기
- 예) App.js에서 Detail.js로 -> App.js에서 export하고 Detail.js에서 import해서 사용
```jsx
export let 재고context = React.createContext(); // export 해주기ㅆ

<Route path="/detail/:id">
 <재고context.Provider value={재고}> // 범위로 감싸기 + value
  <Detail shoes={shoes} 재고 ={재고} 재고변경={재고변경}/>
 </재고context.Provider>
</Route>
```      

```jsx
import {재고context} from './App.js';
```

- Provider value안에 여러값을 객체형식으로도 넣어서 사용가능하다.
- 하지만 이 방식 이Context를 공유하는 컴포넌트들이 재랜더링이 일어날 수 있기에 좋은 방법은 아니다.
```jsx
// Provider 부분
      <todoContext.Provider
        value={{
          todos: todos,
          onCreate: createHandler,
          onRemove: removeHandler,
          onToggle: toggleHandler,
          nextId: nextId,
        }}
      >
        <GlobalStyle />
        <TodoTemplate>
          <TodoHead />
          <TodoList />
          <TodoCreate />
        </TodoTemplate>
      </todoContext.Provider>
```        
```jsx
// 사용하는 부분
import { todoContext } from "../App";
...
const TodoList = () => {
const { todos, onRemove, onToggle } = useContext(todoContext);
...
}
```

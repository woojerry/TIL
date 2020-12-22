## Props
>  props 는 properties 의 줄임말로, 어떠한 값을 컴포넌트에게 전달해줘야 할 때 사용한다.
- props로 전송해 자식 Component에게 부모 Component가 가진 state를 사용하게 해준다.

 1. ```<자식Component 작명 = {state명} />```
 2. 자식 Component 선언하는 function안에 파라미터 입력 후 사용
 3. 요즘은 비구조화 할당?? 으로 많이 
 
```jsx
  import React from 'react'; // App.js
import Hello from './Hello';

function App() {
  return (
    <Hello name="react" color="red"/>
  );
}

export default App;
}
```
```jsx
import React from 'react'; // Hello.js

function Hello(props) {
  return <div style={{ color: props.color }}>안녕하세요 {props.name}</div>
}

export default Hello;
```
```jsx
import React from 'react'; // Hello.js // 비구조화할당

function Hello({ color, name }) {
  return <div style={{ color }}>안녕하세요 {name}</div>
}

export default Hello;
```

### defaultProps

> 컴포넌트에 props 를 지정하지 않았을 때 기본적으로 사용 할 값을 설정하고 싶을 때 사용

```jsx
import React from "react";

function Hello({ color, name }) {
  // App.js
  return <div style={{ color }}>안녕하세요 {name}</div>;
}

Hello.defaultProps = {
  name: "이름없음",
};

export default Hello;
```

```jsx
import React from "react"; // Hello.js

function Hello(props) {
  return <div>안녕하세요 {props.name}</div>;
}

export default Hello;
```

![image](https://user-images.githubusercontent.com/50645183/102776120-8562c280-43d1-11eb-8064-49c5260a052c.png)

### props.children
> 값을 사용하는 곳에서 값을 정하는 것

```jsx
import React from "react"; // App.js
import Hello from "./Hello";
import Wrapper from "./Wrapper";

function App() {
  return (
    <Wrapper>
      <Hello name="react" color="red" />
      <Hello color="pink" />
    </Wrapper>
  );
}

export default App;
```
```jsx
import React from 'react'; // Wrapper.js
                           // 이 경우엔 내부의 내용이 보여지지 않는다.
function Wrapper() {
  const style = {
    border: '2px solid black',
    padding: '16px',
  };
  return (
    <div style={style}>

    </div>
  )
}

export default Wrapper;
```

```jsx
import React from "react"; // Wrapper.js

function Wrapper({ children }) {
  const style = {
    border: "2px solid black",
    padding: "16px",
  };
  return <div style={style}>{children}</div>;
}

export default Wrapper;
```

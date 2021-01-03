## useRef
> JS에서 특정 DOM을 선택해야 하는 상황이 React에서도 발생할 때 사용
- React에서는 ```ref```라는 것을 사용
- 함수형 컴포넌트에서 ```ref```를 사용할 때는 ```useRef``` Hook 사용한다

```jsx
import React, { useState, useRef } from 'react'; // InputTest.js
                                                // 초기화 시 input 태그에 focus 잡히는 기능 

function InputTest() {
  const [text, setText] = useState('');
  const nameInput = useRef(); // Ref 객체 생성
  
  const onChange = e => {
    setText(e.target.value)
  };  
  
  const onRest = () => {
    setText('');
    nameInput.current.focus(); // Ref 객체의 current 값은 선택하고자 하는 DOM을 가리킨다.
                               // DOM API focus()호출해 포커싱한다.
  };  
  
  return (
    <div>
      <input
        name="name"
        onChange={onChange} 
        value={text}
        ref={nameInput}            // 선택하고 싶은 DOM에 속성으로 ref값을 설정
        />
        
        <button onClick={onReset}초기화</button>
        <div>
          <b>내용: </b>
          {text}
        </div>
       </div>
      );
     }
     
     export default InputTest;
```

- useRef로 Component 안의 변수 관리하기
- useRef Hook의 다른 기능으로 컴포넌트 안에서 조회 및 수정 가능한 변수를 관리할 수 있다.
- useRef로 변수를 관리해 그 변수가 업데이트 된다고 그 컴포넌트가 재렌더링이 되지 않으므로 재렌더링 할 필요가 없을 때 useRef로 관리하는게 효율적이다.
- 주로 id, key값을 관리할 때 사용한다.
```jsx
import React, { useRef } from 'react'; // App.js
import UserList from './userList';

function App() {
  const users = [
    {
      id: 1,
      username: 'woo',
      email: 'woojerry@naver.com'
    },
    {
      id: 2,
      username: 'pop',
      email: 'pop@gmail.com'
    }
  ];

  const nextId = useRef(3); // 배열의 고유값 변수로 nextID설정 
                            // useRef() 파라미터로 다음 id가 될 숫자 4를 넣어준다.
  const onCreate = () => {
    // 배열에 새로운 항목 추가하는 로직

    nextId.current += 1;  //.. 파라미터 값을 넣어주면 해당 값이 변수의 current값이 된다.
                          // .current값은 우리가 원하는 DOM을 가르키게 한다.
  };
  return <UserList users={users} />;
}
export default App;
```

참고 <https://xiubindev.tistory.com/98>

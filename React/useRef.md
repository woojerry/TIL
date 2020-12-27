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
    nameInput.current.focus(); //Ref 객체의 current 값은 선택하고자 하는 DOM을 가리킨다.
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

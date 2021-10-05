## 최적화 
> React에서 컴포넌트를 실행하여 React.element를 만들어내는 과정인 ```렌더링```은 컴포넌트 내 state가 변경되었을 때나 props값이 바뀌었을 때이다. React의 shallow copy를 이용한 비교 알고리즘을 통해 재렌더링이 일어날 때 함수나, 변수 등에 대해서 함수형 컴포넌트에서는 ```useMemo```,```useCallback```와 같은 hook 등을 통해 불필요한 렌더링을 없애 최적화를 할 수 있다.
- 크게 보면 useMemo는 변수, useCallback은 함수를 기억하게 해 최적화할 때 사용한다.
### useMemo
> 함수의 return 값을 기억해 의존하는 값이 변경될 때에만 연산하게 해준다.
- 첫번째 파라미터에는 어떻게 연산할지 정의하는 함수를 넣어주면 되고 두번째 파라미터에는 deps 배열을 넣어주면 된다.
```jsx
function countActiveUsers(users) {
  console.log('활성 사용자 수를 세는중...');
  return users.filter(user => user.active).length;
}

const count = useMemo(() => countActiveUsers(users), [users]);
```

### useCallback
> 함수 자체를 기억해 컴포넌트가 리렌더링 될 때 마다 새로 만들어지는 것을 방지해준다.
```jsx
 const onRemove = useCallback(
    id => {
      // user.id 가 파라미터로 일치하지 않는 원소만 추출해서 새로운 배열을 만듬
      // = user.id 가 id 인 것을 제거함
      setUsers(users.filter(user => user.id !== id));
    },
    [users]
  );
```  

### React.memo
> useMemo의 HOC(Higher Order Component)버전
```import {memo} from 'react';```

- 원래 코드
```jsx
function Child2(){
  useEffect( ()=>{ console.log('렌더링됨2') } );
  return <div>2222</div>
}
```
- memo 적용 코드
```jsx
let Child2 = memo(function() { // memo로 감싸진 컴포넌트는 재렌더링 되지 않는다.
  useEffect( ()=>{ console.log('렌더링됨2') } );
  return <div>2222</div>
})  
```

- 하지만 props가 매우 방대하고 큰 경우엔 오히려 손해일 수 있다. memo로 감싼 컴포넌트는 헛되게 재렌더링을 안시키려고 기존 props와 바뀐 props를 비교하는 연산이 추가로 진행된다. 그러므로props가 크고 복잡하면 이거 자체로도 부담이 될 수도 있다.

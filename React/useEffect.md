## Lifecycle Hook
- Component는 생성/삭제/재렌더링(업데이트)의 Lifecycle을 가진다.
- 이 중간에 중간중간 Hook을 걸 수 있다.
- 예를 들어 <Title> Component 등장 전/ 사라지기 전/ 업데이트 후 에 Hook을 활용해 어떤 동작 지시 가능

- 가장 유용한 Hook ```componentDidMount()``` ```componentWillUnmount()```
```
class Detail2 extends React.Component {
  componentDidMount(){
    //Detail2 컴포넌트가 Mount 되고나서 실행할 코드
  }
  componentWillUnmount(){
    //Detail2 컴포넌트가 Unmount 되기 전에 실행할 코드
  }
}
```

## useEffect Hook
- ```import {useEffect} from 'react';```로 import해 사용
- useEffect를 여러개 사용할 땐 적은 순서대로 순차적으로 실행된다.
- 기능1 : Component가 mount끝났을 때(첫 등장 후 로딩 끝난 후에)/ update 후(재렌더링 후)
    - function 컴포넌트 안 return()전에 작성
    ```jsx
    function Detail(props){

        useEffect(()=>{
            // 실행할 코드
        });

        return(
          <HTML/>
          )
    }      
    ```
    
- 기능2 : Component가 unmount될 때 (사라질 때)
    - useEffect()안 return에 함수 넣어 사용
    ```jsx
    function Detail(){

      useEffect(()=>{

        return function [함수명](){ 실행할 코드 } 
      });
    ```  
- update될 때마다 useEffect()가 실행될 경우
    - useEffect()함수 끝부분에 대괄호[]를 집어 넣고 state를 넣어준다. 
    - 만약 []안에 아무것도 안넣으면 조건을 넣지 않은 것이므로 Component가 로드될 때 한번만 실행되는 트릭 사용 가능
```jsx
useEffect(()=>{
   let 타이머 = setTimeout(()=>{ alert변경(false) }, 2000);
}, [alert]); // alert state가 변경될 때만 실행된다.
```

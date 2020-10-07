##Class
  > component만드는 기본문법 (**예전 React 문법**) -> 매우 불편  
  - class : 변수/함수 보관하는 곳
  - constructor : class의 변수/초기값 저장
  - state는 constructor 안에 작성
```jsx
class Profile extends React.Component { // extends : React.Component의 성질을 물려받는다.
  constructor(){ 
    super();
    this.state = { name : 'Kim', age : 30 } 
  }
  
  changeName = () => { // arrow function 으로 만들면 this값 관련한 오류나지 않는다.
    this.setState( { name : 'Park'}
  }
  
  render(){
    return (
        <div>
          <h3>프로필입니다.</h3>
          <p>저는 {this.state.name } 입니다. </p> // state 꺼내쓰려면 this.state.state명
          <button onClick={ ()=>{ this.changeName} }></button> // state변경함수 대신 setState(변경할state)
        </div> 
      )
    }
 }
 
 <Profile /> // state사용
 ```

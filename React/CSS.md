### Boostrap
  - React ver. 설치 방법 : React Boostrap 이용
      - npm install react-bootstrap bootstrap
  - CSS link 태그```<link [내용]/>``` index.html에 복사
  
### Component 가져오기  
  - React-Bootstrap 사이트에서 원하는 Component의 코드 APP component에 붙여넣기 
  - 사용할 **Component를 import**해와야 사용 가능
  ```jsx
  // React-Component import 방법
  import Button from 'react-bootstrap/Button';

  // or less ideally
  import { Button } from 'react-bootstrap';
  ```
### CSS  
- React에서 프로젝트 폴더 중 **public**폴더에 이미지를 보관 (발행해도 파일이 그대로 남아있음)
    - src 안에 있는 파일은 리액트 앱을 발행했을 때 압축될 수 있다.
    
- 배경 그림 넣기 
     - App.css 파일에서 특정 클래스 안에 ```background-image : url(/[이미지파일명]);```
     - public 폴더안에 있는 이미지이므로 ```/```로 경로를 나타내도 public 폴더 내부에 있는 이미지들을 갖다쓸 수 있다.

### import/ export 문법
> 파일을 쪼갤 때 활용

- 내보내기 ```export default [변수명]```
  - export default는 **파일 하나당 한번만** 사용 가능
  - 내보낼 변수가 많을 경우에는 ```export{ [변수1], [변수2]}```

- 가져오기 ```import[변수명] from[경로]```
  - export의 변수명과 import의 변수명은 동일해야한다.
  - 여러개 가져올 때도 ```import{ [변수1], [변수2]} from[경로]```

```jsx
var name = 'Kim';
export default name // 다른 파일에서 변수 사용 가능
```
```jsx
import name from './data.js';  // ./는 현재 경로
```

- 자료가 길 때
```jsx
export default [
    {
      id : 0,
      title : "White and Black",
      content : "Born in France",
      price : 120000
    },
    
    ...
```
```jsx
import React, {useState} from 'react';
import Data from '.data.js'; // .js 생략가능

function App() {
  let [shoes, shoes변경] = useState(Data);
  
  return(
    <h4>{ shoes[0].title}</h4> // "White and Black"  // 데이터 바인딩 
    <p>{ shoes[0].content } </p> // "Born in France",
    ) }
```
```jsx
 <div className="container">
        <div className="row">{
          shoes.map((a,i)=> {
            return <Card shoes = {shoes[i]} i ={i} key={i}/>
          })
        }
        </div>
      </div>


function Card(props) {
  return (
      <div className="col-md4"> // scr="" 데이터 바인딩 하려면 src = {}
        <img src={'https://codingapple1.github.io/shop/shoes' + (props.i + 1)+ +'.jpg'} />
        <h4>{props.shoes.title}</h4>
        <p>{props.shoes.content} & {props.shoes.price} </p>

      </div>

  )
}

## Routing
> 페이지 나누기
- react는 view만 담당하는 라이브러리이므로 라우팅을 담당하는 react-router을 따로 설치해주어야 한다. 그리고 나중에 model과 controller를 담당하는 패키지를 또 설치해야 한다.
- react-router-dom 라이브러리 사용
- terminal에서 ```yarn add react-router-dom``` 또는 ```npm install react-router-dom```으로 설치
- setting -> index.js에서 ```import { BrowserRouter } from 'react-router-dom'; ```하고  ```<BrowserRouter>```태그로 ```<App/>```감싸기

- BrowserRouter VS HashRouter
    - 전자는 #가 없고 후자는 있음.
    - HashRouter는 라우팅을 안전하게 할 수 있게 도와준다.
    - BrowserRouter는 라우팅을 리액트가 아니라 서버에게 요청할 수도 있어서 위험하다.  

- App.js에서 ```<Route>```태그 안에 원하는 HTML넣어준다. 
```jsx
<Route path="/detail">
        <div>HTML about detail</div>
</Route>
```
- React Router는 페이지마다 다른 HTML파일이 아닌 HTML내부의 내용을 갈아치워 다른페이지처럼 보여주는 것이다. (index.html만 있음)
- React Router는 매칭 되는 것을 다 보여준다. 예를 들어 "/detail"로 시작하면 메인페이지인 "/"까지 같이 보인다.
    - 이럴 경우에는 ```<Route exact path="/">```처럼 **exact**를 넣어준다.    
    
- Component가 너무 길어 다른 파일에 저장해두고 import 해올 때 (Component파일명은 대문자로 시작)
    - 그리고 상단에 ```import React```는 필수 !
- 중요한데이터들은 무조건 App 컴포넌트에 보관
    - 상위컴포넌트가 중요 데이터를 다 가지고 있고, 하위컴포넌트가 data를 props로 받아 쓰는 것이 좋다.

### Link
- ```<Link>```태그 사용법
    - ```<Nav.Link> <Link to="/detail">Detail</Link> </Nav.Link>```처럼 원하는 곳에 Link태그로 감싸고 to 속성을 이용해 경로 지정

- 뒤로가기 구현
    - ```import { useHistory } from 'react-router-dom';```후 useHistoy() 메소드 사용. 예)```let history = useHistory();```
    - ```goback()```,```push()``` 메소드 활용
    ```jsx
             <button className="btn btn-danger" onClick={()=>{
                 history.goBack();
              }}>뒤로가기</button> 
    ```    
      
### Switch    
> 여러개의 ```<Route>```들 중 하나만 보여주고 싶을 때 사용
    - ```<Route>```들을 ```<Switch>```태그로 감싸면 된다.
    
### URL Parameter
- ```:```사용, :뒤에 마음대로 작명, 여러개 사용가능
```jsx
<Route path="/detail/:id">
          <Detail shoes={shoes}/>
        </Route>
    </div>
```    
- 데이터 바인딩 시 ```useParams()```훅 사용하기
    - ```import { useParams } from 'react-router-dom';```

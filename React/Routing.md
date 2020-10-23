## Routing
> 페이지 나누기
> react는 view만 담당하는 라이브러리이다. 그래서 라우팅을 담당하는 react-router을 따로 설치해주어야 한다. 그리고 나중에 model과 controller를 담당하는 패키지를 또 설치해야 한다.
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
        <div>디테일페이지</div>
</Route>
```
- React Router는 페이지마다 다른 HTML파일이 아닌 HTML내부의 내용을 갈아치워 다른페이지처럼 보여주는 것이다. (index.html만 있음)
- React Router는 매칭 되는 것을 다 보여준다. 예를 들어 "/detail"로 시작하면 메인페이지인 "/"까지 같이 보인다.
    - 이럴 경우에는 ```<Route exact path="/">```처럼 exact를 넣어준다.    

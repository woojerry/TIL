## Express
> Server인 Express 기본 세팅 
- server.js에 다음 코드 입력
```js
const express = require("express");
const path = require("path");
const app = express();

const http = require("http").createServer(app);
http.listen(8080, function () {
  console.log("listening on 8080");
});
```
```js
// another ver.
const express = require("express"); // express 가져오기
const app = express(); // express앱 만들기
const port = 5000; // port번호

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.listen(port, () => {
  console.log(`Example app listening at http://localhost:${port}`);
});
```
- 그 다음 터미널에 ```npm init```
- ```npm install express --save```
- ```node server.js```로 서버 작동

```js
// HTML파일 보내는법
app.get("/", (req, res) => {
  // req는 요청 , res는 응답
  res.sendFile(path.join(__dirname, "public/index.html"));
});
```
```js
// 미들웨어로 HTML,CSS, img, js 파일들 담긴 곳 명시
app.use(express.static(path.join(__dirname, "public")));
```
<hr>

## Express + React
> React를 만들어 놨으면 React는 HTML파일 하나로 갈아끼우는 원페이지 앱이므로 index.html만 보내주게 세팅하면 된다 ?
- 같은 폴더 내에서 터미널을 하다 더 켜서 ```npx create-react-app [프로젝트 명]``` 을 입력하면 React프로젝트 생성 
- React Project가 완성됐으면 터미널의 react project 디렉토리에서 ```npm run build```를 하면 최종 HTML파일 생성

```js
app.use(express.static(path.join(__dirname, "react-project/bulild ")));
```
```js
app.get("/", (req, res) => {
    res.sendFile(path.join(__dirname, "public/main.html"));
});
```
### Router를 썼을 경우 ?
> React프로젝트 내에서 Routing 가능 -> Server의 역할 축소 -> 서버는 DB입출력으로 
- 하지만 직접 ```http://localhost:3000/```뒤에 예를들어 detail을 입력해 바로 들어가려고 하면 안된다.
```js
// 이렇게 *을 사용하면 해결된다. /detail로 들어가도 실제로 /deatil페이지가 라우팅된다.
app.get("*", (req, res) => {
    res.sendFile(path.join(__dirname, "public/main.html"));
});
```
### Express + React 개발 패턴
1. 예를 들어 /list로 접속시 list 내용의 HTML을 보여주려 할 때, list의 내용물들은 DB에 있을 것이다.
2. list페이지가 load되기 전에 useEffect등에서 Server에 Ajax요청을 한다. 
3. Server에서는 React Ajax요청하는 코드도 작성해줘야하고 그럼 Server에서는 DB에 있던 list 데이터를 보내준다.

### ```'/'```로 접속했을 때 react가 아닌 메인페이지 보여주는 법 
```js
// 미들웨어에서 설정
app.use( '/', express.static(path.join(__dirname, "public")));
app.use( 'react', express.static( path.join(__dirname, 'react-project-build')))

app.get("/", (req, res) => {
  // req는 요청 , res는 응답
  res.sendFile(path.join(__dirname, "main.html")); // 메인페이지
});
app.get("/react", (req, res) => {
    // req는 요청 , res는 응답
    res.sendFile(path.join(__dirname, "react-project/build/index.html")); // 리액트 페이지
  });
```
- 추가로 React프로젝트의 ```package.json```에 가서 ```"homparge" : "/react",```도 넣어 줘야한다.

### 매번 build를 해야하는가에 대해서는 proxy를 활용

## CORS 이슈
> CORS(Cross-Origin Resource Sharing)
- 예륻들어 서버가 5000번 포트를 갖고 있고, 클라이언트가 3000번 포트를 갖고 있을 때, 서로 Request를 보낼 때 보안을 위해서 CORS정책에 의해 막히게 된다.
- 해결하는 방법
```jsx
1. 개발자 도구 활용 - 제한적 ,,
2. 프론트엔드 부분만 수정할 수 있는 상황 -> jsonp - 제한적 ,,
3. 백,프론트 모두 컨트롤할 수 있을 때 -> request 보낼 때 수정 
4. Proxy 활용
```
### Proxy 활용
https://create-react-app.dev/docs/proxying-api-requests-in-development/
1. ```npm install http-proxy-middleware --save``` or ```yarn add http-proxy-middleware```
2. ```src/setupProxy.js``` 파일 생성
3. 코드 넣기
```jsx
const { createProxyMiddleware } = require('http-proxy-middleware');

module.exports = function(app) {
  app.use(
    '/api',
    createProxyMiddleware({
      target: 'http://localhost:5000', // 프론트엔드 3000번을 줄 때, target을 5000으로 주겠다.
      changeOrigin: true,
    })
  );
};
```

## nodemon
> 변화가 됐을 때 서버 재실행 자동화 해주는 library
nodemon설치: terminal에서 ``` npm install nodemon --save-dev``` or ```yarn add nodemon``` (dev를 통해서 local에서 할 때만 사용하겠다 라는 표시 - 빼줘도 된다) 
- global 설치: ``` npm install -g nodemon``` or ```yarn add global nodemon```
- nodemon 실행: ```nodemon server.js```
- ```package.json``` 파일에서 ```"scripts"```부분에 ```"backend": "nodemon server.js"```를 해주면 ```npm run backend```로 실행 가능
(만약 보안 오류 뜰 때: 1. powershell 관리자 권한으로 실행해 ```executionpolicy```를 입력했을 때 ```Restricted```로 나오면 문제가 있는 것.
2.```set-exectionpolicy unrestricted```입력 후 ```y``` 입력)




## React 사용이유
- Web app(앱이랑 사용성이 동일한 웹)을 만들기 위해서 

## VSCode에서 React세팅하기
- terminal에서 ```npx create-react-app [프로젝트 이름]``` 입력
  - 여기서 npx는 nodejs 설치가 돼있을 때 사용하는 라이브러리 설치 명령어이고, create-react-app은 리액트 세팅을 도와주는 라이브러리이다.
  - VSCode terminal에서 디렉토리를 이동한 후 그 디렉토리에서 만들고 싶을 때는 ```npx create-react-app .``` 입력
  
- VSCode 자동정렬
  - Ctrl + A 로 코드를 모두 선택한 후, Ctrl + K + F

- 줄 복사
  - Alt + Shift + down
  
## VSCode에서 React코드 미리보기
- terminal에서 ```npm start``` 입력

## Warning 없애기
- ```/* eslint-disable */``` 입력

## 구성
- APP.js는 메인페이지 들어갈 HTML 짜는 곳이고 실제 메인페이지는 public/index.html이다.
  - index.js가 APP.js를 index.html넣어주는 명령을 하는곳
  
- 모든 Component파일들은 ```import React from "react";```해줘야한다.
- react application은 하나의 component ```App```만을 랜더링 해야한다.
- public은 static파일 보관함, node_modules는 라이브러리 모은 폴더, src가 소스코드 보관함

## JSX
- React에서는 HTML처럼 생긴 JSX라는 문법을 사용
 
  1. ```<div>```에 클래스 줄 때 class대신 className
  2. 데이터 바인딩(서버에서 받아온 데이터 HTML에 넣는 것)이 쉬움 -> {변수명}, {함수명()}
  3. Style속성 -> style {object자료형으로 만든 스타일} ex) ``` <div style={ { color : 'blue', fontSize : '30px' } }```  **중괄호 사용**
    - camelCase 작명관습에 따라 속성명을 사용
    - className으로도 사용가능 



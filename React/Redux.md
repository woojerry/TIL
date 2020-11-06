- import할 때 중괄호의 유무 차이
    - import {Table} : Table이라는 변수/함수 가져오기 
    - import Table : export default된거 가져오기

## Redux
- Redux 세팅

- ```yarn add redux react-redux``` 또는 ```npm install redux react-redux```
- index.js 파일에서 ```import {Provider} from 'react-redux';```로 import해오기
- ```<Provider>```로 ```<APP>```감싸기 -> 감싸진 애들은 props없이도 state 공유가능
- createStore()함수 사용 
    - ```import {CreateStore} from 'redux'```
    - createStore()안에 state 저장
- ```<Provider>```에 props전송 

- Redux사용 이유 1. props없이 모든 컴포넌트가 state를 갖다쓸 수 있다.
- state 데이터 사용하려면 원하는 컴포넌트에서 props로 등록하고 쓴다.

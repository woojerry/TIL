## Ajax
> 서버에 새로고침없이 요청을 할 수 있게 도와주는 기술

- GET : 데이터, 웹페이지 등을 읽고싶을 때 하는 요청 (브라우저 주소창은 GET요청 하는 곳)
- POST : 데이터를 서버로 보내고 싶을 때 하는 요청
- GET/POST 요청 등을 보내면 항상 새로고침된다. -> Ajax를 통해서는 그렇지 않다.

- Ajax 사용 방법
  1. JQuery -> $.ajax()
  2. **axios** -> axios.get() // React
  3. 쌩JS fetch()

## Axios
> axios를 사용하면 JSON을 Object로 알아서 바꿔준다
- axios 라이브러리 설치 : 터미널에서 ```yarn add axios``` 또는 ```npm install axios```
- ```import axios from 'axios';```로 import

- 서버에 GET요청하기 : axios.get(데이터 요청할 URL); + .then() + .catch()
- ajax로 가져온 자료출력하는법 : ```.then((가져온자료) => { })```
```
function App(){
  let [shoes, shoes변경] = useState(Data);
  
  return(
  axios.get('[데이터요청URL]')
  .then((result)=>{
  // 성공했을 때 실행 코드
    shoes변경( [...shoes, ...result.data] ); // ajax로 data 가져올 때, 괄호 벗기고 다시 씌워주기 . 한번에 처리 ???
  })
  .catch(()=>{
  // 실패했을 때 실행 코드            
  })
  )
}
```

- 서버에 POST 요청하기 : axois.post(서버 URL, {보낼 데이터} ) + 요청시의 header 설정도 가능 
```jsx
axios.post('[데이터보낼URL]', { id : 'test', pw : 1234})
```
- 페이지를 처음으로 방문했을 때, ajax 요청하고 싶을 때 : useEffect()사용 

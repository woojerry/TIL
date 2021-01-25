## Fetch
> 브라우저에 내장된 ```fetch()```함수는  비동기 HTTP 요청을 하기 위해 사용한다.  fetch() 기본은 GET이다.

- 사용법 : Promise 타입의 객체를 반환, 반환된 객체는, API 호출이 성공했을 경우에는 응답(response) 객체를 resolve하고, 실패했을 경우에는 예외(error) 객체를 reject한다.
```js
fetch(url, options)
   .then(res => res.json()) // 요청이 성공할 경우 then에서 response 객체를 받아 처리
   .then(res => { // data를 응답 받은 후의 로직 })
  .catch((error) => console.log("error:", error)) // catch에서는 error 처리
```  

### GET
> 원격 API에 있는 데이터를 가져올 때 쓰이는 GET 방식의 HTTP 통신의 경우

```js
const endpoint = `${API_URL}movie/popular?api_key=${API_KEY}&lanuage=en-US&page=1`;

    fetch(endpoint)
      .then((response) => response.json())
      .then((response) => {
        console.log(response);
        // 요청이 성공했을 때 작업들
      });
```

### POST
> POST인 경우에는 fetch() 함수에 method 정보를 인자로 넘겨주어야 한다.

```js
const endpoint = 'https://api.google.com/user';

fetch(endpoint, {
    method: 'post',
    body: JSON.stringify({ // body는 JSON형태로 보내기 위해 JSON.stringfy() 함수에 객체를 인자로 전달하여 JSON형태로 변환한다.
        name: "yeri",
        batch: 1
    })
  })
  .then(res => res.json())
  .then(res => {
    if (res.success) {
        alert("저장 완료");
    }
  })
  ```
- 참고 : https://yeri-kim.github.io/posts/fetch/


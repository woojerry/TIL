## Promise
>  자바스크립트 비동기 처리에 사용되는 객체
- 주로 서버에서 받아온 데이터를 화면에 표시할 때 사용한다.

- 원래 코드 (ajax통신 예제)
```js
function getData(callbackFunc) {
  $.get('url 주소/products/1', function(response) {
    callbackFunc(response); // 서버에서 받은 데이터 response를 callbackFunc() 함수에 넘겨줌
  });
}

getData(function(tableData) {
  console.log(tableData); // $.get()의 response 값이 tableData에 전달됨
});
```

- Promise를 적용한 코드
```js
function getData(callback) {
  // new Promise() 추가
  return new Promise(function(resolve, reject) {
    $.get('url 주소/products/1', function(response) {
      // 데이터를 받으면 resolve() 호출
      resolve(response);
    });
  });
}

// getData()의 실행이 끝나면 호출되는 then()
getData().then(function(tableData) {
  // resolve()의 결과 값이 여기로 전달됨
  console.log(tableData); // $.get()의 reponse 값이 tableData에 전달됨
});
```

### resolve, reject
> ```new Promise()```의 콜백 함수 인자는 ```resolve```, ```reject```

```js
new Promise(function(resolve, reject) {
 // ...
});
``` 

- ```resolve```는 약속을 지킬 수 있는 상황이 되었을 때, 즉 **성공**했을 때 약속을 이행하고 결과 값을 외부로 ```return```하는 함수
```js
function getData() {
  return new Promise(function(resolve, reject) {
    var data = 100;
    resolve(data);
  });
}

// resolve()의 결과 값 data를 resolvedData로 받음
getData().then(function(resolvedData) {
  console.log(resolvedData); // 100
});
```

- ```reject```는 약속이 깨졌을 때, 즉 **실패** 상태에 결과 값을 ```return```
- 그리고, 실패 상태가 되면 실패한 이유(실패 처리의 결과 값)를 catch()로 받을 수 있다.
```js
function getData() {
  return new Promise(function(resolve, reject) {
    reject(new Error("Request is failed"));
  });
}

// reject()의 결과 값 Error를 err에 받음
getData().then().catch(function(err) {
  console.log(err); // Error: Request is failed
});
```

### Promise 예제
```js
let isTimeToSendResume = true
function sendResume(){
	// 이력서를 전송하는 수도 코드
	return true
}
let promiseSendResume = new Promise((resolve, reject) => {
	// 12월을 체크하는 변수
	if(isTimeToSendResume){
		sendResume();
		resolve('이력서 전송 완료')
	}else{
		reject('아직 이력서를 전송할 때가 아닙니다.')
	}
})

promiseSendResume.then((result) => {
	console.log('promise resolved =>', result)
}).catch((err) => {
	console.log('promise rejected =>', err)
})
```
```js
function sendResume(){
	// 이력서를 전송하는 수도 코드
	return true
}

const createPromiseSendResume = (isTimeToSendResume) => {
return new Promise((resolve, reject) => {
	// 12월을 체크하는 변수
	if(isTimeToSendResume){
		sendResume()
		resolve('이력서 전송 완료')
	}else{
		reject('아직 12월 1일이 되지 않았습니다.')
	}
})
}

function prepareInterview(){
	// 면접을 준비하는 수도 코드
	return true
}
const createPromisePrepareInterview = () => {
	return new Promise((resolve, reject) => {
		prepareInterview()
		resolve('면접 준비 완료')
})
}
```
- 이 2개의 ```Promise``` 예제의 연결
```js
function sendResume(){
	// 이력서를 전송하는 수도 코드
	return true
}

const createPromiseSendResume = (isTimeToSendResume) => {
return new Promise((resolve, reject) => {
	// 12월을 체크하는 변수
	if(isTimeToSendResume){
		sendResume()
		resolve('이력서 전송 완료')
	}else{
		reject('아직 12월 1일이 되지 않았습니다.')
	}
})
}

function prepareInterview(){
	// 면접을 준비하는 수도 코드
	return true
}
  
// 이전의 작업이 끝났음을 받는 message 변수 추가
const createPromisePrepareInterview = (message) => {
  return new Promise((resolve, reject) => {
		prepareInterview()
    resolve(message + ' -> ' + '면접 준비 완료')
})
}

createPromiseSendResume(true).then(
  (response) => { return createPromisePrepareInterview(response)}
).then((response) => console.log(response))
```



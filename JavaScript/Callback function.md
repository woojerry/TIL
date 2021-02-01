## Callback Function
>  다른 함수의 매개변수(파라미터)로 함수를 전달하고, 어떠한 이벤트가 발생한 후 매개변수로 전달한 함수가 다시 호출되는 것을 의미
- JS에서 비동기적 프로그래밍을 하기 위해 사용

### 비동기적 처리
> 특정 코드의 연산이 끝날 때까지 코드의 실행을 멈추지 않고 다음 코드를 먼저 실행하는 자바스크립트의 특성을 의미한다

### Synchronous callback
```js
console.log('1');
setTimeout( () => console.log('2'), 1000);
console.log('3');

function printImmediately(print) { // Synchronous callback
  print();
}
printImmediately( () => console.log('hello')); 
```
```js
// 출력 결과
1
3
hello
2
```

### Asynchronous callback

```js
console.log('1');
setTimeout( () => console.log('2'), 1000);
console.log('3');

function printImmediately(print) { // Synchronous callback
  print();
}
printImmediately( () => console.log('hello')); 

function printWithDealy(print, timeout) { // Asynchronous callback
	setTimeout(print, timeout);
}
printWithDelay( () => console.log('async callback'), 2000);
```

```
// 출력 결과
1
3
hello
2
async callback
```
<hr> 

```js
function getData() {
	var tableData;
	$.get('https://domain.com/products/1', function(response) {
		tableData = response;
	});
	return tableData;
}

console.log(getData()); // undefined
```

- 위 코드에서 ajax통신 get요청을 받아오기 전에 ```console.log```가 실행되어 undefined가 출력된다.
- 이렇게 특정 로직의 실행이 끝날 때까지 기다려주지 않고 나머지 코드를 먼저 실행하는 것이 비동기 처리

```js
function getData(callbackFunc) {
	$.get('https://domain.com/products/1', function(response) {
		callbackFunc(response); // 서버에서 받은 데이터 response를 callbackFunc() 함수에 넘겨줌
	});
}

getData(function(tableData) {
	console.log(tableData); // $.get()의 response 값이 tableData에 전달됨
});
```

- 이 코드는 콜백 함수로 비동기 처리 방식의 문제점 해결한 것이다.
- 이렇게 콜백 함수를 사용하면 특정 로직이 끝났을 때 원하는 동작을 실행시킬 수 있다.



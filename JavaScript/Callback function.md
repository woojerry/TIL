## Callback Function
>  다른 함수의 매개변수(파라미터)로 함수를 전달하고, 어떠한 이벤트가 발생한 후 매개변수로 전달한 함수가 다시 호출되는 것을 의미
- JS에서 비동기적 프로그래밍을 하기 위해 사용
```js
function print(callback) {  
    callback();
}
```
```js
function fn_fakeAsync(callback){
  calback();
}

console.log("------- fn_fakeAsync 호출 직전 -------");

fn_fakeAsync(function(){
  console.log("이게 비동기적으로 동작하길 바래");
});

console.log("------- fn_fakeAsync 호출 이후 -------");
```
- 결과
```
------- fn_fakeAsync 호출 직전 -------
이게 비동기적으로 동작하길 바래
------- fn_fakeAsync 호출 이후 ------
```

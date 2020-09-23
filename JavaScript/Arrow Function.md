## Arrow Function
  - arrow function은 함수스코프를 생성하고 (**실행 컨텍스트 생성시 this 바인딩 하지 않는다**)
```js
var b = function (a){ // 원래 함수
  return a*a        
}
```
  - funtction 지우고 화살표 붙인다.
```js
var b = (a) = > { // Arrow Function
  return a*a
}
```
  - 이렇게 함수 내부 내용이 return값 밖에 없다면 중괄호와 리턴까지 없앨 수 있다.
```js
var b = a => a*a // 인자가 하나만 있을 경우는 괄호도 생략 가능
```
### 다른 예시들
 
```js
var c = function (){ // 원래 함수
  return new Date()
}
```
  
```js
var c = () => new Date(); // 인자값이 없는 경우는 () 생략 불가
```
***

```js
var f = function(a) { // 원래 함수
  return function(b) {
    return a + b;
    }
}    
```
```js
var f = a => b => a+b;
```

  

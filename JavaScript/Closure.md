## Closure
> 함수 내부에 중첩 생성된 후 반환된 함수 객체
- 외부 함수가 종료된 후에도 외부 함수의 변수에 접근 가능 

```js
funtion sayHelloTo(name) {
  var text = 'Hello, ' + name;
  return function () {
    console.log(text);
  };
}

var sayHelloTo('John')() // 'Hello, John'
```
```js
function makeCounter() {
  var count = 0;
  return function() {
    return count++;
    };
}

var counter1 = makeCounter();
var counter2 = makeCOunter();
console.log(counter1()); // 0
console.log(counter1()); // 1
console.log(counter1()); // 0
```

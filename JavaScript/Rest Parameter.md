## Rest Parameter (나머지 매개변수)
>  매개변수 이름 앞에 세개의 점 ...을 붙여서 정의한 매개변수를 의미
- ``` ...[매개변수명]```
- Rest 파라미터는 함수에 전달된 인수들의 목록을 **배열**로 전달받는다.
```jsx
function foo(...rest) {
  console.log(Array.isArray(rest)); // true
  console.log(rest); // [ 1, 2, 3, 4, 5 ]
}

foo(1, 2, 3, 4, 5);
```
- 함수에 전달된 인수들은 순차적으로 파라미터와 Rest 파라미터에 할당된다.

```jsx
function foo(param, ...rest) {
  console.log(param); // 1
  console.log(rest);  // [ 2, 3, 4, 5 ]
}

foo(1, 2, 3, 4, 5);

function bar(param1, param2, ...rest) {
  console.log(param1); // 1
  console.log(param2); // 2
  console.log(rest);   // [ 3, 4, 5 ]
}

bar(1, 2, 3, 4, 5);
```

- Rest 파라미터는 이름 그대로 먼저 선언된 파라미터에 할당된 인수를 제외한 나머지 인수들이 모두 배열에 담겨 할당된다. 따라서 Rest 파라미터는 반드시 **마지막 파라미터**이어야 한다.

```jsx
function foo( ...rest, param1, param2) { }

foo(1, 2, 3, 4, 5);
// SyntaxError: Rest parameter must be last formal parameter
```

  

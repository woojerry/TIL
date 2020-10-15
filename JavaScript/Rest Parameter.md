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
  

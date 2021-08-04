## Nullish Coalescing
> null과 같은 것들을 병합하는 연산자 ,,
- 왼쪽 피연산자가 **null이나 undefined일 때만**, 오른쪽 피연산자를 return한다.
- 반대일 경우는 왼쪽 피연산자를 return한다.
```js
let a = null ?? 'hello';
let b = " ?? true;
let c = false ?? true;
let d = 0 ?? 1;
let e = undefined ?? 'world';

console.log(a) // 'hello'
console.log(b) // ''
console.log(c) // false
console.log(d); // 0
console.log(e); // 'world'
```

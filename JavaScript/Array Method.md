## .fliter()
> 주어진 함수의 테스트를 통과하는 모든 요소를 모아 새로운 배열로 반환

```js
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
```
```js
// 정수 배열에서 5의 배수인 정수만 모으기
var arr = [4, 15, 377, 395, 400, 1024, 3000];
var arr2 = arr.filter(function (n) {
  return n % 5 == 0;
});
console.log(arr2); // [15, 395, 400, 3000]
```

```js
//  3이 제외된 배열을 만들고 싶을 때,
array.filter((num) => num !== 3); // [1, 2, 4, 5]
```

```js
onRemove = (id) => {
// React를 활용한 To-do-list에서 제거함수
setTodos(todos.filter((todo) => todo.id !== id))
}
```

## .map
> callback 함수를 실행한 결과를 가지고 새로운 배열을 만들 때 사용

```js
// 제곱근 구하기
var numbers = [4,9,16,25,36];
var result = numbers.map(Math.sqrt);
console.log(result); // [2,3,4,5,6]
```
```js
// 2배의 값 구하기
var numbers = [ 1,2,3,4,5,6,7,8,9];
var newNumbers = numbers.map(number =>number *2);
console.log(newNumbers); // [2, 4, 6, 8, 10, 12, 14, 16, 18]
```
```js
// React를 활용한 To-do-list에서 Toggle함수
const onToggle = (id) => {
  todos.map((todo) => todo.id === id ? {...todo, done: !todo.done} : todo)
  )
}
```

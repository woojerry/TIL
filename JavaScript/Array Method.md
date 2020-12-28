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

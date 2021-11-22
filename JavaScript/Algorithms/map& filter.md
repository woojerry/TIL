- ```map과 filter```의 공통점은 기존배열은 건드리지 않으며 요소들을 순회한 후, **새로운 배열**을 return 한다는 것.
- 차이점은 ```map```은 **콜백함수가** 적용된 새로운 요소, ```filter```는 **조건문을** 만족한 요소를 반환한다는 것.

### map()
> 배열을 순회하며 요소마다 callback 함수 적용 후 새로운 배열로 리턴

```js
let newArray = arr.map(callback(currentValue[, index[, array]]) {
  // return element for newArray, after executing something
}
```

```js
let numbers = [1, 4, 9]
// 일반 함수
let roots = numbers.map(function(num) {
    return Math.sqrt(num)
})
// 화살표 함수
let roots = numbers.map((num) => Math.sqrt(num))
// roots is now     [1, 2, 3]
// numbers is still [1, 4, 9]
```
- ```React```에서의 응용: done을 반대로 만들어 새로운 배열로 ```setState()```할 경우
```js
setTodos(
  todos.map((todo) =>
    todo.id === id ? { ...todo, done: !todo.done } : todo
      )
    );
```

### filter()
> 배열을 순회하며 요소마다 조건 확인 후 조건을 만족하는 원소들로 구성된 새로운 배열 리턴

```js
const words = ['limit', 'exuberant', 'destruction', 'present'];
const result = words.filter(word => word.length > 6);
console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
```

- ```React```에서의 응용: done을 반대로 만들어 새로운 배열로 ```setState()```할 경우
```js
setTodos(todos.filter((todo) => todo.id !== id));
```

- ```React```에서의 응용: 실시간으로 input값에 따라 filter된 값 보여주기 위해 새로운 배열로 ```setState()```할 경우
```js
  useEffect(()=> {
        let tmp = response.filter(el => el.toUpperCase().includes(keyword.toUpperCase()));
        setFilteredResponses(tmp);
  }, [keyword])
```

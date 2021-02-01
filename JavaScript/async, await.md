### 등장 배경
> async와 await는 자바스크립트의 비동기 처리 패턴 중 가장 최근에 나온 문법으로 기존의 비동기 처리 방식인 콜백 함수와 프로미스의 단점을 보완하고 개발자가 읽기 좋은 코드를 작성할 수 있게 도와준다.

### Async

- 원래 Promise 코드
```js
function fetchUser() {
  return new Promise((resolve, reject) => {
     // do network request in 10 secs ...
     resolve('woojerry');
  });  
}

const user = fetchUser();

user.then(console.log); // woojerry
```

- async 적용 코드

```js
async function fetchUser() { // 자동적으로 함수 안의 코드블럭이 자동으로 Promise로 바뀌게 된다.
   // do network request in 10 secs ...
     return 'woojerry'
}

const user = fetchUser();
user.then(console.log); // woojerry
```

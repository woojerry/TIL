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

### Await
> ```await```는 반드시 ```async``` 내에서만 사용이 가능하다.
- 원래 Promise 코드

```js
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

function getApple() {
  return delay(1000)
  .then( () => 'apple');
}

function getBanana() {
  return delay(1000)
  .then( () => 'banana');
}

function pickFruits() {
  return getApple().then(apple => { 
    return getBanana().then(banana => `${apple} + ${banana}`);
  });
}  

pickFruits().then(console.log); // apple + banana
    
```
- async / await 적용 코드 

```js
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function getApple() {
  await delay(1000);
  return 'apple';
}

async function getBanana() {
  await delay(1000);
  return 'banana';
}

async function pickFruits() {
  try{
    const apple = await getApple();
    const banana = await getBanana();
    return `${apple} + ${banana}`;
  }  

pickFruits().then(console.log); // apple + banana
```

- 하지만 이 경우에는 apple 따오고 나서 banana를 따온다. (2초 소요)
- apple과 banana를 받아오는 것은 다른 작업이므로 기다릴 필요없이 동시에 수행 가능하다.

```js
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function getApple() {
  await delay(1000);
  return 'apple';
}

async function getBanana() {
  await delay(1000);
  return 'banana';
}

async function pickFruits() {
  const applePromise = getApple(); // Promise를 만들면 바로 Promise가 실행이 된다.
  const bananaPromise = getBanana();
  const apple = await applePromise;
  const banana = await bananaPromise;
  return `${apple} + ${banana}`;
}

pickFruits().then(console.log); // apple + banana
```
- 이렇게 병렬처리를 해준 경우에는 1초 만에 결과가 나타난다.
- 하지만 이 코드는 깔끔하지 않다.

```js
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function getApple() {
  await delay(1000);
  return 'apple';
}

async function getBanana() {
  await delay(1000);
  return 'banana';
}

// Promise에서 제공하는 all API 활용하기
// Promise 배열을 전달하게 되면 모든 Promise를 병렬적으로 받을 때까지 모아준다.

function pickAllFruits() {
  return Promise.all([getApple(), getBanana()]).then(fruits =>
    fruits.join(' + ')
  );
}  
pickAllFruits().then(console.log); // apple + banana
```


## 평가 전략 (Evaluation Strategy)
> 프로그래밍 언어에서 함수 호출의 아규먼트(argument)의 순서를 언제 결정하고 함수에 어떤 종류의 값을 통과시킬지 결정하는 것.
```js
 "Call-By" 또는 "Pass-By"로 시작하는 용어들을 의미한다.
 Call-By와 Pass-By는 동의어처럼 쓰이는데, Call은 함수를 호출할 때 사용하는 동사이고,
 Pass는 인자를 전달한다는 의미를 나타내는 동사이다.
 바라보는 기준이 함수냐 인자냐에 따라 사용하는 인자가 다른 것이고 큰 틀에서는 같은 의미다. 
```
- **JS는 자료형에 따라 call by value인지, call by reference인지 나뉜다.**
- **자료형을 크게 기본 타입/ 객체로 나눠서 보면 전자는 Call by Value, 후자는 Call by Reference이다. 

## Call by Value
```js
Call by Value의 특징
1. argument로 값이 넘어온다.
2. 값이 넘어올 때 복사된 값이 넘어온다.
3. 호출하는 쪽(caller)에서 인자를 복사해서 넘겨줬으므로 호출당한 쪽(callee)에서 인자를 바꿔도 호출하는 쪽에선(caller)영향을 받지 않는다.
```
```js
let a = 1;
function addOne(b) { // callee
  b= b + 1;
}  

addOne(a); // caller , a는 argument

console.log(a); // 1 
```

## Call by Reference
```js
Call by Reference의 특징
1. arguments로 reference(값에 대한 참조 주소, 메모리 주소를 담고있는 변수)를 넘겨준다.
2. reference를 넘기다 보니 해당 reference가 가리키는 값을 복사하지 않는다.
3. 호출하는 쪽의 인자를 복사해서 넘긴 게 아니므로 호출당한 쪽에서 인자를 건드리면 영향을 받는다.
```

```js
const me = {
  name: 'Jimmy'
};

function changeName(person) { // callee
  person.name = 'Joo';
}

console.log(me); // { name: 'Jimmy'}

changeName(me); // caller

console.log(me); // { name: 'Joo'} 

// me의 참조값이 전달되어 me와 person는 같은 참조값을 가지게 되어 변화 ? 
```
```js
const me = {
  name: 'Jimmy'
};

function changeName(person) { //callee
  person = { name: 'Joo' };
}

console.log(me); // { name: 'Jimmy' } 

changeName(me); // caller

console.log(me); // 정답은? -> Jimmy

// me에서 person으로 넘길 떄 참조값은 복사되어 넘어가고 
따라서 인수인 person은 복사된 참조값을 가지고 있고 같은 객체를 가지고 있다.
같은 참조값을 갖고 있었으나  다른 객체를 참조하게 된다 ??
```

```js
변수가 가리키는 메모리 공간에 저장되어 있는 값을 복사하여 전달한다는 관점에서 바라볼 때
자바스크립트는 항상 값에 의한 전달(Call By Value)만 존재
```

참고<https://velog.io/@jimmyjoo/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%ED%8F%89%EA%B0%80%EC%A0%84%EB%9E%B5-Call-By-Value-vs-Call-By-Reference-vs-Call-By-Sharing>




## Block Scope(블록 스코프)
- 블락에 의해 생기는 유효범위로 { }에 의해서 변수의 유효범위가 결정된다.
  -모든 코드 블록(함수, if 문, for 문, while 문, try/catch 문 등) 내에서 선언된 변수는 코드 블록 내에서만 유효하며 코드 블록 외부에서는 참조할 수 없다. 즉, 코드 블록 내부에서 선언한 변수는 지역 변수이다.
- **var일 때는 Blcok Scope의 영향을 받지 않고, let/const 에서는 받는다.**

```
let foo = 123; // 전역 변수

{
  let foo = 456; // 지역 변수
  let bar = 456; // 지역 변수
}

console.log(foo); // 123
console.log(bar); // ReferenceError: bar is not defined
```
- let 키워드로 선언된 변수는 블록 레벨 스코프를 따른다. 위 예제에서 코드 블록 내에 선언된 변수 foo는 블록 레벨 스코프를 갖는 지역 변수이다. 전역에서 선언된 변수 foo와는 다른 별개의 변수이다. 또한 변수 bar도 블록 레벨 스코프를 갖는 지역 변수이다. 따라서 전역에서는 변수 bar를 참조할 수 없다.
- var 키워드로는 동일한 이름을 갖는 변수를 중복해서 선언할 수 있었다. 하지만, let 키워드로는 동일한 이름을 갖는 변수를 중복해서 선언할 수 없다. 변수를 중복 선언하면 문법 에러(SyntaxError)가 발생한다.

https://poiemaweb.com/es6-block-scope

## Hoisting(호이스팅)
- 자바스크립트 함수는 실행되기 전에 함수 안에 필요한 변수값들을 모두 모아서 유효 범위의 최상단에 선언한다.
- 실제로 코드가 끌어올려지는 건 아니며, 자바스크립트 Parser 내부적으로 끌어올려서 처리하는 것이다.
-유효 범위: 함수블록 { }안에서 유효.

```
if(true){
let a =10
  if(true{
   console.log(a)
   const a = 20
  }
  console.log(a)
}
console.log(a)
```


https://gmlwjd9405.github.io/2019/04/22/javascript-hoisting.html

## 함수선언문 vs 함수표현식

### 함수선언문(Function Declaration)
- 일반적인 프로그래밍 언어에서의 함수 선언과 비슷한 형식
```
// 함수의 호출.
function printName(firstname) {
  var myname = "HEEE";
  return myname + " " +  firstname;
}
```

### 함수표현식(Function Expression)
- 변수값에 함수 표현을 담아 놓은 형태. 유연한 자바스크립트 언어의 특징을 활용한 선언 방식
```
var test1 = function() { // (익명) 함수표현식
  return '익명 함수표현식';
}

var test2 = function test2() { // 기명 함수표현식 
  return '기명 함수표현식';
}
```

### 함수선언문과 함수표현식의 차이 
- 함수선언문은 호이스팅에 영향을 받지만, 함수표현식은 호이스팅에 영향을 받지 않는다.
- 변수에 할당된 함수표현식은 끌어 올려지지 않기 때문에 이때는 변수의 스코프 규칙을 그대로 따른다.




## this
 - this는 함수 내에서 함수 호출 맥락(상황에 따라 달라진다)

 ### 일반 함수 실행 방식
  - 일반적으로 함수를 실행하는 가장 기본적인 방식
  - window : 웹브라우저 Javascript에서 전역 객체의 이름
```js
var age = 100;

function foo () {
  var age = 99;
  bar(age);
}

function bar (age) {
  console.log(this.age); // window.age = 100
}

foo(); 
```

### Dot Notation (점 방식)
  - 오브젝트 메소드 형식으로 실행시키는 방식
```js
var age = 100;
var ken = {
  age: 35,
  foo: function bar () {
    console.log(this.age);
  }
};
var wan = {
  age: 31,
  foo: ken.foo
};
var foo = ken.foo;
ken.foo();  // 35
wan.foo();  // 31
foo();  // 100
```
  - 객체안의 메소드지만 ```this```의 방식에 따라 각각 다르게 호출

### Explicit binding (명시적 바인딩)
 - 
 
 
 
 <출처> https://velog.io/@surim014/JavaScript-this

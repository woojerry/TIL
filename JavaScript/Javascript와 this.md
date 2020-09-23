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
 - call, bind, apply와 같은 메소드들을 사용해서 함수를 실행하는 명시적 바인딩 방법
 ```js
 var age = 100;

function foo () {
  console.log(this.age);
}

var ken = {
  age: 35,
  log: foo
};

// foo function gets invoked
// `this` refers to first argument

foo.call(ken); // 35

var kenLog = ken.log;

kenLog(); // 100
foo.call(ken); // 35
foo.apply(ken); // 35
```
 - ```foo.call(ken)``` : ```foo()```라는 함수가 실행이 되는데 ```this```의 값이 인자의 값으로 준 ```ken```이 되어 실행이 된다.
 
 - ```foo.apply(ken)``` : ```foo()```라는 함수 실행이 되고 ```ken```이라는 인자값이 ```this```의 값으로 설정이 되어 실행이 된다.
 
 ### 'new' keyword 방식
  - 일반적인 생성자 함수
 ```
 function Person (name, age) {
  this.name = name;
  this.age = age;
}

// instances"라고 한다.
var ken = new Person('ken huh', 34);
var wan = new Person('wan huh', 30);

console.log(ken);  // Person?{name: "ken huh", age: 34}
console.log(wan);  // Person?{name: "wan huh", age: 30}
```
 
 
 
 
 
 
 <출처> https://velog.io/@surim014/JavaScript-this%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90#1-regular-function-call---%EC%9D%BC%EB%B0%98-%ED%95%A8%EC%88%98-%EC%8B%A4%ED%96%89-%EB%B0%A9%EC%8B%9D

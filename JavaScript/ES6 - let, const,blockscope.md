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
  - var 키워드로는 동일한 이름을 갖는 변수를 중복해서 선언할 수 있었다. 하지만, let 키워드로는 동일한 이름을 갖는 변수를 중복해서 선언할 수 없다. **변수를 중복 선언하면 문법 에러(SyntaxError)가 발생한다.**

## Hoisting(호이스팅)
- 자바스크립트 함수는 실행되기 전에 함수 안에 필요한 변수값들을 모두 모아서 유효 범위의 최상단에 선언한다.
- 실제로 코드가 끌어올려지는 건 아니며, 자바스크립트 Parser 내부적으로 끌어올려서 처리하는 것이다.
  - 하지만 var 키워드로 선언된 변수와는 달리 let 키워드로 선언된 변수를 선언문 이전에 참조하면 참조 에러(ReferenceError)가 발생한다. 이는 let 키워드로 선언된 변수는 스코프의 시작에서 변수의 선언까지 일시적 사각지대(Temporal Dead Zone; TDZ)에 빠지기 때문이다.
  ```
  console.log(foo); // undefined
  var foo;

  console.log(bar); // Error: Uncaught ReferenceError: bar is not defined
  let bar;
  ```

  - var 키워드로 선언된 변수는 선언 단계와 초기화 단계가 한번에 이루어진다. 즉, 스코프에 변수를 등록(선언 단계)하고 메모리에 변수를 위한 공간을 확보한 후, undefined로 초기화(초기화 단계)한다. 따라서 변수 선언문 이전에 변수에 접근하여도 스코프에 변수가 존재하기 때문에 에러가 발생하지 않는다. 다만 **undefined**를 반환한다. 이후 변수 할당문에 도달하면 비로소 값이 할당된다. 이러한 현상을 **변수 호이스팅(Variable Hoisting)** 이라 한다.
  ```
  // 스코프의 선두에서 선언 단계와 초기화 단계가 실행된다.
  // 따라서 변수 선언문 이전에 변수를 참조할 수 있다.
  console.log(foo); // undefined

  var foo;
  console.log(foo); // undefined

  foo = 1; // 할당문에서 할당 단계가 실행된다.
  console.log(foo); // 1
  ```

  - ES6의 let으로 선언된 변수는 블록 레벨 스코프를 가지므로 코드 블록 내에서 선언된 변수 foo는 지역 변수이다. 따라서 지역 변수 foo도 해당 스코프에서 호이스팅되고 코드 블록의 선두부터 초기화가 이루어지는 지점까지 일시적 사각지대(TDZ)에 빠진다. 따라서 전역 변수 foo의 값이 출력되지 않고 **참조 에러(ReferenceError)** 가 발생한다.
  ```
  let foo = 1; // 전역 변수

  {
    console.log(foo); // ReferenceError: foo is not defined
    let foo = 2; // 지역 변수
  }
  ```
  <출처> https://poiemaweb.com/es6-block-scope

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




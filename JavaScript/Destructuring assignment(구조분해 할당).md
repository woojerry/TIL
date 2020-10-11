Destructuring assignment (구조분해 할당)
=============
## 배열 구조분해 할당(해체할당)
  
  ```jsx
  let colors = ['red', 'white', 'orange']
  
  let first = colors[0];  // let [ first, second, third ] = colors;
  let second = colors[1]; // 좌측 코드와 동일
  let third = colors[2];
  ```
  ```jsx
  let [first, second, third] = ['red', 'white', 'orange'];
  ```
  - 구조 분해할당의 좋은점은 내가 원하는 부분만 추출할 수 있다는 것
  ```jsx
  let[ , second ] = color; // second = white;
  ```
  ```jsx
  let[ , , third ] = color; // third = orange;
  ```
  - rest parameter일 때
  ```jsx
  const arr = [1, 2 ,3 ,4 ,5];
  const [ a, ...b ] = arr; // b = [2,3,4,5]
  const [, , ...c] = arr // c = [3,4,5]
  ```
  
## 객체 구조분해 할당
  - **객체는 index 대신 key가 존재.**  (객체 구조분해 할당은 조금 어려워서 나중에 적용하면서 다시 익히자!)
  ```jsx

  const iu = {
    name : '아이유',
    age : 25,
    gender : 'female'
  }
  
  const {
    name  // name = 아이유 
    age // age = 25
    gender // gender = female 
  } = iu
  ```
  
  - default parameter와의 연동
  ```jsx
  const phone = { 
    name : 'iPhone',
    color : undefined
  }
  
  const {
    name : n, // n = iPhone
    version : v = '6+' //  version 매칭할 값 없으면 v = 6+
    color: c = 'silver' // color는 default parameter이므로 c = sliver 
    } = phone;  
  ```
  ```jsx
  const people = { 
  'name': '홍길동',
  'address': '송파구',
  'age': 33
  }
  const {name:lastName, address, age, hometown='강원도'} = people; // lastName = '홍길동', adress = '송파구', age = 33, hometown = '강원도' 
  //const lastName = people['name']
  // const address = people['address']
  // const age = people['age']
  // const hometown = people['hometown'] ? people['hometown] : '강원도'
  ```

  ```jsx
  const ironMan = {
    name: '토니 스타크',
    actor: '로버트 다우니 주니어',
    alias: '아이언맨'
  };

  const captainAmerica = {
    name: '스티븐 로저스',
    actor: '크리스 에반스',
    alias: '캡틴 아메리카'
  };

  function print(hero) {
    const { alias, name, actor } = hero;
    const text = `${alias}(${name}) 역할을 맡은 배우는 ${actor} 입니다.`;
    console.log(text);
  }
  //function print(hero) {
  //  const text = `${hero.alias}(${hero.name}) 역할을 맡은 배우는 ${hero.actor} 입니다.`;  
  //  console.log(text);}
  ```
  ```jsx
  const { alias, name, actor } = hero;
  ```
  이 코드가 객체에서 값들을 추출해서 새로운 상수로 선언해 주는 것이다.

  다음 예제에서도 만약 데이터 베이스에 name, img_url, recent, url, like의 값이 저장돼있으면,
  주석부분과
  ```{name, img_url, recent, url, like}``` 이부분은 동일하다.
  ```jsx
  for (let i = 0; i < stars.length; i++) {
   let star = stars[i];
   let {name, img_url, recent, url, like} = star;
   //    let name = star['name']
   //    let url = star['url']
   //    let imgUrl = star['img_url']
   //    let recentWork = star['recent']
   //    let like = star['like']
  }                               
  ```

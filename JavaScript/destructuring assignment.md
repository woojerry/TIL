비구조화 할당 
=============
객체 비구조화 할당
```
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

//function print(hero) {
//  const text = `${hero.alias}(${hero.name}) 역할을 맡은 배우는 ${
//    hero.actor
//  } 입니다.`;
//  console.log(text);
//}

function print(hero) {
  const { alias, name, actor } = hero;
  const text = `${alias}(${name}) 역할을 맡은 배우는 ${actor} 입니다.`;
  console.log(text);
}
```
```
const { alias, name, actor } = hero;
```
이 코드가 객체에서 값들을 추출해서 새로운 상수로 선언해 주는 것이다.

다음 예제에서도 만약 데이터 베이스에 name, img_url, recent, url, like의 값이 저장돼있으면,
주석부분과
```{name, img_url, recent, url, like}``` 이부분은 동일하다.
```
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

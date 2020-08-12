비구조화 할당 - 배열 
=============
데이터 베이스에 name, img_url, recent, url, like의 값이 저장돼있으면,
주석부분과 {name, img_url, recent, url, like} 이부분은 동일하다.
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

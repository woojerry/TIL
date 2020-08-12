비구조화 할당 - 배열 
=============
데이터 베이스에 name, img_url, recent, url, like의 값이 저장돼있으면,
주석부분처럼 
```
for (let i = 0; i < stars.length; i++) {
                                let star = stars[i];
                              <span style="color:red">  let {name, img_url, recent, url, like} = star </span>;
                            //    let name = star['name']
                            //    let url = star['url']
                            //    let imgUrl = star['img_url']
                            //    let recentWork = star['recent']
                            //    let like = star['like']
                                       }
```

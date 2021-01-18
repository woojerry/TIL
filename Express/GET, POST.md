- GET        →  데이터 조회(Read)를 요청할 때
                              ex) 영화 목록 조회

* POST     →    데이터 생성(Create), 변경(Update), 삭제(Delete) 요청 할 때
                              ex) 회원가입, 회원탈퇴, 비밀번호 수정

## GET
> 어떤 정보를 서버에 요청해 정보를 가져오는 것 

- GET 방식으로 데이터를 전달하는 방법
```
?  : 여기서부터 전달할 데이터가 작성된다는 의미
& : 전달할 데이터가 더 있다는 뜻
딕셔너리처럼 key와 value가 쌍을 이루고 있다.

예시) google.com/search?q=해리포터&sourceid=chrome&ie=UTF-8

         위 주소는 google.com의 search 창구에 다음 정보를 전달
         q=해리포터                        (검색어 q의 값은 해리포터)
         sourceid=chrome        (브라우저 정보 sorceid의 값은 chrome)
         ie=UTF-8                      (인코딩 정보 ie의 값은 UTF-8)
```         

```js
app.get('경로', function(요청, 응답){
 응답.send('hello');
});
```

```js
// pet사이트를 보여주려고 할 때

const exrpess = require('express');
const app = express();

app.listen(5000, function(){
    console.log('listening on 5000)
});

app.get('/pet', function(req, res){
 res.sendFile(path.join(__dirname, "pet.html"));
});


app.get('/beauty', function(req, res){
 res.sendFile(path.join(__dirname, "beauty.html"));
});
```

## POST
> 사용자의 정보를 서버로 전송

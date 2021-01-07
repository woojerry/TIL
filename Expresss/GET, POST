## GET
> 어떤 정보를 서버에 요청해 정보를 가져오는 것 

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

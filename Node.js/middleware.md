### 미들웨어
- req, res, next를 가진 함수
- req : 클라이언트에서 오는 요청 정보가 담긴 객체
- res : 서버가 응답해주는 응답 정보가 담긴 객체
- next : 호출하면 다음 미들웨어를 실행

#### Example
```
// step1.js
var express = require('express');
var router = express.Router();

router.get('/', function(req, res, next) {
    console.log('step1');
    next();
});

module.exports = router;
```
```
// step2.js
var express = require('express');
var router = express.Router();

router.get('/', function (req, res, next) {
    console.log('step2');
    res.send('respond with a resource');
});

module.exports = router;
```
```
//app.js
var step1 = require('./routes/step1');
var step2 = require('./routes/step2');
app.use('/users', step1, step2);

//result
>> step1
>> step2
```

#### 에러처리 미들웨어
```
app.use(function(err, req, res, next) {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```
- 위와 같은 방식으로 오류처리 미들웨어 함수 정의 가능
- `err, req, res, next` 4개의 인수를 가짐
- 다른 `app.use()` 및 라우트 호출 정의 후, 가장 마지막으로 정의해야 됨

#### next
- next에 인수를 넣으면 에러처리 미들웨어로 이동
```
app.get('/user', (req, res, next) => {
  console.log('hello');
  next(error); //에러처리 미들웨어 실행
}, (req, res, next) => { //실행X
  console.log('world');
});

// 에러처리 미들웨어
app.use((err, req, res, next)=>{
  console.loh('error');
});

//결과
>> hello
>> error
```
- next('route') : 다음 미들웨어가 아닌, 다음 라우터로 이동
```
app.get('/', (req, res, next) => {
  console.log('hello');
  next('route'); // next안에 route를 쓰면 다음 라우터로 이동
}, (req, res, next) => { // 다음 미들웨어는 실행X
	console.log('world');
});

// 다음 라우터가 실행
app.get('/', (req, res) => {
  res.send('!');
});

//결과
>> hello
>> !
```
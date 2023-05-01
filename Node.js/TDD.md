### Jest 
- 테스팅 프레임워크
- 단위 테스트를 위하여 사용

#### Jest  시작하기
1. Jest 라이브러리 설치
```
npm install jest --save-dev
```
> -dev : 개발 환경에서만 사용

> --save : package.json에 추가

2. Test 스크립트 변경
```
# package.json
...
"test" : "jest",
...
```

3. 테스트 코드를 작성할 폴더 및 파일 기본 구조 생성

`test/unit/file-name.test.js`


#### Jest 파일 구조 & 사용법
```
describe {
  test(=it) {...}
  test(=it) {...}
}
```
- describe(name, function) : 여러 테스트를 그룹화하는 블록
- it(name, function, timeout) : 개별 테스트를 수행하는 곳

#### it 구조
```
it {
  expect().matcher();
}
```
- expect : 값을 테스트할 때마다 사용하며 matcher와 함께 사용
- matcher : 다른 방법으로 값을 테스트 하도록 사용하며 여러 종류가 있음
- 예시
```
test('2 + 2 = 4", () => {
  expect(2 + 2).toBe(4);
});
```

#### jest.fn()
- mock 함수를 생성하는 함수 

#### mocking 
- 테스트하고자 하는 코드가 의존하는 function이나 class에 대해 모조품을 만들어 `일단` 돌아가게 하는 것
- 테스트 하고 싶은 기능이 다른 기능들과 엮여 있을 경우 정확한 테스트를 하기 힘들기 때문
- ex) 요청이 오면 controller에서 정보 추출 후, DB에 넣어주는 단위 테스트를 할 경우
  - 실제 DB에 데이터를 넣는 방식의 테스트 X
    - 실제 트랜잭션이 일어나기에 IO 시간도 테스트에 포함, DB 연결 상태에 따라 테스트 실패할 수도 있음
    - 실패 시, 컨트롤러의 문제인지 DB의 문제인지 구분하기 어렵기 때문에 좋은 단위테스트가 아님
  - 실제 DB에 데이터를 넣은 것이 아닌, 넣은 셈 치자는 개념
    - 컨트롤러에 대한 테스트 중이니, DB가 잘 동작한다는 전제를 깔고 감
  - 기존 DB 저장 method를 mock함수로 만들고, mock함수를 호출했을때 반환 받기를 원하는 값을 직접 지정
> 참고 : https://inpa.tistory.com/entry/JEST-%F0%9F%93%9A-%EB%AA%A8%ED%82%B9-mocking-jestfn-jestspyOn

-----
### node-mocks-http
- 단위 테스트에서 request, response 객체를 얻기 위해 사용

#### http 객체(request, response) 얻기
```
req = httpMocks.createRequest();
res = httpMocks.createResponse();
```

#### req.body 설정
```
req.body = jsonValue;
controller.function(req, res, next);
```

----
### beforeEach
- 테스트에 공통된 코드가 있다면, beforeEach안에 넣어서 반복을 줄일 수 있음
- 하나의 describe의 테스트에서 코드가 반복된다면
```
describe{
  beforeEach()
  test()
  test()
}
```
- 모든 describe의 테스트에서 코드가 반복된다면
```
beforeEach()
describe{
  test()
  test()
}
```

-----
### Supertest
- nodejs http 서버를 테스트하기 위해 만들어진 모듈
- 통합 테스트 구현 용이

#### 사용방법
```
const request = require('supertest');

request(app)
  .get('/user')
  .expect('Content-Type', /json/);
  .expect('Content-Length', '15');
  .expect(200)
  end(function(err, res) {
    if (err) throw err;
  });
```
## Map
```js
const products = [
  { name: '상품1', price: 1000 },
  { name: '상품2', price: 1500 },
  { name: '상품3', price: 2000 },
];

const map = (func, iter) => {
  let res = [];
  for (const a of iter) {
    res.push(func(a));
  }
  return res;
}

log(map(p => p.name, products));
>> ['상품1', '상품2', '상품3']

log(map(p => p.price, products));
>> [1000, 1500, 2000];
```
- map 함수는 다형성이 높음
- 이터러블 프로토콜을 따르는 값들을 모두 사용가능
- 제너레이터 함수의 결과도 map 사용가능. 거의 모든 것들을 map 가능
```js
function *gen() {
  yield 2;
  yield 3;
  yield 4;
}
log(map(a => a * a, gen()));
>> [4, 9, 16]
```

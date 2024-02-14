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

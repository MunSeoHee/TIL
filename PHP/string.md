### 큰 따옴표(""), 작은 따옴표('')
- 문자열 내부에 변수 또는 개행문자가 있을 경우 차이가 존재
#### 변수 치환
- 큰 따옴표
```php
$string = "world";
echo "hello $string !";

//결과
// "hello world !"
```
- 작은 따옴표
```php
$string = "world";
echo "hello $string !";

//결과
// "hello $string !"
```

#### 개행 문자
- 큰 따옴표
```php
echo "hello world!\n";

//결과
// "hello world!"
```
- 작은 따옴표
```php
echo "hello world!\n";

//결과
// "hello world!\n"
```

#### ELT 함수
- N번째 위치의 문자열을 출력하는 함수
- 문자열의 위치는 0, 1, 2, 3의 순서가 아닌 1, 2, 3, 4의 순서이다
  - 첫번째 문자열을 출력하고 싶다면 N = 1

#### 사용 방법 
##### 기본 문법
```sql
SELECT ELT(N, str1, str2, str3, ...);
```
##### 지정한 위치에 값이 없는 경우 NULL을 출력
```sql
SELECT ELT(3, "A", "B");
>> NULL
```
##### N의 값이 실수인 경우, 반올림한 위치에 있는 값을 출력
```sql
SELECT ELT(1.3, "A", "B", "C");
>> "A"
```
##### 랜덤으로 문자열을 출력
```SQL
SELECT ELT(FLOOR(RAND() * 6) + 1, 'A', 'B', 'C', 'D', 'E', 'F');
```
  - [FLOOR(RAND() * n)](https://github.com/MunSeoHee/TIL/blob/main/Mysql/rand%20%ED%95%A8%EC%88%98.md)은 0부터 n-1까지의 랜덤 정수를 출력
  - ELT의 위치를 지정하는 N값은 1부터 시작해야되기 때문에 위에 값(FLOOR(RAND() * n))에 + 1을 해줌

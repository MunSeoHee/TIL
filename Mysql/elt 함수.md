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
SELECT ELT(0.5 + FLOOR(RAND() * 6), 'A', 'B', 'C', 'D', 'E', 'F');
```
  - RAND()의 결과로 0이 나오면 결과 값이 NULL이 되어버리기 때문에, 이를 방지하기위해 실수(0.5)를 더하여 반올림이 되게 함
  - [FLOOR(RAND() * N)는 RAND 함수에서 기록](https://github.com/MunSeoHee/TIL/blob/main/Mysql/rand%20%ED%95%A8%EC%88%98.md)

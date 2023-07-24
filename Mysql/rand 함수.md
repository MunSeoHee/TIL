#### Rand 함수
- 임의의 데이터를 반환

#### 사용법
##### 기본
```sql
SELECT RAND();
```

##### 랜덤 정렬
```sql
SELECT * FROM table ORDER BY RAND();
```
- 테이블의 인덱스를 이용하지 않는 정렬이기 때문에 데이터 양이 많은 경우 성능 저하가 될 수 있음
- 튜닝 방법 : https://blog.naver.com/sinjoker/221524576602

##### 랜덤 정수 값 출력
```sql
SELECT FLOOR(RAND() * N);
```
- 0부터 N-1까지의 정수 중에 랜덤으로 출력

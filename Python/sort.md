### 정렬 함수
- array.sort()
    - 원본 값이 정렬된 값으로 직접 수정
    - 리턴 값 None
    - list만 사용 가능
- sorted(array)
    - 원본 값에 변화 없음
    - 정렬 된 값을 리턴
    - list, tuple, dictionary, string 모두 사용 가능

```
array = [3,2,5,1]

print(sorted(array))
>> [1,2,3,5]
print(array)
>> [3,2,5,1]

print(array.sort())
>> None
print(array)
>> [1,2,3,5]
```

### 정렬 기준
```
sorted(list, key = function, reverse = bool)
list.sort(key = function, reverse = bool)
```
- reverse의 값이 True면 내림차순, False면 오름차순으로 정렬
- key값을 이용하여 여러 기준으로 정렬 가능

#### 다중 정렬 조건
```
array = ['abc', 'bac', 'bca', 'acb']
array.sort(key = lambda x : (x[1], x))
```
- 각 요소의 [1]번째를 기준으로 정렬하고, 만약 값이 동일하다면 x값 자체를 기준으로 정렬
    - 예시
        - 배열 각 요소의 [1]번째는 차례대로 ['b', 'a', 'c', 'c']이기 때문에 ['bac', 'abc', 'bca', 'acb']로 정렬이 된다
        - ['bca', 'acb']는 [1]번째의 값이 'c'로 동일하기 때문에, 두번째 정렬 조건이 들어가게 된다
        - 'bca'와 'acb'의 두 문자열이 순서대로 배치되면 'acb', 'bca'순이 된다
        - 따라서 정렬을 모두 마치면 ['bac', 'abc', 'acb', 'bca'] 가 된다
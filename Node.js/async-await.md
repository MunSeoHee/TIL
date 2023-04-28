### 🍇 동기 (Synchronous)
- 한 작업이 실행되는 동안 다른 작업은 멈춘 상태를 유지하고 자신의 차례를 기다리는 방식
- Node.js에서는 `Sync`라는 단어가 있으면 `동기`방식으로 동작
- ex) Action1 실행 -> Action1 실행 결과 받음 -> Action2 실행 -> Action2 실행 결과 받음
----

### 🍋 비동기 (Asynchronous)
- 어떠한 요청을 보내면 그 요청이 끝날 때까지 기다리는 것이 아니라, 응답에 관계없이 다음 동작이 실행되는 방식
- `Sync`가 없으면 `비동기`방식으로 동작
- ex) Action1 실행 -> Action2 실행 -> Action1, Action2 실행 결과 받음
----

### 🥝 Promise{pending}
```
const response = model.create();
console.log(response);
```
- 위와 같은 코드에서 `console.log(Object)`를 했을 때, `Promise{<pending>}`로 출력되는 것을 경험한 적이 많음
- Node.js는 기본적으로 비동기 처리 방식이기 때문에 `model.create()`의 결과를 받아오기 전에 `console.log()`가 실행
- 아직 미결상태의 값을 출력하려고 하니 `Promise{<pending>}`이라는 값이 출력

#### 해결 방법
- 방법 1 : `Async Request` & `.then()`
    - 비동기 요청이 끝난 뒤 .then() 안에 결과값이 들어오게 됨
    ```
    model.create()
        .then(response => {
            console.log(response);
        })
    ```
- 방법 2 : `async` & `await` (추천)
    - 함수 앞쪽에 `async`를 붙여주고 기다릴 부분에 `await`를 붙여 사용
    - `await`는 `async` 함수 안에서만 동작
    ```
    exports.controller = (req, res, next) => {
        const response = await model.create();
        console.log(response);
    }
    ```
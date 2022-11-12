# 이벤트 루프 (Event Loop)
![42eatw03fcha0e1qcrf0](https://user-images.githubusercontent.com/79434205/201484713-6f1c0d8f-c6bb-477f-aa7a-9ef8aa62cfb4.gif)
- 다중 스레드인 브라우저, Node.js 등 구동 환경이 단일 스레드인 자바스크립트와 연동하여 **여러 작업을 동시에 처리하기 위해 사용**하는 방식
- 작업이 들어오길 기다리다가 들어오면 처리하고 처리가 끝나면 다시 기다리는 것을 반복
- 구동 환경은 콜 스택을 처리, 이벤트 루프는 태스크 큐를 처리
- **콜 스택 -> 마이크로태스크 큐 -> 매크로태스크 큐** 순서대로 실행

## 콜 스택 (Call Stack)
- 호출된 함수가 차례로 쌓이는 스택
- `setTimeOut()` (매크로태스크), `Promise callback` (마이크로태스크) 등 비동기 관련 콜백 함수를 만나면 태스크 큐에 저장
- `async` 함수의 경우, `await`을 만나면 태스크 큐로 보내고 함수 실행 중단 후 호출했던 실행 컨텍스트로 돌아감
- 처리가 완료된 함수는 pop
- 콜 스택이 비면 태스크 이벤트 루프가 큐의 작업을 콜 스택으로 옮겨줌

## 태스크 큐 (Task Queue)
- **매크로태스크 큐**(Macrotask Queue) 라고도 함
- `setTimeOut()`, `setInterval()` 등의 함수 저장
- 큐에 있는 모든 작업을 처리할 때까지 수행
- 처리해야 할 작업이 없다면 (콜 스택이 비면) 실행 가능한 작업 중 **가장 오래된 것**을 dequeue하여 처리
- 마이크로태스크보다 **우선 순위 낮음**

### 마이크로태스크 큐(Microtask Queue)
- `Promise callback`, `process.nextTick()` 등의 함수 저장
- 큐에 있는 모든 작업을 처리할 때까지 수행
- `Promise.then()`의 경우 `Promise`가 계속 실행되어 **콜백 실행이 끝난 후 함수가 끝나지만**, `await`의 경우 `async` 함수는 중단되고 다음 함수로 넘어가 버리므로 **콜백이 나중에 실행**됨

## 이벤트 루프 과정
1. 매크로태스크 큐에서 가장 오래된 작업 1개를 실행
2. 마이크로태스크 큐가 빌 때까지 가장 오래된 것부터 모든 작업 실행
3. 화면 갱신이 필요하다면 렌더링
4. 매크로태스크 큐에 새로운 작업이 저장될 때까지 대기
5. 위의 과정 반복

## 참고 사이트
- https://developer.mozilla.org/ko/docs/Web/JavaScript/EventLoop
- https://ko.javascript.info/event-loop
- https://ko.javascript.info/microtask-queue
- https://meetup.toast.com/posts/89
- https://dev.to/lydiahallie/javascript-visualized-promises-async-await-5gke
# 제너레이터 (Generator)
- **이터레이터**이면서 **이터러블 객체**
- 이터러블 객체를 간단히 **구현**할 수 있음
- `function *` 키워드로 선언
- `yield` 를 사용하면 함수의 실행을 멈추고 값을 반환할 수 있음 -> 함수 한 개에서 **여러 번 값 반환 가능**
- `yield` 를 사용하면 단일 값을, `yield*` 를 사용하면 제너레이터 등 이터러블 객체를 반환 가능
- `next()` 에 인자를 넣음으로서 **값**을 제너레이터 안에 **전달** 가능 (처음 호출하는 `next()` 는 인자를 비워야 함)
- `yield` 가 `await` 의 역할을 하여 **비동기 함수**를 구현할 수 있음
- `return(값)` 을 사용하면 `{ value: 값, done: true }` 를 반환하여 제너레이터를 **종료**시킬 수 있음
- `throw(에러)` 를 사용하면 에러를 발생시켜 제너레이터를 **중단**시키고 따로 처리하게 할 수 있음

## 참고 사이트
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators
- https://ko.javascript.info/generators
- https://ui.toast.com/weekly-pick/ko_20151021
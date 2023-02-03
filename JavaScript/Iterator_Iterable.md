# 이터레이터 (Iterator)
- `{ value: 반환 값, done: true / false }` **형태의 객체를 반환**하는 `next()` 메서드를 가진 객체
- **순회 종료** 시의 반환 값은 `{ done: true }`

# 이터러블 객체 (Iterable Object)
- **반복할 수 있는 객체**
- **이터레이터를 반환**하는 `[Symbol.iterator]()` 를 가진 객체
- 자신 또는 프로토타입이 `[Symbol.iterator]()` 를 가졌다면 모두 이터러블 객체
- `for-of` **반복문**, **전개 구문**, **구조 분해 할당** 등을 사용할 수 있음
- `Array`, `Map`, `Set`, **DOM** `NodeList`, `String` 등


## 참고 사이트
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators
- https://ko.javascript.info/iterable
- https://ui.toast.com/weekly-pick/ko_20151021
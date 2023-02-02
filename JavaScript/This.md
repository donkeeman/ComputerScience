# this
- 호출 방식에 따라 동적으로 결정되는 **객체**
- 값을 임의로 변경할 수 없음

## 전역에서 호출 시
- **전역 객체** ( `window` (브라우저), `global` (노드) ) 를 가리킴

## 일반 함수에서 호출 시
- **비엄격 모드**에서는 **전역 객체**를 가리킴
- **엄격 모드**에서는 `undefined`
- `call()`, `apply()`, `bind()`를 이용하여 `this`를 직접 **지정** 가능

### `call()`
- 인자를 **나열**하는 방식으로 전달
- 함수를 **즉시 실행**
```javascript
function.call( this로 지정할 객체, 인자 1, 인자 2, ... );
```

### `apply()`
- 인자를 **배열**으로 전달
- 함수를 **즉시 실행**
```javascript
function.apply( this로 지정할 객체, [인자 1, 인자 2, ...] );
```

### `bind()`
- 함수에 인자를 전달 후 그 **함수를 반환**
- 함수를 즉시 실행하지 않기 때문에 **나중에 실행할 수 있음**
```javascript
const newFunction = function.bind( this로 지정할 객체, 인자 1, 인자 2, ...);
newFunction();

// bind 시 원래 function의 인자보다 적게 준 경우에는 추가 인자를 넘겨줄 수도 있음
// 원래 function의 인자의 개수보다 많이 넘겨주면 나머지 인자는 무시됨
newFunction(인자 3, 인자 4, ...);
```

## 화살표 함수에서 호출 시
- 자신을 감싸고 있는 **바로 상위의 렉시컬 환경**을 가리킴 (전역에 있는 경우 전역 객체를 가리킴)
- `call()`, `apply()`, `bind()`를 사용하여 인자를 지정해 줄 수는 있으나 `this`**의 지정은 불가**

## 객체의 메서드에서 호출 시
- 메서드를 **호출한 객체**를 가리킴
- **프로토타입**, **접근자**, **설정자**에서도 동일

## 생성자 함수에서 호출 시
- **생성자로 만들어진 새 객체**를 가리킴

## 이벤트 핸들러에서 호출 시
- **이벤트가 연결된 객체**를 가리킴
- HTML에서의 이벤트 핸들러 호출은 **해당 HTML 요소**를 가리킴

## 참고 사이트
- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/this
- https://poiemaweb.com/js-this
- https://www.w3schools.com/js/js_this.asp
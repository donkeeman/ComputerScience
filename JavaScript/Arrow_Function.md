# 화살표 함수 (Arrow Function)
- 자바스크립트 ES6 문법에서 새로 등장한 함수 표현 방식
- `( argument ) => { expression }` 의 형태
- 인수가 하나인 경우 소괄호를 생략할 수 있음
- 인수가 없을 경우 `()` 처럼 무조건 소괄호를 적어야 함
- 표현식이 한 줄인 경우 중괄호와 `return`을 생략할 수 있음
- 표현식이 여러 줄인 경우 중괄호로 감싸주어야 하며 `return`과 함께 반환값을 명시해줘야 함
- 간단한 함수 또는 콜백 함수에 사용하기 좋음
- `function ( argument ) { expression }` 방식을 완전히 대체하는 것은 불가능

## `function ( argument ) { expression }` 방식과의 차이점
- 기명 함수 불가, 무조건 **익명 함수**
- 함수를 사용하는 코드보다 전에 선언해야 함 (**호이스팅 불가**)
- `this`를 호출하면 자기 자신이 아닌, **자신을 감싸는 렉시컬 환경**을 참조함
- **생성자 함수**로 사용할 수 **없음**
- **함수의 인수 배열**인 `arguments`를 사용할 수 **없음**
- 객체의 **메서드**로 사용할 수 **없음**
- **prototype**으로 사용할 수 **없음**

## 참고 사이트
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions
- https://ko.javascript.info/arrow-functions-basics
- https://ko.javascript.info/arrow-functions
# 호이스팅 (Hoisting)
- 변수 또는 함수를 선언하기 전에도 사용할 수 있도록 **선언문을 현재 범위의 맨 위로 올리는 동작**
- 실제 코드가 끌어올려지는 것이 아니라 코드 실행 전 자바스크립트 내에서 **끌어올려진 것처럼 자체적으로 처리**하는 것
- 선언문만 끌어올리고 **초기화 동작은 끌어올리지 않음**
- **변수의 호이스팅**이 함수의 호이스팅보다 먼저 이루어짐
- **함수 표현식**은 호이스팅 **불가능**

## 일시적 사각 지대 (Temporal Dead Zone, TDZ)
- 스코프의 선언 지점부터 초기화 지점까지의 구간
- `var`와 달리, `let`과 `const`는 호이스팅이 일어나지만 선언만 되고 **초기화는 이루어지지 않은 상태로 메모리에 저장**되므로 초기화되기 전, TDZ에서는 참조할 수 없음 (**화살표 함수**도 마찬가지)


## 참고 사이트
- https://developer.mozilla.org/ko/docs/Glossary/Hoisting
- https://www.w3schools.com/js/js_hoisting.asp
- https://poiemaweb.com/js-execution-context
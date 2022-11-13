# 이벤트 버블링 (Event Bubbling)
- 처음 이벤트가 트리거된 태그부터 시작해서 상위 태그, 상위 태그 ... `document`까지 거슬러 **올라가면서** 각각 적용된 이벤트 핸들러가 실행되는 현상
- 상위 태그에 이벤트 핸들러가 적용되어 있다면, 그 **하위 태그에 이벤트 핸들러가 없어도 이벤트가 실행**됨
- 상위 태그에 이벤트를 전파시키고 싶지 않다면 상위 태그에 `Event.stopPropagation()` 메소드를 사용

## `event.target`
- 실제 이벤트가 **트리거**된 가장 하위 객체
## `event.currentTarget`
- 이벤트 핸들러가 **할당**되어 있는 객체 (`obj.addEventListener(...)`일 때 `obj`)
- `this`와 같음

# 이벤트 캡처링 (Event Capturing)
- 최상위 태그부터 시작하여 하위 태그로 **내려가면서** 이벤트가 발생한 태그를 찾으면 실행시키는 것
- 이벤트가 트리거된 태그의 하위 태그에는 이벤트가 적용되지 않음
- `addEventListener()`에서 `capture` 옵션을 `true`로 설정해 주어야 함 (기본값인 `false`는 버블링만 발생)
- 아래로 내려가면서 **캡처링** -> 이벤트 타겟의 이벤트 **실행** -> 다시 위로 올라가면서 **버블링**
- 버블링과 마찬가지로 `Event.stopPropagation()` 메소드를 이용하여 이벤트 전파를 막을 수 있음
- 사용되는 경우가 많지 않음

# 이벤트 위임 (Event Delegation)
- **최상위 요소에만 이벤트 핸들러를 적용**하여 그 핸들러에서 하위 요소들의 이벤트를 제어하는 것
- `event.target`의 `id`가 무엇인지 등 조건문으로 **하위 요소들의 서로 다른 동작을 지정**할 수 있음
- **동적으로 추가되는 요소**의 이벤트 적용에 용이
- **메모리 낭비, 누수 방지**

## 참고 사이트
- https://ko.javascript.info/bubbling-and-capturing
- https://www.geeksforgeeks.org/what-is-event-bubbling-and-event-capturing-in-javascript/
- http://javascript.info/tutorial/event-delegation
- https://ui.toast.com/weekly-pick/ko_20160826
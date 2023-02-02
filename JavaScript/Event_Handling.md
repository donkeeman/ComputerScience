# 이벤트 핸들링 (Event Handling)
- 이벤트 발생 시 **실행할 동작을 지정**하는 것
- **이벤트 바인딩**을 통해 컴포넌트와 이벤트 핸들러를 연결

## HTML 이벤트 핸들러
- HTML 코드에 **인라인**으로 작성
- 이벤트 타겟은 해당 HTML 요소이며 따로 명시하지 않음
- `this` 는 이벤트 타겟을 가리킴
- HTML 요소의 속성에 접근 가능
- HTML과 자바스크립트를 혼용하기 때문에 유지 보수가 어려움
- 자바스크립트가 로딩되기 전 HTML 요소에 이벤트가 발생할 경우 에러가 날 수 있음
- 위의 문제점으로 인해 **사용을 지양해야 함**
```html
<div onclick="clickHandler();">Event Target1</div>
<div onkeydown="keyDownHandler();">Event Target2</div>

<script>
    function clickHandler() {
        console.log("clicked!");
    }

    function keyDownHandler() {
        console.log("key pressed!");
    }
</script>
```

## DOM Level 0 이벤트 핸들러
- `onclick`, `onkeydown`, ... 등의 **이벤트 핸들러 속성**을 이용하여 작성
- 이벤트 한 개당 **한 개**씩의 핸들러 함수만 등록 가능하므로 이벤트 핸들러가 여러 개이면 **마지막 한 개만 실행됨**
- 이벤트 **버블링**만 지원
```javascript
function clickHandler() {
    console.log("clicked!");
}

function keyDownHandler() {
    console.log("key pressed!");
}

// 이벤트 핸들러 등록
EventTarget1.onclick = clickHandler;
EventTarget2.onkeydown = keyDownHandler;
// 한 개의 이벤트만 등록 가능하므로 위의 이벤트는 덮어씌워지고 아래의 이벤트만 실행됨
EventTarget2.onkeydown = () => {
    console.log("key pressed!!!!");
}

// 이벤트 핸들러 제거
EventTarget1.onclick = null;
EventTarget2.onkeydown = null;
```

## DOM Level 2 이벤트 핸들러
- `addEventListener()`를 이용하여 작성
- 이벤트 이름, 핸들러 함수, 캡처링 여부 (기본값: `false`) 를 인자로 받음
- 이벤트 한 개에도 이벤트 핸들러를 **여러 개** 등록할 수 있음
- 이벤트 **캡처링** / **버블링** 둘 다 지원
- HTML 요소 외에도 **모든 DOM 요소**에 이벤트 바인딩 가능
```javascript
function clickHandler() {
    console.log("clicked!");
}

function keyDownHandler() {
    console.log("key pressed!");
}

// 이벤트 핸들러 등록
EventTarget1.addEventListender("click", clickHandler);
EventTarget2.addEventListender("keydown", keyDownHandler);
// 여러 이벤트를 등록할 수 있으므로 위의 이벤트, 아래의 이벤트 모두 실행됨
EventTarget2.addEventListender("keydown", () => {
    console.log("key pressed!!!!");
});

// 이벤트 핸들러 제거
EventTarget1.removeEventListender("click", clickHandler);
EventTarget2.removeEventListender("keydown", keyDownHandler);
// addEventListener 때와 같은 인자를 전달해야 하므로, 핸들러 함수가 익명 함수였다면 제거되지 않음
// 그래서 아래의 이벤트는 제거되지 않음
EventTarget2.removeEventListender("keydown", () => {
    console.log("key pressed!!!!");
});
```

## 참고 사이트
- https://developer.mozilla.org/en-US/docs/Web/Events/Event_handlers
- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events
- https://www.javascripttutorial.net/javascript-dom/handling-events-in-javascript/
- https://en.wikipedia.org/wiki/DOM_events#Event_handling_models
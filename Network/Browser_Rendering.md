# 브라우저의 렌더링
주소창에 URL을 입력, 링크 클릭 또는 form 전송 등 사용자의 요청이 발생하고, 서버가 응답하면 브라우저는
## 1. DOM (Document Object Model) 트리 생성
- 서버로부터 받은 HTML 파일을 브라우저가 이해할 수 있는 형태인 DOM 트리로 바꾸는 과정
- **파서 (Parser)** 는 인코딩에 따라 파일을 **문자열로 변환**하고 **토큰화**하여 태그(`<...></...>`)로 이루어진 **노드** 생성
- 파싱 중 `<script>` 태그를 만나면 HTML 파싱을 멈추고 자바스크립트 코드를 실행 -> `<script>`에 `async` / `defer` 옵션을 사용하여 파싱 중단을 막을 수 있음
- **노드 간의 관계**를 트리 형태로 구조화
## 2. CSSOM (CSS Object Model) 트리 생성
- DOM 노드에 **스타일**을 적용하는 과정
- `<style>` 태그, HTML의 인라인 스타일 등 다양한 방식의 스타일을 모두 읽고 CSSOM 생성
- 스타일은 아래의 것으로 덮어씌워짐 (**Cascading**)
## 3. 렌더 트리 (Render Tree) 생성
- DOM 트리와 CSSOM 트리를 결합하여 **렌더링**될 요소들만 렌더 트리에 추가
- DOM 트리에서 `<meta>`, `<title>` 등 화면에 그려지지 않는 노드는 렌더 트리에 포함되지 않음
- CSSOM 트리에서 `display: none` 이 적용되어 화면에 그려지지 않는 노드는 렌더 트리에 포함되지 않음
- CSSOM 트리에서 `visuality: hidden` 이 적용된 노드는 보이지 않지만 자리를 차지하므로 렌더 트리에 포함됨
## 4. 레이아웃 (Layout)
- 각 DOM 노드의 **너비/높이**와 DOM 노드가 그려질 **위치**를 계산
- 처음 레이아웃이 그려지고 나서 노드의 너비/높이, 위치를 다시 계산해야 할 경우 **리플로우** 발생
### 리플로우 (Reflow)
- 리소스를 가장 많이 사용
- CPU 사용
- 리플로우가 발생하는 경우
    - **뷰포트의 크기**를 변경하는 경우
    - **DOM 노드**가 추가/제거된 경우
    - `position`, `margin`, `padding`, `width`/`height` 등 **리플로우가 일어나는 요소**를 변경하는 경우
    - **폰트 크기**를 변경한 경우
    - **이미지 크기**를 변경한 경우
## 5. 페인트 (Paint)
- 계산된 위치와 크기를 바탕으로 DOM 노드를 픽셀 단위로 **화면에 그리는 과정**
- 처음 페인트되고 나서 노드를 다시 그려야 할 경우 **리페인트** 발생
### 리페인트 (Repaint)
- 리플로우보다는 리소스를 적게 사용
- CPU 사용
- 리페인트가 발생하는 경우
    - **리플로우**가 발생한 경우
    - `background`, `color` 등 **리페인트만 일어나는 요소**를 변경하는 경우
## 6. 합성 (Compositing)
- `z-index` 사용 등 페인트 과정에서 레이어가 나누어진 경우, 각 레이어를 겹쳐 **하나의 페이지로 만듦**
- 리소스를 가장 적게 사용
- GPU 사용

이 과정을 **중요 렌더링 경로** (Critical Rendering Path) 라고도 함

## 렌더링 최적화 방법
- 리플로우 최소화
    - 불필요한 요소, CSS 규칙 등을 삭제
    - 복잡한 CSS 선택자 사용을 지양
    - 애니메이션 등으로 자주 바뀌는 요소의 경우 `position: absolute / fixed`를 사용
    - `transform`, `opacity` 등 합성 과정만 발생하는 요소 사용
- HTML, CSS, JavaScript 파일 크기를 줄이기
    - 공백 / 들여쓰기 / 줄바꿈 삭제
    - 주석 삭제
- 이미지 최적화
    - 이미지 너비/높이를 미리 정하기
    - 손실 / 무손실 압축으로 이미지 파일의 크기 줄이기
    - 반응형 이미지를 사용하여 환경에 적합한 이미지만 제공
- 지연 로딩 (Lazy Loading)
    - 당장 필요하지 않은 요소는 렌더링하지 않고 필요할 때만 렌더링

## 렌더링 엔진
- 같은 웹 페이지여도 브라우저의 렌더링 엔진에 따라 다르게 그려질 수 있음

|엔진|브라우저|
|:-:|:-:|
|Blink|Chrome, Edge, Opera 등 **Chromium** 기반 브라우저|
|WebKit|Safari, 다른 브라우저들의 **iOS** 버전|
|Gecko|Firefox, Thunderbird 등 **Mozilla 재단**의 브라우저|
|⋮|⋮|

## 참고 사이트
- https://developer.chrome.com/blog/inside-browser-part3/
- https://developer.mozilla.org/ko/docs/Web/Performance/How_browsers_work
- https://developer.mozilla.org/ko/docs/Web/Performance/Critical_rendering_path
- https://medium.com/jspoint/how-the-browser-renders-a-web-page-dom-cssom-and-rendering-df10531c9969
- https://developers.google.com/speed/docs/insights/browser-reflow?hl=ko
- https://dev.to/omerwow/understanding-browser-rendering-and-performance-optimization-5f81
- https://ko.wikipedia.org/wiki/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80_%EC%97%94%EC%A7%84
# 리액트 컴포넌트의 생명 주기 (Lifecycle)
<table align="center">
    <thead>
        <tr>
            <td align="center">
                <a href="https://wavez.github.io/react-hooks-lifecycle/">클래스 컴포넌트 (클릭 시 사이트로 이동)</a>
            </td>
            <td align="center">
                <a href="https://wavez.github.io/react-hooks-lifecycle/">함수형 컴포넌트 (클릭 시 사이트로 이동)</a>
            </td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td align="center">
                <a href="https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/">
                    <img src="https://user-images.githubusercontent.com/79434205/227422404-e7532aa1-f0e5-49d4-b78e-b1831ed82a69.png" width="400" />
                </a>
            </td>
            <td align="center">
                <a href="https://wavez.github.io/react-hooks-lifecycle/">
                    <img src="https://user-images.githubusercontent.com/79434205/227490335-fe0bdba5-8714-4383-beec-e141ea7ede64.png" width="400" />
                </a>
            </td>
        </tr>
    </tbody>
</table>

모든 리액트 컴포넌트는 생명 주기 메서드를 가지며, 메서드를 이용하여 아래와 같은 과정 중 특정 시점에서 실행할 동작을 지정할 수 있음

## 1. 마운트 (Mount)
- 컴포넌트가 생성되어 DOM에 추가되는 과정
1. **`constructor()`** (클래스)
    - 컴포넌트의 생성자를 구현하는 메서드
    - 유일하게 `this.state`로 직접 할당 가능하지만 `this.setState()`는 사용 불가
    - 함수형 컴포넌트의 경우, 생성자 함수 역할을 하는 함수는 따로 없으며 `useState()`로 초기값을 지정
2. `static getDerivedStateFromProps()` (클래스) / `useState()`의 `setState()` (함수형)
    - 컴포넌트의 렌더링 직전에 호출되는 메서드
    - 시간에 따라 변하는 `props`에 `state`가 의존하는 특수한 경우에만 사용 -> 잘 사용되지 않음
3. **`render()`** (클래스) / **`return()`** (함수형)
    - 컴포넌트에서 반드시 구현되어야 하는 유일한 메서드
    - 호출될 때마다 같은 값을 반환하여야 함 -> `setState()` 사용 불가
    - 브라우저와 상호작용하지 않음
    - JSX 외에도 string, number, portal, null, boolean 값 등을 반환할 수 있음

==DOM에 컴포넌트 추가==

4. **`componentDidMount()`** (클래스) / **`useEffect()`**, **`useLayoutEffect()`** (함수형)
    - 컴포넌트가 DOM에 추가된 직후 호출되는 메서드
    - DOM 조작, 네트워크 요청, 데이터 구독에 사용

## 2. 업데이트 (Update)
- 컴포넌트의 변경 사항을 업데이트하고 DOM에 반영하는 과정
1. `static getDerivedStateFromProps()` (클래스) / `useState()`의 `setState()` (함수형)
    - 컴포넌트의 렌더링 직전에 호출되는 메서드
    - 시간에 따라 변하는 `props`에 `state`가 의존하는 특수한 경우에만 사용 -> 잘 사용되지 않음
2. `shouldComponentUpdate()` (클래스) / `useMemo()` (함수형)
    - 컴포넌트의 `props` 또는 `state`가 바뀌어서 컴포넌트를 새로 렌더링해야 할 때 호출되는 메서드
    - 기본값은 `true`
    - 최초 렌더링과 `forcedUpdate()` 메서드 사용 시에는 실행되지 않음
    - 성능 최적화를 위해서만 사용 -> 잘 사용되지 않음
3. **`render()`** (클래스) / **`return()`** (함수형)
    - 컴포넌트에서 반드시 구현되어야 하는 유일한 메서드
    - 호출될 때마다 같은 값을 반환하여야 함 -> `setState()` 사용 불가
    - 브라우저와 상호작용하지 않음
    - `shouldComponentUpdate()`가 `false`이면 실행되지 않음
4. `getSnapshotBeforeUpdate()` (클래스)
    - 컴포넌트의 변경 사항이 DOM에 반영되기 직전 호출되는 메서드
    - 스크롤 위치를 얻는 등 바뀌기 전의 DOM 정보가 필요할 때 사용 -> 잘 사용되지 않음
    - 함수형 컴포넌트의 경우, 이 역할을 하는 메서드가 따로 없으므로 필요하다면 클래스 컴포넌트로 작성해야 함

==DOM에 컴포넌트 변경 사항 반영==

5. **`componentDidUpdate()`** (클래스) / **`useEffect()`**, **`useLayoutEffect()`** (함수형)
    - 컴포넌트의 변경 사항이 DOM에 반영된 직후 호출되는 메서드
    - 최초 렌더링 시에는 호출되지 않고, 오직 변경 사항이 있었을 때만 호출됨
    - `props`가 바뀌었을 때의 DOM 조작, 네트워크 요청 등에 사용
    - `shouldComponentUpdate()`가 `false`이면 실행되지 않음

## 3. 언마운트 (Unmount)
- 컴포넌트가 DOM에서 제거되는 과정
1. **`componentWillUnmount()`** (클래스) / `useEffect()`, `useLayoutEffect()` 내부의 **`return () => {}`** (함수형)
    - 컴포넌트가 DOM에서 제거되기 직전 호출되는 메서드
    - 이 이후로는 컴포넌트가 다시 렌더링되지 않음
    - 타이머, 네트워크 요청, `componentDidMount()`에서 한 데이터 구독 등의 해제에 사용

## 오류 처리
- 컴포넌트의 하위 컴포넌트에서 렌더링, 생명 주기 중 오류가 생겼을 때 호출되는 메서드
- `static getDerivedStateFromError()` (클래스)
    - 컴포넌트가 DOM에 추가되기 전 (렌더링 단계) 호출 -> 다른 동작을 같이 수행할 수 없음
    - 오류 정보를 반환해야 함
    - 함수형 컴포넌트의 경우, 이 역할을 하는 메서드가 따로 없으므로 컴포넌트를 따로 작성해야 함
- `componentDidCatch()` (클래스)
    - 컴포넌트가 DOM에 추가된 이후 (커밋 단계) 호출 -> 다른 동작을 같이 수행할 수 있음
    - 반환값이 없어야 함
    - 함수형 컴포넌트의 경우, 이 역할을 하는 메서드가 따로 없으므로 컴포넌트를 따로 작성해야 함

## 그 외 생명 주기 메서드
- `setState()` (클래스) / `useState()`의 `setState()` (함수형)
    - `state`를 변경할 때 사용
    - `state`가 실제로 변경되지 않더라도 무조건 리렌더링함
    - 비동기적이기 때문에 데이터가 바로 반영되지 않음
- `forceUpdate()` (클래스) / `useSyncExternalStore()` (함수형)
    - `render()` 메서드를 사용하여 업데이트하지 못하는 경우, 즉 `props`나 `state`를 사용하지 않고 외부 데이터를 사용하는 경우에 컴포넌트를 강제 리렌더링하기 위해 사용

## 참고 사이트
- https://ko.reactjs.org/docs/react-component.html
- https://react.dev/reference/react/Component
- https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/
- https://wavez.github.io/react-hooks-lifecycle/
# 실행 컨텍스트 (Execution Context)
- **코드의 변환 및 실행**을 처리하는 환경
- 전역 실행 컨텍스트, 함수 실행 컨텍스트, eval() 실행 컨텍스트, 블록 실행 컨텍스트로 나뉨
- Creation Phase -> Execution Phase의 순서로 실행
- 실행 컨텍스트가 생성되면 콜 스택에 push되고 실행이 끝나면 pop됨

## Creation Phase
- 컨텍스트를 **생성**하는 단계
- Variable Environment, Lexical Environment로 나뉨

### Variable Environment
- Leical Environment와 과정은 동일하나 `var` 만 저장
- **초기값**만 저장되어 있고 그 이후로 **변경되지 않음**

### Lexical Environment
- `let`, `const` 와 **함수 선언**을 저장
- Variable Environment의 **초기값을 복사**하여 생성됨
- 값이 바뀔 때마다 **최신 상황 반영**
- 환경 레코드 -> 외부 환경에 대한 참조 -> this 바인딩의 순서로 생성

### 환경 레코드 (Environment Record)
- **변수 객체**를 이용하여 선언된 변수, 함수를 저장
- 선언만 되고 값 할당이 되지 않았으므로 `undefined` 상태

#### Declarative Environment Record
- `var`, `let`, `const`, `function`, `import` 등 **선언**된 **정적**인 식별자들을 저장

#### Object Environment Record
- 전역 객체, `with` 등 **동적**인 **객체**를 저장
- `with`는 자바스크립트에서 사용을 권장하지 않음

#### 변수 객체 (Variable Object)
- 실행 컨텍스트의 종류에 따라 다름

    |컨텍스트|변수 객체|
    |:---:|:---:|
    |전역 실행 컨텍스트|**전역 객체** ( `window` (브라우저), `global` (노드) )|
    |함수 실행 컨텍스트|**활성 객체** (매개 변수와 인자 정보를 가지고 있음)|

### 외부 환경에 대한 참조 (Reference to the outer environment)
- `outer` 를 통해 부모 컨텍스트의 **스코프 체인**을 참조하여 스코프 체이닝이 가능하도록 함

#### 스코프 체인 (Scope Chain)
- 해당 변수 또는 함수를 **참조**하는 **객체들의 목록**
- 호출된 변수 또는 함수를 찾기 위해서 가장 내부의 함수의 스코프부터 시작하여 전역 실행 컨텍스트까지 상위로 한 단계씩 나가면서 찾음, 없으면 에러 발생

### `this` 바인딩 (`this` Binding)
- 함수의 호출 방법에 따라서 `this` 결정
- ES6에서는 Lexical Environment에 포함

## Execution Phase
- 코드를 위에서부터 내려가면서 변수에 값 **할당** 및 함수 **실행**하는 단계
- 사용되는 변수들은 변수 객체 안에서 값을 찾음
- 변수 객체 안에 없다면 스코프 체이닝을 통해 상위 객체로 올라가면서 찾음

## 전역 실행 컨텍스트
- 자바스크립트 코드가 **처음 실행**될 때 생성
- **전역 객체** 생성
- 코드 전체에 대한 정보를 가지고 있음
- 브라우저 페이지가 종료될 때까지 유지

## 함수 실행 컨텍스트
- 함수가 **호출**될 때 생성
- 함수 실행이 마무리되면 사라짐

## `eval()` 실행 컨텍스트
- `eval()` 함수가 실행될 때 생성
- `eval()` 함수는 자바스크립트에서 사용을 권장하지 않음

## 블록 실행 컨텍스트
- **블록 스코프**를 가진 객체가 실행될 때 생성
- ES6에서 추가
- 환경 레코드, 외부 환경에 대한 참조까지의 과정만 거치고 `this`는 자동으로 상위 객체로 지정됨

## 참고 사이트
- https://www.freecodecamp.org/news/how-javascript-works-behind-the-scene-javascript-execution-context/
- https://www.zerocho.com/category/JavaScript/post/5741d96d094da4986bc950a0
- https://www.zerocho.com/category/JavaScript/post/609778ad9f879900043a8728
- https://www.javascripttutorial.net/javascript-execution-context/
- https://meetup.nhncloud.com/posts/129
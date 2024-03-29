# 프로토타입 (Prototype)
- 자바스크립트에서 다른 언어의 `class` 대신 사용하기 위해 만들어진 개념
- 비슷한 객체의 공통적인 속성/메서드를 프로토타입을 이용하여 하나로 묶고 그 프로토타입을 **상속**하는 형태로 구현
- 프로토타입을 이용하여 생성된 객체는 따로 선언하지 않아도 프로토타입의 속성/메서드에 접근 및 호출할 수 있음
- `Object.prototype.속성 이름 = 값` 형식으로 프로토타입 정의 후에도 **속성/메서드를 추가 및 수정**할 수 있음
- 프로토타입이 변경되면 프로토타입을 이용하여 생성된 객체에도 **자동으로 변경 사항이 반영됨**
- 생성자 (`constructor`) 속성은 프로토타입의 **생성자 함수**를 가리킴
- 프로토타입 링크 (`__proto__`) 를 이용하여 프로토타입에 접근할 수 있으나 **표준이 아님** (많이 사용되어서 사실상 표준화된 경우)
- 프로토타입을 이용하여 생성된 객체에서 메서드를 호출한 경우, `this`는 해당 객체를 가리킴
- ES5부터 추가된 `Object.create(프로토타입 객체 이름)` 메서드로 프로토타입을 지정하여 객체를 생성할 수 있음
- ES6부터 추가된 `Object.getPrototypeOf(객체 이름)`, `Object.setPrototypeOf(객체 이름, 프로토타입 객체 이름)` 메서드로 프로토타입에 접근 가능

```javascript
function Person() { ... }

const Person1 = Object.create(Person); // new로 생성 후 prototype을 지정해주는 과정을 하나로 합친 것
Object.getPrototypeOf(Person1);

const Person2 = new Object();
Object.setPrototypeOf(Person2, Person);
Object.getPrototypeOf(Person2);
```

## 함수에서의 프로토타입
- 함수에서는 함수 객체의 프로토타입인 `Function.prototype` 을 가리키는 `__proto__` 외에도 **함수를 가진 객체의 프로토타입**을 가리키는 `prototype` 속성이 존재
- **화살표 함수는 프로토타입이 없음** -> 화살표 함수를 생성자 함수로 사용할 수 없음

## 내장 객체의 프로토타입
- `Array`, `Date`, `String` 등 자바스크립트에 내장되어 있는 객체의 프로토타입
- 모든 내장 객체의 프로토타입인 `Object.prototype`은 `null`
- 내장 객체 프로토타입의 속성/메서드도 추가 및 수정 가능하지만, 코드 전체에 영향이 갈 수 있으므로 **폴리필** 용도 외에는 사용하지 말아야 함
- 내장 객체가 원시 타입에게 메서드를 제공할 때 사용되는 **임시 래퍼 객체** 때문에, `null`과 `undefined`를 제외한 원시 타입에서도 추가 또는 수정한 속성/메서드를 사용할 수 있음
```javascript
String.prototype.concatWord = function (word) {
    return `${this} ${word}`;
}

// 임시 래퍼 객체 때문에 원시 타입 string에서 내장 객체 String의 프로토타입 메서드를 사용할 수 있음
const str = "hello";
str.concatWord("world");
"hi".concatWord("everyone");
```

## 프로토타입 체이닝 (Prototype Chaining)
- 속성/메서드가 호출된 객체에 해당 속성/메서드가 없다면 **프로토타입 링크**를 따라 **상위 프로토타입의 속성/메서드를 참조**하는 것
- 상위에 중복되는 속성/메서드가 있다면 **가장 가까운 쪽을 참조함**
- 거슬러 올라가다 `Object.prototype`, 즉 `null`을 만나면 해당 속성/메서드가 존재하지 않는다는 의미 -> `undefined`를 반환하고 종료됨
- 순환되는 형태의 참조는 허용되지 않음

## `class` 와의 차이점
- ES6부터 자바스크립트에도 `class` 가 추가됨
- 클래스가 추가되었다고 해서 자바스크립트가 클래스 기반 언어로 바뀐 것은 아님
- 함수와 같이 클래스 표현식에 이름을 붙일 수도 있고 안 붙일 수도 있음
- **재정의 불가능**
- `constructor()` 메서드를 이용하여 **생성자 초기화 동작을 정의**할 수 있으며, 클래스 내에 단 한 개만 존재할 수 있음
- 메서드 작성 시에는 `function` 등의 키워드 없이 작성
- 속성/메서드 앞에 `static` 키워드를 붙이면 클래스 밖에서 클래스로 호출 가능한 **정적 속성/메서드**를 만들 수 있음 (그러나 클래스를 이용하여 구현된 객체에서는 호출할 수 없음)
- `extends`로 다른 클래스를 **상속** 가능
- `super`로 **부모 클래스**를, `super()`로 **부모 클래스의 생성자**를 호출 가능 -> **오버라이딩** 가능


## 참고 사이트
- https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Object_prototypes
- https://developer.mozilla.org/ko/docs/Web/JavaScript/Inheritance_and_the_prototype_chain
- https://ko.javascript.info/prototypes
- https://www.programiz.com/javascript/prototype
- https://www.w3schools.com/js/js_object_prototypes.asp
- https://poiemaweb.com/js-prototype
- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classes
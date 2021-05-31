---
title: "JavaScript"
date: 2021-04-07
categories: [JavaScript]
comments: true
---

> 해당 포스팅은 [생활 코딩 자바스크립트 언어 - 함수 지향 유효 범위 파트](https://opentutorials.org/course/743/6495) 수강 후 강의 내용을 토대로 학습한 내용을 담고 있습니다. 😎
포스팅 내용에 대한 피드백은 언제나 환영입니다!

<br>

## 유효 범위 (Scope)
변수에 접근할 수 있는 **범위**
`
해당 강의에서는 '변수의 수명'이라고 설명해 주셨는데, 아마 범위에 따라 해당 변수의 접근 가능 여부가 달라져서 그런 것 같음 🤔
`

<br>
<hr>
<br>

### 유효 범위의 타입
- 전역 스코프 (Global scope): 전역에 선언되어 자바스크립트 애플리케이션 어느 곳에서든 접근 가능
- 지역 스코프 (Local scope): 해당 지역 한정 접근 가능, 지역을 벗어나면 접근 불가능
- 블록 스코프 (Block scope): 블록({}) 내에서 유효(참조, 접근) 가능한 스코프
- 함수 스코프 (Function scope): 함수 내에서 선언된 변수는 해당 함수 내에서만 유효하고 함수 외부에서는 유효하지 않음 (참조, 접근 불가능)
  - **자바스크립트는 함수 스코프를 따름**

<br>
<hr>
<br>

### 정적 스코프와 동적 스코프
- 정적 스코프(Static scope)
  - 렉시컬 스코프(Lexical scope)라고도 하며, 함수가 **선언**된 시점에서 유효 범위를 가짐
  - 대부분의 프로그래밍 언어와 자바스크립트도 정적 스코프를 따름
  - 전역 스코프, 블록 스코프, 함수 스코프에 적용됨

```js
// 예제 1
var i = 5; // 전역 변수

function a() {
  var i = 10; // 지역 변수
  b();
}
function b() {
  document.write(i);
}

a(); // 5 출력
```

> ❓ 예제 1에서 `a();`의 값으로 왜 5가 출력되나요?
→ 함수 a 호출 시 함수 a 내부에 있는 함수 b가 실행되는데, 이때 함수 b는 선언된 시점에서 변수명이 i인 지역 변수가 없어 변수명이 i인 전역 변수를 찾아 출력하기 때문에 5가 출력됩니다!

```js
// 예제 1-1
var num = 100;

function foo() {
  var num = 10;
  console.log('foo: ' + num);
  bar();
}
function bar() {
  console.log('bar: ' + num);
}

foo();
/*
  foo: 10
  bar: 100
*/
```

```js
// 예제 2
var a = 10,
    b = 20,
    c = 30;

function outerFunc() {
  var b = 200,
      c = 300;
  innerFunc();
}
function innerFunc() {
  var c = 3000;
  document.write('a: ' + a + '<br>');
  document.write('b: ' + b + '<br>');
  document.write('c: ' + c + '<br>');
}

outerFunc();
/*
  a: 10
  b: 20
  c: 3000
*/
```

```js
// 예제 2-1
var a = 10,
    b = 20,
    c = 30;

function outerFunc() {
  var b = 200,
      c = 300;

  function innerFunc() {
    var c = 3000;
    document.write('a: ' + a + '<br>');
    document.write('b: ' + b + '<br>');
    document.write('c: ' + c + '<br>');
  }
}

outerFunc();
/*
  a: 10
  b: 200
  c: 3000
*/
```

> ❓ `예제 2의 b 값`과 `예제 2-1의 b 값`이 다른 이유는 무엇인가요?
→ 내부 함수는 자신을 포함하고 있는 외부 함수의 변수에 접근할 수 있기 때문입니다!
<br>
예제 2의 innerFunc 함수 내에는 지역 변수 b가 존재하지 않아 전역 변수 b의 값인 20을 출력하고, 예제 2-1의 innerFunc 함수 내에는 지역 변수 b가 존재하지 않지만 innerFunc 함수를 포함하고 있는 외부 함수 outerFunc의 지역 변수 b가 존재함과 동시에 접근할 수 있으므로 200을 출력합니다.
<br>
📍 예제 2, 2-1은 [해당 강의 페이지](https://opentutorials.org/course/743/6495)에 '금도끼은도끼' 님이 남기신 예제를 기반으로 작성되었습니다.

- 동적 스코프(Dynamic Scope)
  - 함수가 **호출**된 시점에서 유효 범위를 가짐
  - 프로그램의 런타임이나 실행 컨텍스트, 호출 컨텍스트에 의해 결정되는 스코프

<br>
<hr>
<br>

### 유효 범위에 따른 변수

변수는 **선언 위치에 따라** 유효 범위를 가짐

- 전역 변수 (Global variables): 자바스크립트 내 어느 위치에서든 선언하여 자바스크립트 애플리케이션 전역에서 접근할 수 있는 변수
- 지역 변수 (Local variables): 변수가 선언된 해당 블록에서 선언하여 범위 내에서만 유효하게 사용할 수 있는 변수
  - 자바스크립트의 지역 변수는 **함수에서만 유효함**

> 📍 '왜 전역 변수로 써야 하는가?'에 대한 구체적인 이유를 인지하고 있지 못한 상태라면 **언제나 지역 변수를 사용**해야 함
여러 프로그램을 결합하다 보면 같은 이름의 변수를 다른 의미로 사용하는 경우가 생길 수 있기 때문 (이름의 충돌)

```js
// 예제 1
var vscope = 'global';

function fscope() {
  alert(vscope);
}

fscope(); // 변수 vscope는 전역 변수이기 때문에 'global' 출력
```

```js
// 예제 1-1
var vscope = 'global';

function fscope() {
  var vscope = 'local';
  alert(vscope);
}

fscope(); // fscope 내 선언된 vscope는 지역 변수이기 때문에 'local' 출력
```

> ❓ 예제 1-1은 왜 `fscope 내 선언된 지역 변수 vscope`가 출력되나요?
→ 전역 영역에서는 전역 변수만 참조가 가능하고, 함수 내 지역 영역에서는 전역 변수, 지역 변수 모두 참조 가능합니다. 이때 예제 2처럼 변수명이 중복된 경우는 함수 내에 있는 지역 변수를 우선으로 참조합니다!

```js
// 예제 2
var vscope = 'global';

function fscope() {
  var vscope = 'local',
      lv = 'local variables';
  alert(lv);
}

fscope(); // 'local variables' 출력
alert(lv); // Uncaught ReferenceError: lv is not defined
```

> ❓ 예제 2 중 마지막 행 `alert(lv);`는 왜 `Uncaught ReferenceError: lv is not defined`를 출력하나요?
→ fscope 함수 내에 선언된 지역 변수인 lv는 외부에서 접근이 불가능하기 때문입니다!

```js
// 예제 3
var vscope = 'global';

function fscope() {
  vscope = 'local';
}

alert(vscope); // 'local' 출력
```

```js
// 예제 3-1
var vscope = 'global';

function fscope() {
  var vscope = 'local';
}

alert(vscope); // 'global' 출력
```

> ❓ 예제 3과 예제 3-1의 출력값은 왜 다른가요?
→ 예제 3처럼 함수 내에서 변수 키워드를 생략하고 선언된 변수는 자동적으로 전역 변수로 선언되기 때문입니다!

```js
// 예제 3-2
var foo = function() {
  var a = 3,
      b = 5,
      bar = function() {
        var b = 7,
            c = 11;
        a += b + c;
      }
  console.log(a); // 3
  bar();
  console.log(a); // 21
}
foo();
```

> ❓ 예제 3-2 중 9행과 11행의 `console.log(a);`의 값이 다른 이유는 무엇인가요?
→ 함수 bar의 호출 여부 때문입니다!
9행은 함수 bar의 호출 전 a의 값으로 함수 foo의 지역 변수인 a의 값 3이 출력되고, 11행은 함수 bar의 호출 후 a의 값으로 함수 bar 내부에서 변수 키워드 없이 a가 `a += b + c;`로 선언되었기 때문에 3(a) + 7(b) + 11(c)로 21이 출력됩니다.

```js
// 예제 4
var vscope = 'global';

function fscope() {
  var vscope = 'local';
  vscope = 'local variables';
}

alert(vscope); // 'global' 출력
```

> ❓ 예제 4에서 변수 키워드 없이 `vscope`가 선언되었는데 왜 출력값은 `'global'`인가요?
→ 변수 키워드를 생략하고 선언되었다 하더라도 자바스크립트는 같은 함수 안에 이미 선언된 같은 이름의 지역 변수가 있는지 확인한 후, 존재한다면 그 지역 변수를 가리키기 때문입니다!

<br>
<hr>
<br>

### 최소한의 전역 변수 사용

자기 자신만 쓰는 전역 변수 하나만을 만들어놓고, 나머지 다른 전역 변수들은 그 전역 변수 객체의 소속으로 만들면 변수명이 충돌할 확률은 현저하게 낮아짐

```js
var MYAPP = {}; // 전역 변수, 변수의 값은 객체

MYAPP.calculator = {
  'left': null, // null: 프로그래머가 아직 값을 부여하지 않았다는 걸 명시적으로 지정함
  'right': null
}
MYAPP.coordinate = {
  'left': null,
  'right': null
}

MYAPP.calculator.left = 10;
MYAPP.coordinate.right = 20;

function sum() {
  return MYAPP.calculator.left + MYAPP.coordinate.right;
}
document.write(sum); // 30 출력
```

<br>
<hr>
<br>

### 즉시 실행 함수를 이용한 전역 변수 사용 억제

하나의 전역 변수도 사용하고 싶지 않을 때는 익명 함수를 사용하여 해당 함수를 바로 호출함

```js
(function() {
  var MYAPP = {}; // 익명 함수의 지역 변수가 됨

  MYAPP.calculator = {
    'left': null,
    'right': null
  }
  MYAPP.coordinate = {
    'left': null,
    'right': null
  }

  MYAPP.calculator.left = 10;
  MYAPP.coordinate.right = 20;

  function sum() {
    return MYAPP.calculator.left + MYAPP.coordinate.right;
  }
  document.write(sum());
})(); // 함수 바로 호출 -> 30 출력
```

<br>

> 참고 문서 📝
1. [생활 코딩](https://opentutorials.org/course/743/6495)
2. [모던 자바스크립트 입문](https://book.naver.com/bookdb/book_detail.nhn?bid=13447219)
3. [Poiemaweb 스코프](https://poiemaweb.com/js-scope)
4. [Songlog 님 블로그](https://iamsjy17.github.io/javascript/2019/06/08/js33_06_scope.html) - 정적 스코프, 동적 스코프 부분 개념과 예제

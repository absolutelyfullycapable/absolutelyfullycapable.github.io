---
title: "JavaScript 값으로서의 함수와 콜백 함수"
date: 2021-04-11
categories: [JavaScript]
comments: true
---

> 해당 포스팅은 [생활 코딩 자바스크립트 언어 - 함수 지향 값으로서의 함수와 콜백 파트](https://opentutorials.org/course/743/6495) 수강 후 강의 내용을 토대로 학습한 내용을 담고 있습니다. 😎
<br>
포스팅 내용에 대한 피드백은 언제나 환영입니다!

<br>

## 일급 객체 (First-class object)

- 컴퓨터 프로그래밍 언어 디자인에서 일급 객체는 **다른 객체들에게 일반적으로 적용 가능한 연산을 모두 지원하는 객체**임
- 이 연산에는 보통 매개 변수로 전달되고, 함수에서 반환되고 수정되고, 변수에 할당되는 작업이 포함됨

<br>

### 일급 객체의 조건

1. 변수나 데이터 구조 안에 담을 수 있다.
2. 매개 변수로 전달할 수 있다.
3. 리턴 값으로 사용할 수 있다.

→ 자바스크립트에서 함수는 위 세 조건을 모두 충족하여 일급 객체라고 할 수 있음

<br>
<hr>
<br>

## 값으로서의 함수

자바스크립트에서는 함수도 일급 객체, 일종의 **값**임
<br>
→ 거의 모든 언어가 함수를 가지고 있지만 자바스크립트의 함수가 다른 언어의 함수와 다른 점은 **함수 자체로 값**이 될 수 있다는 것임

<br>

### 1. 변수 안에 저장 가능

```js
function a() {}
```

위 함수는

```js
var a = function() {}
```

이렇게 풀어서 쓸 수 있음 (함수(값)를 `변수 a`에 저장한 것)

<br>
<hr>
<br>

### 2. 객체 안에 value로 저장 가능

```js
obj = {
  'first': function() {}
}
```

`obj`라는 객체 안에 `first`라는 속성이 담겨 있는데, 그 속성의 값이 함수일 때 그 함수를 **메소드(Method)**라고 함

<br>

```js
// 예제 1
calc = {
  'plus': function(a, b) {
    return a + b;
  },
  'minus': function(a, b) {
    return a - b;
  }
}
console.log(calc['plus'](1, 2)); // 3 출력
console.log(calc['minus'](2, 1)); // 1 출력
```

<br>

```js
// 예제 2
var movie = {
  name: '옥자',
  director: '봉준호',
  show: function() {
    console.log(this.name + ' ' + this.director);
  }
}
movie.show(); // 옥자 봉준호
```

<br>
<hr>
<br>

### 3. 다른 함수의 인자로 전달 가능 (콜백 함수)

```js
// 예제 1
function cal(func, num) {
  return func(num);
}

function increase(num) {
  return num + 1;
}
function decrease(num) {
  return num - 1;
}

alert(cal(increase, 1)); // 2
/*
  alert(function cal(increase, 1) {
    var func = increase(1) {
      return 1 + 1;
    }
    func(1); // 2
  });
*/
alert(cal(decrease, 1)); // 1
/*
  alert(function cal(decrease, 1) {
    var func = decrease(1) {
      return 1 - 1;
    }
    func(1); // 0
  });
*/
```

> ❓ 예제 1의 `cal 함수`는 어떻게 실행되나요?
<br>
→ 첫 번째 인자로 담긴 함수(func)를 호출하면서 두 번째 인자로 전달된 값(num)을 호출된 함수(func)의 인자로 전달합니다!

<br>
<hr>
<br>

### 4. 함수의 리턴 값으로 사용 가능

```js
// 예제 1
function cal(mode) {
  var func = {
    'plus': function(left, right) {
      return left + right;
    },
    'minus': function(left, right) {
      return left - right;
    }
  }
  return func[mode];
}

alert(cal(plus)(2, 1)); // 3
alert(cal(minus)(2, 1)); // 1
```

> ❓ 예제 1 중 `alert(cal(plus)(2, 1));`에서 `(2, 1)`은 어떤 매개 변수의 인자인가요?
<br>
→ 함수 func의 메소드의 매개 변수인 `left, right`의 인자입니다!
<br>
`cal(mode);` 함수가 실행되면 return 값으로 `func[mode];`를 출력합니다. 이때 `func[mode];`의 값은 메소드로 `left`와 `right`라는 매개 변수를 가지고 있습니다.

<br>
<hr>
<br>

### 5. 배열의 값으로 사용 가능

```js
var process = [
  function(input) { return input + 10; },
  function(input) { return input * input },
  function(input) { return input / 2 }
],
    input = 1;

for(var i = 0; i < process.length; i++) {
  input = process[i];
  /*
    i = 0일 때 input = 1 + 10 = 11,
    i = 1일 때 input = 11 * 11 = 121,
    i = 2일 때 input = 121 / 2 = 60.5
  */
}

alert(input); // 60.5 출력
```

<br>
<hr>
<br>

## 콜백 함수

자바스크립트에서 함수는 일급 객체로 일종의 값
이때 **함수는 값으로 다른 함수의 인자가 될 수 있는데**, 그 함수를 **콜백 함수**라 함

<br>

```js
// 예제 1: '배열 요소를 순서대로 정렬하고 싶어요!'
var numbers = [20, 8, 5, 3, 1, 2, 4, 6, 9, 7, 10];
```

`numbers` 배열을 내장(빌트인) 메소드인 `.sort()`를 통해서 순서대로 정렬할 수 있음

> ❓ 내장(빌트인) 메소드는 뭐예요?
<br>
→ 자바스크립트가 기본적으로 가지고 있으면서 사용자에게 제공하는 메소드입니다!

<br>

```js
var numbers = [20, 8, 5, 3, 1, 2, 4, 6, 9, 7, 10];
console.log(numbers.sort()); // [1, 10, 2, 20, 3, 4, 5, 6, 7, 8, 9] 출력
```

`.sort()` 메소드 사용 시 숫자는 암시적으로 문자열로 변환되기 때문에 1 다음에 10, 2 다음에 20이 오는 걸 알 수 있음
이때 콜백 함수를 사용하면 순서대로 정렬 가능함

> ❓ 왜 콜백 함수를 사용하면 순서대로 정렬이 가능한가요?
<br>
→ 기본적으로 `.sort()` 메소드는 인자로 함수를 받습니다. (콜백 함수!) 이때 인자로 받은 함수는 원소를 비교하고 무엇이 우선인지 판단하는 역할을 하기 때문입니다!

```js
var numbers = [20, 8, 5, 3, 1, 2, 4, 6, 9, 7, 10],
    sortFunc = function(a, b) {
      return a - b;
    }
console.log(numbers.sort(sortFunc)); // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 20] 출력
```

> ❓ `sortFunc 함수`는 왜 `a - b`를 리턴하나요?
<br>
→ `.sort()` 메소드는 **리턴값(음수, 0, 양수)으로 순서를 정하기 때문**입니다!
<br>
a에서 b를 뺀 값이 음수일 때는 `a < b로 a가 먼저` 옵니다. 0일 때는 `a = b로 서로에 대해 변경하지 않고 모든 다른 요소에 대해 정렬`합니다. 양수일 때는 `a > b로 b가 먼저` 옵니다.
<br>
동일한 방법으로 역순 정렬을 원할 때는 `b - a`를 리턴하면 되겠죠? 😎

<br>

> 참고 문서 📝
1. [생활 코딩](https://opentutorials.org/course/743/6508)
2. [Soeun/Sona Lee 님 블로그](https://soeunlee.medium.com/javascript%EC%97%90%EC%84%9C-%EC%99%9C-%ED%95%A8%EC%88%98%EA%B0%80-1%EA%B8%89-%EA%B0%9D%EC%B2%B4%EC%9D%BC%EA%B9%8C%EC%9A%94-cc6bd2a9ecac)
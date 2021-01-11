---
title: "JavaScript 함수 (2) 중첩 함수와 재귀 함수"
date: 2020-12-31
categories: [JavaScript]
comments: true
---

## **중첩 함수**

- 특정 함수의 내부에 선언된 함수
- C나 Java 등에서 사용 불가능, 자바스크립트에서 사용 가능
    - 자바스크립트에서는 외부 함수의 최상위 레벨에만 중첩 함수 작성 가능
    - 함수 안의 if문와 while문 등의 문장 블록 안에는 중첩 함수 작성 불가능
- 중첩 함수의 참조는 그 중첩 함수를 둘러싼 외부 함수의 지역 변수에 저장
    - 외부 함수의 바깥에서는 읽거나 쓰기 불가능
- **자신을 둘러싼 외부 함수의 인수와 지역 변수에 접근 가능**
    - 외부 함수의 변수 유효 범위가 그 함수의 중첩 함수에 미침 (클로저의 핵심 구성 요소)
        - 간단한 예시 1)의 중첩 함수 sumSquare는 변수 x 사용
        - 변수 x는 외부 함수인 example의 인수

<br>

- 간단한 예시

1) 배열 요소의 제곱합에 대한 제곱근을 구하는 함수

```js
function example(x) {
    var sum2 = sumSquare();
    return Math.sqrt(sum2); // Math.sqrt(x) -> x의 제곱근

    function sumSquare() {
        sum = 0;
        for(var i = 0; i<x.length; i++) {
            sum += x[i]*x[i];
        }
        return sum;
    }
}

var a = [2, 1, 3, 5, 7];
var n = example(a);
console.log(n); // -> 9.38083151964686
```

- - -

<br>

## **재귀 함수**

- 재귀 호출을 수행하는 함수
    - 재귀 호출: 함수가 자기 자신을 호출하는 행위

<br>

- 유의 사항
    1. 재귀 호출은 반드시 멈춰야 한다
        - 함수가 자신을 호출하면 무한한 연쇄 호출로 이어지므로 프로그램이 멈추지 않을 가능성이 있기 때문
    2. 재귀 호출로 문제를 간단하게 해결할 수 있을 때만 사용한다
        - 호출된 각각의 재귀 함수는 메모리의 다른 영역 사용 -> 호출된 횟수만큼 메모리 소비량 늘어남
        - 대부분 while문이나 for문으로 작성하는 게 이해하기 쉽고 공간도 적게 차지함

<br>

- 간단한 예시

1-1) n의 팩토리얼을 구하는 함수

```js
function fact(n) {
    if(n <= 1) {
        return 1;
    }
    return n*fact(n-1);
}

fact(5); // -> 120
```

<br>

1-2) 위 예제의 함수 fact를 함수 리터럴로 정의하려면 다음과 같이 함수 리터럴 표현식에 함수 이름을 적음 (함수 이름 f는 함수 안에서만 유효)

```js
var fact = function f(n) {
    if(n <= 1) {
        return 1;
    }
    return n*f(n-1);
}
```

<br>

1-3) **arguments.callee**를 사용하면 이름이 없는 익명 함수도 재귀 호출 가능 (arguments.callee -> 지금 실행 중인 함수 가리킴)

```js
var fact = function f(n) {
    if(n <= 1) {
        return 1;
    }
    return n*arguments.callee(n-1);
}
```
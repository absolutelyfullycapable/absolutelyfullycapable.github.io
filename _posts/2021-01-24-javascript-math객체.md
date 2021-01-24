---
title: "JavaScript Math 객체"
date: 2021-01-24
categories: [JavaScript]
comments: true
---

## **Math 객체**

- 수학에서 자주 사용하는 상수와 함수를 미리 구현한 자바스크립트 표준 내장 객체 (**함수 객체 아님**)
    - Math 객체의 모든 속성과 메서드는 정적임 (숫자를 수학적으로 다루거나 수학 상수를 제공)
- 다른 전역 객체와 달리 생성자가 존재하지 않음 (자바스크립트 기본 내장 객체 중 유일)
    - Math 객체의 모든 메서드나 프로퍼티 바로 사용 가능

<br>

- - -

<br>

### **· Math 객체의 프로퍼티**

- `Math.E` : 자연 로그의 밑수
- `Math.LN2` : 2의 자연 로그
- `Math.LN10` : 10의 자연 로그
- `Math.LOG2E` : 2를 밑으로 한 e의 로그
- `Math.LOG10E` : 10을 밑으로 한 e의 로그
- `Math.PI` : 원주율
- `Math.SQRT1_2` : 1/2의 제곱근
- `Math.SQRT2` : 2의 제곱근

<br>

### **· Math 객체의 메서드**

- 손쉬운 작업이 가능하도록 다양한 메서드들이 있지만 그 중에서도 가장 자주 쓰이는 대표적인 Math 메서드들
    - `Math.abs(x)` : x의 절댓값 (|x|)
    - `Math.ceil(x)` : x 이상의 최소 정수
    - `Math.floor(x)` : x 이하의 최대 정수
    - `Math.max(x, y)` : x와 y 중 큰 값
    - `Math.min(x,y)` : x와 y 중에서 작은 값
    - `Math.random()` : 0 이상 1 미만의 난수(특정한 순서나 규칙을 가지지 않는 수)
    - `Math.round(x)` : x의 반올림
    - `Math.sqrt(x)` : x의 제곱근

<br>

- - -

<br>

#### **· 간단한 예시**

1) 로또 번호 자동 생성기

```js
let lotto = "<h2>로또 번호 자동 생성기</h2>";
lotto += "<ul>";

// 임의의 수 6개 출력
for(i = 1; i <= 6; i++) {
    lotto += "<li>" + Math.ceil(Math.random()*45) + "</li>";
}

lotto += "</ul>";

document.write(lotto);
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbpMvNj%2FbtqUvDcKhvb%2FhONfKB91F7rCocdh0kG1e1%2Fimg.png)
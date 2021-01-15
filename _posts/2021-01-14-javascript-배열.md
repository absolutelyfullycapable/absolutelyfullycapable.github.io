---
title: "JavaScript 배열 (1)"
date: 2021-01-14
categories: [JavaScript]
comments: true
---

## **배열(Array)**

- 여러 개의 '데이터'를 담는 특별한 변수
- 인덱스 번호(요소 번호)로 관리
- 가변적임

<br>

- - -

<br>

### **· 배열 생성**

<br>

#### **1. 배열 리터럴로 생성하기**

- 배열 리터럴은 쉼표로 구분한 값을 대괄호([])로 묶어서 표현

- ex)

    ```js
    var evens = [2, 4, 6, 8]
    ```

    - **배열 리터럴**: [2, 4, 6, 8]
    - **배열 요소**: 배열 값 하나 (2, 4, 6, 8 하나하나)
    - **인덱스(요소 번호)**: 요소에 매긴 번호, 배열 요소 왼쪽부터 순서대로 0, 1, 2 ... 번호 매겨짐 (**인덱스 번호는 0부터 시작**)

<br>

```js
var arr1 = [1, 2, 3]; // 인덱스 0: 1, 인덱스 1: 2, 인덱스 2: 3
var arr2 = []; // 빈 배열 생성, 배열로서 초기화
var arr3 = [,,,,,] // 5개의 요소 없는 배열 생성
var arr4 = [1, "string", true, function(){}, arr1, null, undefined]; // 숫자, 문자열, 논리, 함수, 변수, null, undefined .. 등 모든 타입의 값이 올 수 있음

console.log(arr1[1]); // 배열 요소 중 인덱스 1 호출 -> 2
console.log(arr2[4]); // arr1 이름이 출력되는 게 아니라 arr1의 배열([1, 2, 3]) 출력됨

arr1[0] = "문자열"; // 변수 arr1의 인덱스 0의 숫자(1)를 "문자열"로 변경
console.log(arr1[3]); // 없는 배열 요소 -> undefined
```

- 자바스크립트의 배열은 객체 타입이므로 배열을 변수에 대입하면 배열의 참조가 변수에 저장됨
- 배열 리터럴 안에 어떠한 요소도 작성하지 않으면 빈 배열 생성됨
- 배열 리터럴 요소의 값을 생략하면 그 요소는 생성되지 않음

    ```js
	var a = [2, , 4];
    console.log(a); // [2, undefined, 4]
	```

    - undefined가 표시되어 있지만 실제로는 없음

<br>

#### **2. Array 생성자로 생성하기**

- ex)

```js
var evens = new Array(2, 4, 6, 8); // [2, 4, 6, 8] 생성
var empty = new Array(); // 빈 배열 생성, 배열로서 초기화
var five = new Array(5); // 5개의 요소 없는 배열 생성
var various = new Array(1, "string", true, function(){}, arr1, null, undefined);
```

- Array 생성자의 인수가 한 개고 그 값이 양의 정수면 의미 달라짐
    - 이때 인수는 **배열 길이**를 뜻하므로 배열이 그 길이만큼 생성됨

```js
var x = new Array(3);
console.log(x.length); // 3
```

- Array 생성자의 인수가 한 개고 그 값이 양의 정수가 아니면 오류 발생

    - ex)

    ```js
    var x = new Array(-3); // 오류 발생
    ```

<br>

- - -

<br>

### **· length 프로퍼티**

- 배열 길이 (자바스크립트에서는 배열의 요소의 개수를 뜻하지 않는 경우(희소 배열)가 있으므로 주의해야 함)
    - 배열 요소의 최대 인덱스 값 + 1
- length 프로퍼티에 현재의 배열 요소 개수보다 작고 0보다 큰 정수 값을 대입하면 배열 길이가 줄어듦
    - 배열의 앞쪽을 기준으로 그 배열 길이를 넘는 인덱스 번호에 할당된 배열 요소는 삭제됨

```js
var arr1 = [1, "two", 3];
console.log(arr1.length); // .length: 배열에 저장된 요소의 수 출력 -> 3
console.log(arr1[1].length); // 해당 인덱스 번호의 글자 수 출력 -> 3

var arr2 = ["a", "b", "c", "d"];
arr2.length = 2; // 배열의 앞쪽을 기준으로 2개 뒤로는 강제 삭제
console.log(arr2); // ["a", "b"]
```

- length 프로퍼티에 그 배열 길이보다 큰 정수 값을 대입하면 배열에 새로운 요소가 추가되지 않고 length 값만 바뀜

<br>

- - -

<br>

### **· 배열 요소의 추가, 삭제**

<br>

#### **1. 추가**

(1) 없는 배열 요소에 값 대입

```js
var a = ["A", "B", "C"];
a[3] = "D";
console.log(a); // ["A", "B", "C", "D"];
```

(2) push 메서드 사용 -> 요소의 끝에 추가

```js
var a = ["A", "B", "C"];
a.push("D");
console.log(a); // ["A", "B", "C", "D"];
```

<br>

#### **2. 삭제**

(1) delete 연산자 사용 -> 특정 배열 요소 삭제

- delete 연산자를 사용하여 배열 요소를 삭제해도 그 배열의 **length 값은 유지** (삭제한 요소만 사라짐)

```js
var a = ["A", "B", "C"];
delete a[1]; // a 배열의 인덱스 1 (두 번째 배열 요소) 삭제
console.log(a); // ["A", undefined, "C"]
console.log(a.length); // 3
```

(2) shift 메서드 사용 -> 배열의 첫 번째 요소 삭제

- **length 값 변경**

```js
var a = ["A", "B", "C"];
a.shift(); // "A" 삭제
console.log(a.length); // 2
```

(3) pop 메서드 사용 -> 배열의 마지막 요소 삭제

- **length 값 변경**

```js
var a = ["A", "B", "C"];
a.pop(); // "C" 삭제
console.log(a.length); // 2
```

<br>

- - -

<br>

### **· 희소 배열**

- 배열에 요소를 추가하거나 제거하여 배열 안 요소 위치가 연속적이지 않은 배열
- ex)

    ```js
    var a = ["A", "B", "C"];
    a[4] = "E";
    console.log(a); // ["A", "B", "C", undefined, "E"];
    console.log(a.length); // 5 (length 프로퍼티가 배열 요소의 개수를 뜻하지 않는 경우)
    ```

    - undefined라고 표시된 요소는 실제로 없는 요소

<br>

- - -

<br>

### **· 자바스크립트 배열은 Array 객체**

- 배열에 대괄호 연산자를 사용하는 것은 객체에 대괄호 연산자를 사용하는 것과 마찬가지
- 배열의 요소 번호로 숫자 값 대신 문자열 사용 가능

    ```js
    var a = ["A", "B", "C"];
    console.log(a["2"]); // C
    ```

- 없는 배열 요소를 읽으려고 하면 undefined 반환

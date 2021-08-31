---
title: "JavaScript 배열 (1)"
date: 2021-01-14
categories: [JavaScript]
comments: true
---

## **배열(Array)**

- 연관된 여러 개의 데이터를 모아서 통으로 관리하기 위해 사용하는 데이터 타입 (데이터들을 담는 그릇이라고 할 수 있음)
	- 데이터를 담는다는 의미에서 변수와 비슷하지만 변수는 하나의 데이터를 저장, 배열은 여러 개의 데이터를 저장함
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
    - **인덱스(색인, 요소 번호)**: 요소에 매긴 번호, 배열 요소 왼쪽부터 순서대로 0, 1, 2 ... 번호 매겨짐 (**인덱스 번호는 0부터 시작**)

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
var empty = new Array(); // 빈 배열 생성, 배열로서 초기화
var evens = new Array(2, 4, 6, 8); // [2, 4, 6, 8] 생성
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

- 배열 안에 담겨 있는 원소가 몇 개인지 나타냄 (그러나.. 자바스크립트에서는 배열의 요소의 개수를 뜻하지 않는 경우(희소 배열)도 있으므로 주의해야 함)
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

```js
var arr3 = [1, 2];
arr3.length = 4;
console.log(arr3);
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FTfF0S%2Fbtq0SGaONqz%2F3sdV8TUGK58ThIRD8Z8sz0%2Fimg.png)

<br>

- - -

<br>

### **· 배열 요소의 추가, 삭제, 정렬**

<br>

#### **1. 추가**

(1) 없는 배열 요소에 값 대입

```js
var a = ["A", "B", "C"];
a[3] = "D";
console.log(a); // ["A", "B", "C", "D"];
```

(2) .unshift(): 배열의 시작 지점에 원소를 추가하는 메소드, 인덱스 바뀜

```js
var a = [3, 4, 5];
a.unshift(1, 2);
console.log(a); // [1, 2, 3, 4, 5]
```

(3) .push(): 배열의 끝에 하나의 원소를 추가하는 메소드

```js
var a = ["A", "B", "C"];
a.push("D");
console.log(a); // ["A", "B", "C", "D"];
```

(4) .concat(): 배열의 끝에 메소드에 담겨 있는 배열을 연결해서 하나의 배열로 만들고 리턴하는 메소드

```js
var a = ["A", "B", "C"];
a = a.concat(["D", "E"]);
console.log(a); // ["A", "B", "C", "D", "E"];
```

<br>

#### **2. 삭제**

(1) delete 연산자: 특정 배열 요소 삭제 / **length 값은 유지** (삭제한 요소만 사라짐)

```js
var a = ["A", "B", "C"];
delete a[1]; // a 배열의 인덱스 1 (두 번째 배열 요소) 삭제
console.log(a); // ["A", undefined, "C"]
console.log(a.length); // 3
```

(2) .shift(): 배열의 첫 번째 요소 삭제 / **length 값 변경**

```js
var a = ["A", "B", "C"];
a.shift(); // "A" 삭제
console.log(a.length); // 2
```

(3) .pop(): 배열의 마지막 요소 삭제 / **length 값 변경**

```js
var a = ["A", "B", "C"];
a.pop(); // "C" 삭제
console.log(a.length); // 2
```

<br>

#### **3. 정렬**

(1) .sort(): 배열의 요소를 알파벳 순서대로 정렬시키는 메소드

```js
var a = ["d", "a", "c", "e", "b"];
a.sort();
console.log(a); // ["a", "b", "c", "d", "e"]

var b = [11, 9, 10, 7, 4, 3, 1, 5, 2, 6, 8, 12];
b.sort();
console.log(b); // [1, 10, 11, 12, 2, 3, 4, 5, 6, 7, 8, 9] -> 숫자의 경우 암시적으로 문자열로 변환시키기 때문에 숫자 10이 숫자 1 뒤에 나옴
```

(2) .reverse(): 배열 요소 순서를 반전 시킴 (첫 번째 요소는 마지막 요소로, 마지막 요소는 첫 번째 요소로)

```js
var a = ["d", "a", "c", "e", "b"];
a.reverse();
console.log(a); // ["b", "e", "c", "a", "d"]

var b = [1, 2, 3, 4, 5];
b.reversr();
console.log(b); // [5, 4, 3, 2, 1]
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

<br>

- - -

<br>

### **· 반복문과 결합했을 때 진가를 보이는 배열**

- 반복문으로 배열에 담긴 정보를 하나씩 꺼내서 처리할 수 있기 때문!
- ex) 배열에 담긴 값을 대문자로 출력하는 프로그램

    ```js
    function members() {
    	return ['jh', 'dk', 'boo', 'mg'];
    }
    svt = members();
    for(var i = 0; i < svt.length; i++) { // .length 덕분에 반복문이 동작하는 횟수는 배열에 담겨 있는 원소들의 개수에 따라 탄력적으로 바뀜 -> 배열에 담겨 있는 원소들이 달라져도 오류 없이 실행 가능!
    	document.write(svt[i].toUpperCase() + '<br>'); // .toUpperCase(): 대문자 변환
    }
    ```

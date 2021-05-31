---
title: "JavaScript 명시적 타입 변환"
date: 2020-09-04
categories: [JavaScript]
comments: true
---

## **명시적 타입 변환**

<br>

### **1. 숫자를 문자열로 변환**

<br>

- 숫자 + 문자열
	- 숫자와 문자열을 + 연산자로 연결하면 숫자의 타입이 문자열로 바뀜

    ```js
	ex1) 10 + "cookies"; // "10cookies"
	ex2) 100 + ""; // "100" : 숫자에 빈 문자열을 더해 숫자를 문자열로 바꿀 수 있음
	```

    <br>

- Number 객체의 메서드 활용
	- toString: 숫자를 문자열로 변환
	- toLocaleString: 숫자를 지역화된 문자열로 변환
	- toFixed: 숫자의 소수점 아래 자릿수를 지정한 문자열로 변환
	- toExponential: 숫자의 소수점 아래 자릿수를 지정한 문자열로 변환하되 지수와 함께 표시
	- toPrecision: 숫자를 유효 숫자가 지정된 문자열로 변환, 유효 숫자가 정수부의 자릿수보다 작을 때는 지수로 표시
	<br>

    ```js
	var a = 26;
    a.toString(); // 26 >> 인수를 지정하지 않으면 10진수 문자열로 변환
    a.toString(2); // 11010 >> 2진수 문자열로 변환

    var b = 1234.567;
    b.toString(); // 56
    b.toFixed(0); // 1234
    b.toFixed(2); // 1234.57
    b.toFixed(4); // 1234.5670
    b.toExponential(3); // 1.235e+3
	b.toPrecision(3); // 1.23e+3
    ```

    <br>

- **String 함수 활용**
	- String 생성자 앞에 new를 붙이지 않으면 일반적인 함수로 활용 가능
	- 이때 String 함수 반환값은 String 객체가 아닌 문자열
	- **String 함수에는 모든 데이터 타입을 문자열로 바꾸는 기능이 있음**
	<br>

	```js
	const a = "합계", b = 234, c = 654;
    console.log(a + (b + c)); // 합계888
	console.log(a + (String(b) + String(c))); // 합계234654
    ```
	<br>

- - - -

<br>

### **2. 문자열을 숫자로 변환**

<br>

- 수식 안에서 묵시적으로 변환

	```js
	var a = 2;
    a - 0; // 첫 번째 방법
    +a; // 두 번째 방법
    ```
	<br>

- parselnt와 parseFloat 함수 사용
	- parselnt: 문자열을 정수로 바꿈
	- parseFloat: 문자열을 부동소수점으로 바꿈
	- 두 함수 모두 **첫 번째 문자를 숫자로 바꾼 값으로 반환, 이후 등장하는 문자열은 무시**
	<br>

	```js
	parselnt("3.14"); // 3
    parselnt("3.14 meters"); // 3 : 숫자 다음에 오는 문자열은 무시
    parseFloat("3.14"); // 3.14
    parseFloat("3.14 meters"); // 3.14 : 숫자 다음에 오는 문자열은 무시
    parselnt(".5"); // NaN : 문자열 앞에 "."이 있으므로 해석하지 않음
    parselnt("abc"); // NaN : 숫자로 인식할 수 없음

    parselnt("101",2); // 5 : 문자열을 2진수로 해석해서 변환
    parselnt("ff", 16); // 255 : 문자열을 16진수로 해석해서 변환
    ```

    <br>

- **Number 함수를 활용하는 방법**
	- Number 생성자 앞에 new를 붙이지 않으면 일반적인 함수로 활용 가능
	- 이때 Number 함수 반환값은 Number 객체가 아닌 숫자
	- **Number 함수에는 모든 데이터 타입을 숫자로 바꾸는 기능이 있음**
	<br>

	```js
	Number(true); // 1
    Number(false); // 0
    Number(NaN); // NaN
    Number(undefined); // NaN
    Number(null); // 0

	const a = "234", b = "335", c = "문자";
   	const total = Number(a) + Number(b) + Number(c);
    console.log(total); // NaN
    ```
	<br>

- - - -

<br>

### **3. 논리값으로 변환**

<br>

- !!a
	- ! 연산자는 논리 타입이 아닌 값의 타입을 논치 타입으로 바꿈
	- !를 하나 더 붙여서 참과 거짓을 뒤바꾸고 있음
- Boolean(a)
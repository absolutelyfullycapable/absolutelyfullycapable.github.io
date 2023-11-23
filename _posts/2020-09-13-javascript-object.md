---
title: "JavaScript 객체의 기초와 객체 생성 방법"
date: 2020-09-13
categories: [JavaScript]
comments: true
---

### **객체 (Object)**

-  데이터 여러 개를 하나로 모은 복합 데이터
	- 배열과 비슷하지만 배열과는 다르게 인덱스를 문자 혹은 우리가 직접 원하는 데이터로 지정 가능 (가시적인 차이점)
-  변수와 함수(속성, 이벤트, 메소드)가 모여 만든 변형 가능한 속성들의 집합 -> 하나의 단위로 구조화할 수 있어 유용 
-  자바스크립트 객체는 크게 네이티브 객체, 호스트 객체, 사용자 정의 객체로 나뉘어짐
	- **네이티브 객체(Native  Object), 코어 객체(Core Object)**: ECMAScript 사양에 정의된 객체
	    - 내장 생성자 객체(Object, String, Number, Boolean, Array, Function...), JSON, Math, Reflect 등
	- **호스트 객체(Host Object)**: ECMAScript에는 정의되어 있지 않지만 자바스크립트 실행 환경에 정의된 객체 -> 운영 체제, 웹 브라우저마다 달라짐
	    - BOM 객체(Browser Object Model(브라우저 객체): Window, Navigator, History, Location, Screen, Document...), DOM 객체(Document Object Model(문서 객체 모델)), XMLHttpRequest 객체, HTML5의 각종 API...
	- **사용자 정의 객체(User-defined Object)**: 사용자가 정의한 자바스크립트 코드를 실행한 결과로 생성된 객체

<br>

### **프로퍼티 (Property)**

- 객체에 포함된 데이터 하나(이름과 값의 쌍)
- 프로퍼티에 저장된 값이 함수일 경우, 일반 함수와 구분하기 위해 그 프로퍼티를 메소드(method)라 부름
- 프로퍼티는 프로퍼티 키(이름)와 프로퍼티 값으로 구성됨
	- 프로퍼티는 유일하게 프로퍼티 키로 식별할 수 있음 (프로퍼티 키는 프로퍼티를 식별하기 위한 식별자)
	- 프로퍼티 키는 빈 문자열을 포함하는 모든 문자열 또는 symbol 값으로 작성함
		- 문자열, symbol 값 이외의 값을 지정하면 암묵적으로 **문자열**로 변환됨
		- 프로퍼티 키 중복 선언 시 나중에 작성된 프로퍼티 키 값으로 적용됨
	- 프로퍼티 값에는 모든 형태의 데이터 올 수 있음
		- 이미 존재하는 프로퍼티 키에 새로운 값 부여하면 해당 프로퍼티 값은 새로운 값으로 변경됨
- 배열과 다르게 객체는 프로퍼티 열거 시 순서를 보장하지 않음

<br>

### **메소드 (Method)**

- 객체에 소속된 프로퍼티의 값으로 함수를 지정할 수 있음 (객체에 소속된 함수를 만들 수 있다는 뜻)
	- 객체에 소속된 그 함수가 **메소드**
- 객체에 제한되어 있음

<br>
- - -
<br>

### **자바스크립트로 객체 생성하기**

<br>

#### **1. 객체 리터럴로 객체 생성하기**

- ex)  `card = {suit: "하트", rank: "A"};`
	- {...} : **객체 리터럴**
	- 객체 리터럴을 변수 card에 대입한 것
	- 객체가 생성되면 객체 내부에는 속성과 값이 존재
	- **프로퍼티 이름(key): 프로터티 값(value)** ('콜론(:)'으로 구분)
	- 프로퍼티 값에는 모든 데이터 타입의 값과 표현식 대입 가능
	- 중괄호 안에 있는 프로퍼티들은 **쉼표(,)**로 구분

<br>

- 변수에 대입된 객체 안의 프로퍼티 값을 읽거나 쓸 때는 **마침표 연산자** 또는 **대괄호 연산자** 사용 (객체 접근)
	- 마침표(.) 연산자: 프로퍼티 이름, 즉 식별자만 사용 가능
	    - obj.name = "이름"; -> 객체명.속성(프로퍼티 이름) = 값(프로퍼티 값)
	    - `.`: 객체에 접근하는 오퍼레이터 (object access operator)

    ```js
    card.suit // >> 하트
    ```

    <br>

	- 대괄호([]) 연산자: 프로퍼티 이름 또는 문자열 반환하는 표현식 사용 가능

    ```js
    card["rank"] // >> A
    ```

<br>

- 객체에 없는 프로퍼티를 읽으려고 시도하면 undefined 반환됨

```js
card.color // >> undefined
```

<br>


- 객체 리터럴 안에 어떠한 프로퍼티도 작성하지 않으면 빈 객체 생성됨
- 객체 타입의 값을 변수에 대입하면 그 변수에는 객체의 참조(메모리에서의 위치)가 저장됨
	- 이때 변수의 상태를 **그 객체를 참조하고 있다**라고 함

<br>

#### **2. 생성자로 객체 생성하기**

`const obj = new Object();`

- **생성자**: new 연산자로 객체를 생성할 것이라 기대하고 만든 함수
- 생성자로 객체를 생성할 때는 **new 연산자** 사용 (빈 객체 생성됨)
	- 생성자 안에서 **this.프로퍼티 이름**에 값을 대입하면 그 이름을 가진 프로퍼티에 값이 할당된 객체 생성됨
- **메소드 함수 안에서 this 사용하면 그 값이 생성자와 new 연산자로 생성한 객체의 프로퍼티임을 명시 가능**

	```js
	const person = new Object();

	person.name = 'Ji Hye';
	person.gender = 'female';
	person.sayHello = function () {
	    console.log('Hi! My name is ' + this.name);
	};

	console.log(person); // {name: "Ji Hye", gender: "female", sayHello: ƒ}
	person.sayHello(); // Hi! My name is Ji Hye
	```

- 객체를 생성하고 초기화하는 역할을 함
- 생성자 인수값이 null이거나 undefined면 빈 객체 반환

	```js
	const obj1 = new Object(null);
	const obj2 = new Object(undefined);
	// 둘 다 빈 객체 반환
	```

- **특수한 상황이 아니라면 객체 리터럴 방식을 사용하는 것이 일반적**
	- 자바스크립트 엔진은 객체 리터럴로 객체를 생성하는 코드를 만나면 내부적으로 Object 생성자 함수를 사용하여 객체를 생성하기 때문에 굳이 생성자로 객체를 생성하지 않아도 됨
- 생성자에는 보통의 객체처럼 속성을 추가할 수 없음

	```js
	const a = new Object();

	a.name = "jihye";
	console.log(a); // { name: "jihye" }
	```

	```js
	const a = new Object;

	Object.name = "jihye";
	console.log(a); // {}
	```

<br>

#### **3. 생성자 함수로 생성하기**

- 생성자 함수: 객체를 생성하는 함수
- 생성자 함수를 통해 생성된 객체를 인스턴스(instance)라고 함
- 객체를 생성하기 위한 템플릿처럼 사용 -> 프로퍼티 값만 다른 여러 개의 객체를 생성할 때의 불편함 보완 가능
- 생성자 함수 이름은 보통 파스칼 표기법 따름 (일반 함수와 생성자 함수를 구분하기 위해) 
- 생성자 함수 내에서 선언된 일반 변수는 내수에서는 자유롭게 접근이 가능하지만 외부 참조는 불가능

{% include codepen.html hash="OJdZxmB" title="생성자 함수로 객체 생성하기 예시" %}

<br>
- - -
<br>

### **프로퍼티 추가와 삭제**

- 자바스크립트의 객체는 실행 중에 프로퍼티를 자유롭게 추가하거나 삭제할 수 있음
- 없는 프로퍼티 이름에 값을 대입하면 새로운 프로퍼티 추가됨

```js
card.value = 14;
console.log(card); // >> Object {suit:"하트", rank:"A", value:14}
```

<br>

- 간단한 예시

```js
let obj = {};
obj.name = "이름";
obj.age = "나이";

document.write("객체 obj의 name 속성은 " + obj.name + "<br>");
document.write("객체 obj의 age property는 " + obj.age + "<br>");
console.log(obj);
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbCL1IB%2Fbtq03vlPkdj%2F8EsLCS9kTmb2k57KGFSuy1%2Fimg.png)
<a class="jsbin-embed" href="https://jsbin.com/wopubawuzi/embed?js,console,output">JS Bin on jsbin.com</a><script src="https://static.jsbin.com/js/embed.min.js?4.1.8"></script>

<br>

```js
let address = {
    "이름" : "홍길동",
    "주소" : "서울특별시"
};

address.우편번호 = 1550; // 객체 속성 추가

console.log(address.이름);
console.log(address.주소);
console.log(address.우편번호);

address["연락처"] = "010-1234-5678"; // 객체 속성 추가
console.log(address.연락처);
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbfJbOq%2FbtqM4zg101Y%2FM5Is3YeZxgCMMWm7kKP10k%2Fimg.png)

<br>

- delete 연산자를 사용하면 프로퍼티 삭제 가능
    - 이때 피연산자는 **프로퍼티 키**여야 함

```js
const person = {
    "first-name": "Ung-mo",
    "last-name": "Lee",
    gender: 'male',
};

delete person.gender;
console.log(person.gender); // undefined

delete person;
console.log(person); // Object {first-name: 'Ung-mo', last-name: 'Lee'}
```

<br>
- - -
<br>

### **in 연산자**로 프로퍼티 확인

- 작성 방법: 프로퍼티 이름을 뜻하는 문자열 **in** 객체명

```js
var card = {suit:"하트", rank:"A"};
console.log("suit" in card); // >> 프로퍼티가 객체에 포함되어 있을 때는 true 반환
console.log("color" in card); // >> 프로퍼티가 객체에 포함되어 있지 않을 때는 false 반환
```

<br>

- **in 연산자가 조사하는 대상은 그 객체가 가진 프로퍼티와 그 객체가 상속받은 모든 프로퍼티**

<br>
- - -
<br>

#### **내장 객체**

- 자바스크립트에서는 처음부터 사용할 수 있는 내장 객체(빌트인 오브젝트)가 마련되어 있음
- 내장 생성자
	- Object, String, Number, Boolean, Array, Date, Function ...
- Date 생성자
	- 날짜와 시간을 표현하는 객체 생성

		`const now = new Date();`

		- .getFullYear() : 연도를 뜻하는 숫자값
		- .getMonth(); : 월을 뜻하는 숫자값, 0부터 시작
		- .getDay(); : 요일을 뜻하는 숫자값, 0(일요일)부터 시작
		- .getDate(); : 날짜를 뜻하는 숫자값
		- .getHours(); : 시각의 시간을 뜻하는 숫자값
		- .getMinutes(); : 시각의 분을 뜻하는 숫자값
		- .getSeconds(); : 시각의 초를 뜻하는 숫자값
		- .getMilliseconds(); : 시각의 밀리초를 뜻하는 숫자값
		- now.toString(); : 현재 날짜와 시간을 문자열로 나타냄
		- now.toLocaleString(); : 지역화된 날짜와 시간 정보
		- now.toLocaleDateString(); : 지역화된 날짜 정보
		- now.toLocaleTimeString(); : 지역화된 시간 정보
		- .getUTCHours(); : UTC 시각의 시간을 뜻하는 숫자값
		- now.toUTCSting(); : UTC 날짜와 시간 정보
- Function 생성자
	- 함수를 생성하는 내장 생성자
	- const 변수 이름 = new Function(첫 번째 인수, ..., n 번째 인수, 함수 몸통);
	- **Function 생성자로 생성한 함수는 전역 변수와 자신의 지역 변수만 읽고 쓸 수 있다는 단점이 있어 함수를 동적으로 생성해야 하는 특별한 상황 외는 사용 안 함**
- 기타 내장 객체
	- 전역 객체: 프로그램 어디서나 사용할 수 있는 객체
		- 전역 객체의 프로퍼티
			- 전역 프로퍼티: undefined, NaN, Infinity
			- 생성자: Object(), String(), Number() ...
			- 전역 함수: parseInt(), parseFloat(), isNaN() ...
			- 내장 객체: Math, JSON, Reflect
	- JSON: JSON을 처리하는 기능을 제공
	- Math: 수학적인 함수와 상수를 제공
	- Reflect: 프로그램의 흐름을 가로채는 기능을 제공

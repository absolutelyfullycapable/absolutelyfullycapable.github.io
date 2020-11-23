---

layout: post

title: "JavaScript 객체의 기초와 객체 생성 방법"

description: "객체에 대한 기본적인 것들과 객체 생성 방법에 대해 알아보자"

date: 2020-09-13

tags: JavaScript 객체

comments: true

---





**객체**

-  데이터 여러 개를 하나로 모은 복합 데이터
-  변수와 함수(속성, 이벤트, 매서드)가 모여 만든 변형 가능한 속성들의 집합
-  자바스크립트 객체는 크게 네이티브 객체, 호스트 객체, 사용자 정의 객체로 나뉘어짐
	- **네이티브 객체(Native  Object), 코어 객체(Core Object)**: ECMAScript 사양에 정의된 객체
	    - 내장 생성자 객체(Object, String, Number, Boolean, Array, Function...), JSON, Math, Reflect 등

    <br>

	- **호스트 객체(Host Object)**: ECMAScript에는 정의되어 있지 않지만 자바스크립트 실행 환경에 정의된 객체 -> 운영 체제, 웹 브라우저마다 달라짐
	    - BOM 객체(Browser Object Model(브라우저 객체): Window, Navigator, History, Location, Screen, Document...), DOM 객체(Document Object Model(문서 객체 모델)), XMLHttpRequest 객체, HTML5의 각종 API...

    <br>

	- **사용자 정의 객체(User-defined Object)**: 사용자가 정의한 자바스크립트 코드를 실행한 결과로 생성된 객체

<br>

**프로퍼티**

- 객체에 포함된 데이터 하나(이름과 값의 쌍)

<br>
- - -
<br>

### **자바스크립트로 객체 생성하기**

<br>

##### **1. 객체 리터럴로 객체 생성하기**

- ex) var card = {suit: "하트", rank: "A"};
	- {...} : **객체 리터럴**
	- 객체 리터럴을 변수 card에 대입한 것
	- 객체가 생성되면 객체 내부에는 속성(프로퍼티)와 값이 존재
	- **프로퍼티 이름 (키):프로터티 값** ('콜론(:)'으로 구분)
	- 프로퍼티 값에는 모든 데이터 타입의 값과 표현식 대입 가능
	- 중괄호 안에 있는 프로퍼티들은 **쉼표(,)**로 구분

<br>

- 변수에 대입된 객체 안의 프로퍼티 값을 읽거나 쓸 때는 **마침표 연산자** 또는 **대괄호 연산자** 사용 (객체 접근)
	- 마침표(.) 연산자: 프로퍼티 이름, 즉 식별자만 사용 가능
	    - obj.name = "이름"; -> 객체명.속성(프로퍼티) = 값

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

- 프로퍼티 추가와 삭제
	- 자바스크립트의 객체는 실행 중에 프로퍼티를 자유롭게 추가하거나 삭제할 수 있음
	- 없는 프로퍼티 이름에 값을 대입하면 새로운 프로퍼티 추가됨

    ```js
	card.value = 14;
    console.log(card); // >> Object {suit:"하트", rank:"A", value:14}
    ```

	<br>

    - delete 연산자를 사용하면 프로퍼티 삭제 가능

    ```js
	delete card.rank;
    console.log(card); // >> Object {suit:"하트", value:14}
    ```

<br>

- 간단한 예시

```js
let obj = {};
obj.name = "이름";
obj.age = "나이";

document.write("객체 obj의 name 속성은 " + obj.name + "<br>");
document.write("객체 obj의 age property은 " + obj.age + "<br>");
document.write(obj);
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbtFTFb%2FbtqM5UEZWaT%2F9v2oI2gzB6zWgrEc5y5Dd0%2Fimg.png)

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
- - -
<br>

- **in 연산자**로 프로퍼티 확인
	- 프로퍼티 이름을 뜻하는 문자열 **in** 객체명

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

- 매서드
	- 프로퍼티에 저장된 값의 타입이 함수일 때 그 프로퍼티를 매서드라고 부름

<br>
- - -
<br>

##### **2. 생성자로 객체 생성하기**
- **생성자**: new 연산자로 객체를 생성할 것이라 기대하고 만든 함수
- 생성자로 객체를 생성할 때는 **new 연산자** 사용
- 객체를 생성하고 초기화하는 역할을 함
- 생성자 이름은 보통 파스칼 표기법 따름
- 생성자 안에서 **this.프로퍼티 이름**에 값을 대입하면 그 이름을 가진 프로퍼티에 값이 할당된 객체 생성됨
- 매서드 함수 안에서 this 사용하면 그 값이 인스턴트(생성자와 new 연산자로 생성한 객체)의 프로퍼티임을 명시 가능

<br>
- - -
<br>

##### **3. 내장 객체**

- 자바스크립트에서는 처음부터 사용할 수 있는 내장 객체(빌트인 오브젝트)가 마련되어 있음

<br>

- 내장 생성자
	- Object, String, Number, Boolean, Array, Date, Function ...

<br>

- Date 생성자
	- 날짜와 시간을 표현하는 객체 생성

		```js
        var now = new Date();
        ```

		- .getFullYear() : 연도를 뜻하는 숫자값
		- .getMonth(); : 월을 뜻하는 숫자값, 0부터 시작
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

<br>

- Function 생성자
	- 함수를 생성하는 내장 생성자
	- var 변수 이름 = new Function(첫 번째 인수, ..., n 번째 인수, 함수 몸통);
	- **Function 생성자로 생성한 함수는 전역 변수와 자신의 지역 변수만 읽고 쓸 수 있다는 단점이 있어 함수를 동적으로 생성해야 하는 특별한 상황 외는 사용 안 함**

<br>

- 기타 내장 객체
	- 전역 객체: 프로그램 어디서나 사용할 수 있는 객체
		- 전역 객체의 프로퍼티
			- 전역 프로퍼티: undefined, NaN, Infinity
			- 생성자: Object(), String(), Number() ...
			- 전역 함수: parseInt(), parseFloat(), isNaN() ...
			- 내장 객체: Math, JSON, Reflect

	<br>

	- JSON: JSON을 처리하는 기능을 제공
	- Math: 수학적인 함수와 상수를 제공
	- Reflect: 프로그램의 흐름을 가로채는 기능을 제공
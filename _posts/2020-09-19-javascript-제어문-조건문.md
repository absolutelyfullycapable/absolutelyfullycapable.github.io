---

layout: post

title: "Javascript 제어문 (1) 조건문"

description: "제어문 중 조건문에 대해 알아보자"

date: 2020-09-19

tags: javascript 제어문 조건문

comments: true

---





**순차적 실행**
- 문장은 일반적으로 위에서부터 아래 방향으로 작성된 순서로 실행

<br/>

### **제어문**
- 프로그램 실행 과정을 제어하기 위해, 즉 순차적 실행 흐름을 변화시키기 위해 쓰이는 문장
- 반복 처리 및 선택 처리를 할 때 사용
- 제어문에 사용하는 모든 문자는 **소문자**

<br/>

#### **제어문의 종류**
- 조건문
	- 조건에 따라 다음 문장을 선택적으로 실행함

	- `if문, if~else문, 다중 if~else문, switch~case문, try/catch/finally문`

- 반복문
	- 동일한 명령을 여러 번 처리하거나 특정 연산을 반복적으로 처리

	- `for문, for~in문, for~of문, while문, do~while문`


- 보조 제어문 (점프문)
	- 조건문을 만나면 건너뛰거나 반복 수행 종료 (반복문 내에서 사용)

	- `continue문, break문, return문, throw문`

<br/>
<br/>
- - -
<br/>

### **조건문**

#### **1. if문**

- 주어진 조건에 따라 참(true)과 거짓(false)으로 나눔
- 조건식이 참인 경우에만 블록 내의 문장 처리, 거짓이면 블록을 빠져나감
	- if 조건문은 조건의 값이 참인 경우 실행되기 때문에 거짓의 조건(0, null, "", undefined)에서는 실행되지 않음
- 조건식에 true 값을 직접 대입하면 무조건 처리하도록 제어할 수 있음
- 조건식에 false 값을 쓰면 블록 내 문장은 영원히 처리 불가능
- if문 안에 또 다른 if문 포함하여 작성 가능 (중첩된 if문)

<br/>

##### **· 작성 방법**

```js
// 1. 기본 작성
if(조건식) { // 조건식이 참인 경우
	실행 문장; // 실행하라
}


//2. 중첩된 if문
if(조건식 A) {
	실행 문장 1;
	if (조건식 B) {
		실행 문장 2;
	}
}
```

<br/>
<br/>

##### **· 간단한 예시**

1)

```js
if(111 < 100) {// 조건이 거짓이면
alert('참입니다.'); // 실행되지 않음
}

if(0) {// 조건이 거짓이면 (0 == false)
alert('참입니다.'); // 실행되지 않음
}

if(1) {// 1 == true -> 조건이 참이면
alert('참입니다.'); // 실행됨
}

const num = 100;
if(num > 99) {// 조건이 참이면
	alert(num + '은 99보다 큽니다.'); // 실행됨
}
if(num != 99) {// 조건이 참이면
	alert(num + '와/과 99는 같지 않습니다.'); // 실행됨
}
```

<br/>

2) if 조건문은 조건의 값이 참인 경우 실행되기 때문에 거짓의 조건(0, null, "", undefined)에서는 실행되지 않음

```js
let num1 = 0;
if(num1) {// 0 == false
	alert(num1); // 실행 안 됨
}

let num2 = null;
if(num2) {// null == false
	alert('null'); // 실행 안 됨
}

let num3 = "";
if(num3) {// "" == false
	alert('num3'); // 실행 안 됨
}

let num4 = undefined;
if(num4) {// undefined == false
	alert('num4'); // 실행 안 됨
}
```

<br/>

3) 입력창에 하루 걸음수를 입력 받아 6000보 이상인 경우 '좋은 습관을 가지고 있습니다.' 출력

```js
const walk = prompt('하루 걸음수를 입력해 주세요.','이곳에 작성해 주세요.'); // prompt를 변수 walk에 저장
if(walk >= 6000) {
	alert('좋은 습관을 가지고 있습니다.'); // 출력
}
if(walk < 6000) {
	alert('조금 더 걸어 보세요.');
}
```

<br/>
<br/>
- - -
<br/>

#### **1-1. if~else문**
- 조건식이 참(true)인 경우와 거짓(false)인 경우 처리할 문장이 각각 따로 있을 때 사용하는 제어문
	- 조건의 만족 여부에 따라 처리할 작업 선택
- "만약 ~이라면... (if) 그렇지 않으면... (else)"이라는 식의 처리 흐름 표현
- if~else문도 다른 if~else문을 포함하여 작성 가능 (중첩된 if~else문)
<br/>

##### **· 작성 방법**

```js
if(조건식) {
    실행 문장 1;
} else {
    실행 문장 2;
}
```

   <br/>
   <br/>

##### **· 간단한 예시**

1) 나이가 19세 이상이면 성인, 미만이면 미성년자로 구분하는 프로그램

```js
if(age >= 19) { // age가 19보다 같거나 크다
	result="성인입니다.";
} else { // age가 19보다 작다
	result="미성년자입니다."
}
```

<br/>

2) 주어진 변숫값을 판별하여 남자/여자, 성인/미성년자를 구분하는 프로그램

```js
var gender = "M" // 남자(M), 여자(F)
var age = 21;

if(gender == "M") { // 남자일 때
	if(age >= 19) { // 남자 성인일 때
		result="남자 성인입니다.";
	} else { // 남자 미성년자일 때
		result="남자 미성년자입니다.";
	}
} else { // 여자일 때
	if(age >= 19) { // 여자 성인일 때
		result="여자 성인입니다."
	} else { // 여자 미성년자일 때
		result="여자 미성년자입니다."
	}
}
```

<br/>

3) 특정 년도가 윤년인지 아닌지 판정하는 함수 (윤년은 4로 나누어떨어지고, 100으로는 나누어떨어지지 않지만 400으로는 나누어떨어지는 해)

```js
function isLeapYear(year) {
	if((year % 400 == 0) || (year % 4 == 0) && (year % 100 != 0)) {
		return true;
	}
	return false;
}
```

<br/>

4) 로그인 (아이디: admin, 패스워드: 123456)

```js
id = prompt('아이디 입력');

if(id == 'admin') { // 아이디 일치 시
	password = prompt('비밀번호를 입력');

	if (password === "123456") { // 아이디 일치, 비밀번호 일치 시
		location.href="login.html" // 로그인 완료 화면으로 이동
        // location.href=""; : "" 안의 주소로 이동
	} else { // 아이디 일치, 비밀번호 불일치 시
		location.href="error.html" // 에러 화면으로 이동
	}
} else { // 아이디 불일치 시
	location.href="error.html" // 에러 화면으로 이동
}
```

<br/>
<br/>
- - -
<br/>

#### **1-2. 다중 if~else문**
- 여러 조건을 체크해야 할 때 사용

<br/>

##### **· 작성 방법**

```js
if(조건식 A) { // 조건식 A가 참인 경우
	실행 문장 1; // 실행 문장 1을 실행하라
} else if(조건식 B) { // 조건식 B가 참인 경우
	실행 문장 2; // 실행 문장 2를 실행하라
} else { // 조건식 A와 조건식 B가 모두 거짓일 경우
	실행 문장 3; // 실행 문장 3을 실행하라
}
```

<br/>
<br/>
- - -
<br/>

#### **2. switch~case문**

- if~else의 단점(마지막 else문에 도달할 때까지 모든 조건식을 체크, 다중 선택이 많아져 코드 복잡해짐)을 보완하기 위해 사용하는 다중 선택문
- 조건문을 체크하여 다음에 처리할 문장의 위치를 파악한 후 해당 문장으로 가서 바로 처리
	- 특정 값과 비교하여 참인 경우 실행
- 간결하게 표현 가능
- 범위값 지정 가능

<br/>

##### **· 작성 방법**

```js
switch(상수값(비교값)) {
    case 수치나 문자 1 (비교할 값 1):
    	실행 문장 A;
        break;
    case 수치나 문자 2 (비교할 값 2):
    	실행 문장 B;
        break;
   	...
    default:
    	실행 문장 C;
}
```


1) 괄호 안에 들어 있는 표현식을 평가<br/>
2) 평가한 값과 일치하는 case 표현식(라벨의 값)을 위에서부터 아래 방향으로 찾음

<br/>

- **switch(상수값(비교값))**
	- 상수값으로 수치 또는 문자 사용
	- 다음에 처리할 문장이 몇 번째 case문에 해당하는지 표시

<br/>

- **case 수치나 문자(case 라벨의 값) ~ default**
	- case 뒤에 수치나 문자를 작성하고 마지막에는 꼭 **:**(콜론) 붙임
		- 표현식으로 작성하지 않음

		- ``case 표현식 1:``

	- case에 해당하는 경우 없으면 마지막 default문 실행
		- default문에는 어떤 case문에도 해당하지 않는 경우 처리할 문장 작성
	- default 문장 생략 가능
	- deafault는 else와 같은 역할
	- default는 switch 불록 어느 위치에 있어도 문법 오류가 발생하지 않지만, 블록 중간에 있으면 프로그램을 이해하기 어려워 되도록이면 마지막에 작성하도록 함

<br/>

- **break**
	- 해당 case문의 문장을 처리하고 구문을 벗어난 (정지) 후 다음 작업을 시작함
	- case 표현식 다음에 이어지는 실행문의 마지막에는 일반적으로 break 문 넣음
		- 사용하지 않으면 다음 표현식에 등장하는 전체 문장을 실행
	- 함수 끝에 switch문을 사용하면 break문 대신 return문을 사용해도 무방함

   <br/>
   <br/>

##### **· 간단한 예시**

1) n이 1일 때는 One, 2일 때는 Two, 3일 때는 Three, 그 외에는 Other 출력

```js
switch(n) {
    case 1:
    	console.log("One");
        break;
    case 2;
    	console.log("Two");
        break;
    case 3;
    	consolor.log("Three");
        break;
    default:
    	console.log("Other");
}
```

<br>

2)

```js
let num = prompt("1~4까지의 숫자 중 하나만 작성하세요.");
num = Number(num);

switch (num) {// 비교값에는 숫자, 문자열, 변수 등등이 들어갈 수 없다.
	case 1:
		alert("숫자 1입니다.");
		break;
	case 2:
		alert("숫자 2입니다.");
		break;
	case 3:
		alert("숫자 3입니다.");
		break;
	case 4:
		alert("숫자 4입니다.");
		break;
	default:
		alert("1~4까지의 번호만 입력해 주세요.")
}
```
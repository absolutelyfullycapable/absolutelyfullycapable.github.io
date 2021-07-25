---
title: "JavaScript 연산자"
date: 2020-09-03
categories: [JavaScript]
comments: true
---

## **연산자 (Operator)**

- 연산의 대상인 피연산자에게 연산 명령을 내리기 위해 사용하는 기호 (어떠한 작업을 컴퓨터에게 지시하기 위한 기호)
- 하나 이상의 표현식을 대상으로 산술, 할당, 비교, 논리, 타입 연산 등을 수행해 하나의 값을 만듦

<br>
- - -
<br>

## **1. 문자열 연산자 (연결 연산자)**

- `+` 기호를 사용하여 문자열을 연결시키는 기능을 함

    ```js
    var a = "Hello " + "Javascript"; // >> Hello Javascript 출력
    ```

<br>

- 산술 연산자 기호와 똑같기 때문에 주의해야 함

    ```js
    var a = "100" + 10; // >> 10010 출력
    var b = 100 + 10; // >> 110 출력
    ```

<br>
- - -
<br>

## **2. 산술 연산자**

- 사칙 연산의 방식을 따르고 수행하는 연산자
- 피연산자는 숫자
- **더하기 연산자를 제외한 다른 연산자는 문자열 데이터를 연산할 수 없음**
- **더하기 연산자를 제외한 다른 연산자는 숫자형 문자열의 경우 숫자로 자동 변환하여 연산함**
- 왼쪽에서 오른쪽으로 순차적으로 연산

    ```js
    a = 50, b = 40, c = 20;
    console.log(a - b + c); // 50-40+20 >> 30
    ```

<br>

- 곱하기, 나누기 연산자가 먼저 연산되고 더하기, 나누기 연산자는 나중에 연산

    ```js
    console.log(a - b / c); // 40 / 20 >> 2, 50-2 -> 48
    ```
<br>

- 괄호 안을 먼저 연산 후 나머지 연산

    ```js
    console.log( (a-b)/c ); //(50-40) >> 10, 10 / 20 >> 0.5
    ```
<br>

- 계산할 수 없는 경우는 NaN로 평가
	- 산술 연산자의 피연산자가 true면 1, false나 null이면 0, undefined면 NaN로 평가함
<br>

- **산술 연산 특이**

    ```js
    console.log(0/0); // NaN
    console.log(true + true - false); // true (1), false (0) -> 2
    console.log(1 + null); // 1 + 0 (null은 연산에서 0) -> 1
    console.log(1 + ""); // 1 + 0 (빈 문자열 경우에도 0으로 자동 변환) -> 1
    console.log(1 + undefined); // NaN (undefined는 변환되지 않음)
    ```

<br>
- - - -
<br>

- 2-1. **산술 이항 연산자**

	<br>

	- **더하기 연산자**: `+` 기호 사용

	    ```js
	    num = 11 + 22; // 숫자 11 + 숫자 22 >> 숫자 33
        num = "11" + 22; // 문자열 11 + 숫자 22 >> 문자 1122
    	num = 11 + "22"; // 숫자 11 + 문자 22 >> 문자 1122
    	num = "오늘은 " + "즐거운 " + "목요일입니다."; // 문자열 + 문자열 + 문자열 >> 문자열
	    ```

	- **빼기 연산자**: `-` 기호 사용

	    ```js
	    num = 11 - 22; // 숫자 11 - 숫자 22 >> 숫자 -11
    	num = "11" - 22; // 문자열 11 - 숫자 22 >> 숫자 -11 (숫자 문자열의 경우 숫자로 자동 변환되어 계산함)
    	num = "오늘은 " - "즐거운 " - "목요일입니다."; // 문자열 - 문자열 - 문자열 >> NaN (Not a Number)
	    ```

	- **곱하기 연산자**: `*` 기호 사용

	    ```js
	    num = 11 * 22; // 숫자 11 * 숫자 22 >> 숫자 242
        num = "11" * 22; // 문자열 11 * 숫자 22 >> 숫자 242 (숫자 문자열의 경우 숫자로 자동 변환되어 계산함)
    	num = "11" * "22"; // 문자열 11 * 문자열 22 >> 숫자 242 (숫자 문자열의 경우 숫자로 자동 변환되어 계산함)
    	num = "오늘은 " * "즐거운 " * "목요일입니다."; // 문자열 * 문자열 * 문자열 >> NaN (Not a Number)
	    ```

	- **나누기 연산자**: `/` 기호 사용

	    ```js
	    num = 11 / 22; // 숫자 11 / 숫자 22 >> 숫자 0.5
    	num = "11" / 22; // 문자열 / 숫자 >> 숫자 0.5 (숫자 문자열의 경우 숫자로 자동 계산되어 계산됨)
    	num = "11" / "22"; // 문자열 / 문자열 >> 숫자 0.5 (숫자 문자열의 경우 숫자로 자동 계산되어 계산됨)
	    ```

	- **나눈 후 나머지값 연산자**: `%` 기호 사용

	    ```js
	    modulus = 6 % 3; // 0
    	modulus = 5 % 3; // 2
    	modulus = 3 % 3; // 0
    	modulus = 2 % 3; // 2
    	modulus = 1 % 3; // 1
    	modulus = 0 % 3; // 0
	    
	    console.log(12 % 5); // 12를 5로 나누면 값은 2고 나머지 값은 2
	    console.log(10 % 7); // 10을 7로 나누면 값은 1이고 나머지 값은 3
	    console.log(1 % 5); // 1을 5로 나누면 값은 0이고 나머지 값은 1
	    console.log(4 % 3 + 1); // 사칙 연산의 법칙에 따라 나머지 값이 먼저 연산되므로 4를 3으로 나누면 나머지 값은 1, 1 + 1 -> 2
	    ```

<br>
- - -
<br>

#### 간단한 예시

```js
const a = 11 + 22 + '의 합은?'; // 숫자 + 숫자 + 문자열 >> (숫자 + 숫자) + 문자열 >> 33의 합은?
const b = '다음 수의 합은? ' + 11 + 22; // 문자열 + 숫자 + 숫자 >> 다음 수의 합은? 1122
```

<br>
- - -
<br>

- 2-2. **증감 연산자**
	- `++`, `--` 기호 사용
	- 변수값을 1씩 증가시키거나 감소시킴
	- 전위 증가 연산자 (`++a`): 변수를 불러오기 전에 1 증가 후 출력
	- 후위 증가 연산자 (`a++`): 변수를 먼저 출력 후 1 증가
	- 전위 감소 연산자 (`--a`): 변수를 불러오기 전에 1 감소 후 출력
	- 후위 감소 연산자 (`a--`): 변수를 먼저 출력 후 1 감소

	    ```js
	    let a = 10, b = 20;

	    console.log(a); // 10
	    console.log(a++); // 10(11) >> 변수 a를 출력 후 증가, 출력값은 10이지만 실질값은 11
	    console.log(a); // 11

	    console.log(b); // 20
	    console.log(++b); // 21 >> 변수 b를 불러오기 전에 증가시킨 후 출력
	    console.log(b); // 21
	    ```

	- 증감 연산자를 연속으로 사용하면 참조 오류 발생

	    ```js
	    (a++)++; // >> 참조 오류
	    ```


<br>
- - -
<br>

- 2-3. 산술 대입 연산자
	- 대입 연산자와 산술 이항 연산자를 조합한 연산을 좀 더 간략하게 표기한 것 (shortcut)
	- = 기호를 사용하여 값이나 변수를 할당하는 연산
	- = 기호를 기준으로 우변의 숫자만큼 연산하여 좌변의 변수에 **'새로운 값으로 갱신'**하는 것

	    ```js
        a += b; -> a + b -> a; a와 b를 더한 후 a에 새로운 값으로 갱신
        ```
	<br>

    - 기호
        - `+=` : 더하기 대입
        - `-=` : 빼기 대입
        - `*=` : 곱하기 대입
        - `/=` : 나누기 대입
        - `%=` : 나눈 후 나머지값 대입

    <br>

    - 예시

    ```js
    let a = 4;

    a += 3; // 기존 선언된 변수 a의 값(4)에 더하기 3을 한 후 좌변의 변수 a에 갱신.
    // a(4) + 3 -> 7 -> a

    a += 3; // a(7) + 3 -> 10 -> a
    a += 10; // a(10) + 10 -> 20 -> a
    a += 5; // a(20) + 5 -> 25 -> a

    a -= 3; // a(25) - 3 -> 22 -> a
    a *= 2; // a(22) * 2 -> 44 -> a
    a /= 4; // a(44) / 4 -> 11 -> a
    a %= 3; // a(11) % 3 -> 2 -> a
    ```

    <br>

    ```js
    let b = 10;

    b += 5; // 10 + 5 -> 15
    b += 4; // 15 + 4 -> 19
    b *= 5; // 19 * 5 -> 95
    b %= 5; // 95 % 5 -> 0
    ```

    <br>
    <br>

    - 활용 예제

    <br>

- html5
- CSS3
- javascript

<br>

위와 같은 목록 형식도 대입 연산자를 활용하여 만들기 가능

```js
window.onload = function(){ // 문서 준비 이벤트
    let list = ""; // 변수를 빈 문자열로 초기화

    list += "<ul>"; // "" + <ul> -> <ul>
    list += "    <li>HTML5</li>"; // <ul> + <li>html5></li> -> <ul><li>html5</li>
    list += "    <li>CSS3</li>"; // <ul><li>html5</li> + <li>CSS3</li> -> <ul><li>html5</li><li>CSS3</li>
    list += "    <li>Javascript</li>"; // <ul><li>html5</li><li>CSS3</li> + <li>javascript</li> -> <ul><li>html5</li><li>CSS3</li><li>javascript</li>
    list += "</ul>"; // <ul><li>html5</li><li>CSS3</li><li>javascript</li> + </ul> -> <ul><li>html5</li><li>CSS3</li><li>javascript</li></ul>

    document.body.innerHTML = list; // 문서 노드 안의 바디노드 안에 html 구조를 작성
}
```

<br>
- - -
<br>

## **3. 비교 연산자 (관계 연산자)**

- 두 개 이상의 피연산자의 값을 비교하여 참(true, 1) 또는 거짓(false, 0)값을 반환
- 주로 조건문에서 많이 사용됨
- 좌항 기준
- 기호
	- `>` : 우항보다 크다
	- `<` : 우항보다 작다
	- `==` : 우항과 같다 (동등 연산자: equal operator)
	- `===` : 우항과 값, 타입이 모두 같다 (엄격한 비교값, 일치 연산자: strict equal operator)
		- 실제 프로그래밍에서는 데이터 타입이 다른 것은 다른 데이터기 때문에 동등 연산자보다는 일치 연산자를 쓰는 것을 추천! 🌟
		- 큰 프로젝트에서 비슷한 것을 같은 것으로 처리하는 문법은 에러로 심각한 결과를 초래할 수 있기 때문에 좋은 거라고는 할 수 없음
	- `>=` : 우항보다 크거나 같다
	- `<=` : 우항보다 작거나 같다
	- `!=` : 우항과 같지 않다

        ```js
        let i;
        i = 5 < 4; // ~보다 작다. 좌항(5)은 우항(4)보다 작다. 거짓 == false == 0
        i = 5 > 4; // ~보다 크다. 좌항(5)은 우항(4)보다 크다. 참 == true == 1
        i = 5 == 4; // 같다. 좌항(5)과 우항(4)은 같다. false
	    i = 4 === 4; // 값과 타입이 모두 같다. (엄격한 비교값) 좌항(4)과 우항(4)의 값과 타입이 모두 같다. true
        i = 5 != 4; // 같지 않다. 좌항(5)과 우항(4)은 같지 않다. true
	    i = 5 <= 4; // 작거나 같다. 좌항(5)은 우항(4)보다 작거나 같다. false
        i = 5 >= 4; // 크거나 같다. 좌항(5)은 우항(4)보다 크거나 같다. true

        console.log(40 > 25 > 10); // false. 좌항 기준으로 차례대로 비교함
        // (40 > 25) 비교한 값 -> true
        // true(1) > 10 -> false

        console.log(1 == true); // true
        console.log('345' == 345); // 숫자형 문자를 자동 변환해서 비교하기 때문에 true
	```

<br>

- 비교 연산 특이

    ```js
    console.log(0 == false); // true
    console.log(0 === false); // false
    console.log("" == false); // true
    console.log("" === false); // false
    console.log("" == 0); // true
    console.log("" === 0); // false
    
    console.log("" == null); // false -> null은 변수에 데이터로 null이 저장되어 있는 경우나 변수에 저장된 데이터를 비우고자 할 때 사용
    console.log("" == undefined); // false -> undifined는 변수에 아무 값도 등록되어 있지 않은 경우로 변수 초기값

    console.log(null == undefined); // true
    console.log(null === undefined); // false
    // 둘 다 똑같이 값이 없는 상태지만 undefined는 프로그래머가 의도하지 않은 상황, null은 프로그래머가 현재 값이 없다는 것을 의도적으로 지정한 상황
    
    console.log(NaN === NaN); // false -> NaN는 자신과 일치하지 않는 유일한 값
    ```

<br>
- - -
<br>

- **숫자형 문자열끼리 비교 시 문자열 타입을 그대로 가지고 있되 눈에 보이지 않지만 비교 시에 숫자로 자동 변환됨**

	<br>

- **숫자와 숫자형 문자열 비교 시에도 숫자형 문자열은 문자열 타입을 그대로 가지고 있되 눈에 보이지 않지만 비교 시에 숫자로 자동 변환됨**

	<br>

    ```js
    console.log('15' > '12'); // 숫자형 문자열은 자동 변환되어 비교되기 때문에 true
    console.log(15 > '12'); // 숫자형 문자열은 자동 변환되어 비교되기 때문에 true
    console.log('015' > '10'); // 0이 앞에 오면 문자형으로 비교되어 0이 1보다 작으니까 false
    console.log('korea' > 'america'); // true. ( 11 (k) > 1 (a) )
    console.log('한글' > '영어'); // true. ( ㅎ (14) > ㅇ (8) )
    console.log('한글' > 'zoo'); // true. 다른 언어 비교 시에는 언어마다 우선 순위가 있음

    console.log('1234' == 1234); // true. '문자열' == 숫자 데이터
    console.log('1234' === 1234 ); // false. === -> 데이터 형태까지 완전히 같다. (엄격한 비교값)
    console.log('' === 0); // false.
    console.log(NaN === NaN); // false.  NaN(Not a Number: 숫자가 아님, 계산할 수 없음)만큼은 NaN를 포함한 모든 값과 같지 않다고 판정함

    console.log('' !== 0); // true. !== -> 데이터 형태까지 완전히 같지 않다.
    ```

- - -

- 변수는 데이터 값을 저장하는 공간으로 메모리에 저장해놓고 필요할 때 꺼내 쓰는 역할을 함
- 그러다 보니 다양한 조건에서 다르게 리턴되는 경우가 있음

    ```js
    var a = [1, 2, 3];
    var b = [1, 2, 3];
    console.log(a == b); // >> 각 배열에 같은 데이터가 담겨 있지만 메모리에서 차지하는 위치, 즉 저장 위치가 달라 false
    ```

<br>
- - -
<br>

## **4. 논리 연산자**

- 주어진 조건을 논리적으로 연산하여 피연산자 값 반환
- 두 개 이상의 값을 비교
- 기호
	- 논리곱 연산자: &&
	    - 연산 순서
	    	1. 가장 왼쪽 피연산자부터 확인하며 **falsy** 값 찾음
	    	2. falsy 값 발견 시 작동 멈추고 그 값을 반환
	    	3. 피연산자에서 falsy 값 발견 못 했을 때는 마지막 피연산자 값을 반환
	    - falsy 값 (falsy 값을 제외한 모든 값은 truthy 값)
	    	<br>
	    	```0, -0, false, "", '', ``, undefined, null, NaN```
	    - **논리합 연산자보다 우선 순위 높음**
	    
            ```js
	    const a = 10, b = 20;
	    console.log(a >= 10 && b == 20); // true
	    console.log(a > 10 && b == 20); // false
	    
	    console.log(false && 10); // false
	    console.log('abc' && null); // null
	    
	    console.log([] || 'happy' && null); // []
	    ```

	<br>

	- 논리합 연산자: `||`
	    - 연산 순서
	    	1. 가장 왼쪽 피연산자부터 확인하며 **truthy** 값 찾음
	    	2. truthy 값 발견 시 작동 멈추고 그 값을 반환
	    	3. 피연산자에서 truthy 값을 발견 못 했을 때는 마지막 피연산자 값을 반환

            ```js
            const a = 10, b = 20;
            console.log(a > 10 || b == 20); // true
	    
	    console.log('def' || 0); // 'def'
	    console.log("" || undefined); // undefined
            ```

	<br>

	- 논리 부정 연산자: !
	    - !A 조건 : A 조건이 아니면 true

            ```js
            const a = 10, b = 20;
            console.log(b == 10); // false
            console.log(!(b == 10)); // 상수 b는 10과 같지 않지 않기 때문에 true
            console.log(!(a == 10)); // 상수 a는 10과 같지 않다는 게 맞지 않기 때문에 false
            ```

<br>
- - -
<br>

## **5. 삼항 조건 연산자**

- 조건식을 판별하여 참(true)이냐 거짓(false)이냐에 따라 다음 문장을 선택적으로 실행하는 연산자
- 첫 번째 피연산자를 조건식으로 평가한 후 그 결과가 참(true)이면 두 번째 피연산자 값으로 삼고, 거짓(false)이면 세 번째 피연산자를 값으로 삼음
- 예시 1: 변수 a와 b의 값을 비교하여 a > b가 참이면 a, 거짓이면 b를 변수 c에 대입하는 수식

    ```js
    var a = 10, b = 20,
	c = (a > b) ? a : b;
    console.log(c); // 20
    ```
    
- 예시 2: x가 짝수이면 '짝수'를, 홀수이면 '홀수'를 반환

    ```js
    var x = 10,
        result = (x % 2) ? '홀수' : '짝수'; // x % 2는 0, 0은 false로 암묵적 타입 변환됨 
    console.log(result); // 짝수
    ```

<br>
- - -
<br>

## **6. typeof 연산자**

- typeof 뒤에 위치한 피연산자의 데이터 타입을 **문자열**로 반환
- typeof가 반환하는 문자열은 7 개의 데이터 타입과 일치하지 않음
    - "string", "number", "boolean", "undefined", "symbol", "object", "function" 중 하나를 반환
    - "null"은 반환하지 않음


```js
typeof ''; // "string"
typeof 1; // "number"
typeof NaN; // "number"
typeof true; // "boolean"
typeof undefined; // "undefined"
typeof Symbol(); // "symbol"
typeof null; // "object" -> 자바스크립트의 첫 번째 버전에서 이렇게 설계된 것을 현재의 버전에 반영하지 못하고 있기 때문
typeof []; // "object"
typeof {}; // "object"
typeof new Date(); // "object"
typeof function() {}; // "function"

// null 타입을 확인할 때는 일치 연산자(===) 사용
var n = null;
console.log(typeof n === null); // false
console.log(n === null); // true
```

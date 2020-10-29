---

layout: post

title: "Javascript 제어문 (2) 반복문"

description: "제어문 중 반복문에 대해 알아보자"

date: 2020-10-27

tags: javascript 제어문 반복문

comments: true

---





### **반복문**

- 동일한 명령을 여러 번 처리하거나 특정 연산을 반복적으로 처리
	- 일정한 처리를 한 다음 원래 위치로 돌아가 똑같은 처리를 반복하는 처리
- 반복문의 공통 작업
	1. 반복 조건의 초기화 작업
	2. 반복문의 조건식
	3. 반복 작업이 하나 끝났을 때 반복 조건을 갱신하는 작업


<br/>

#### **1. for 반복문**

- 반복 횟수에 중점을 둠
- 조건이 만족되는 동안 반복 실행
- 반복문의 공통 작업을 명시적으로 한 곳(소괄호 안)에 모아서 표기
	- 어떤 반복 처리를 하는지 이해하기 쉬움
	- 반복 조건의 포기화 작업과 갱신 작업을 빠뜨리는 등의 실수 사전 방지 가능
- for 반복문 안에 break 문, continue 문 사용 가능

<br/>

##### **· 작성 방법**

```js
// 1. 기본 작성
for(초기화식; 조건식; 반복식;) {
    실행 문장
}
```

- 초기화식: 반복 변숫값 초기화, for문이 처음 시작할 때 단 한 번만 실행됨
	- 초기화식 입력하는 부분에는 변수 선언 가능
		- **루프 카운터 변수**: 반복식 안에서 값이 바뀌는 변수
	- 쉼표 연산자를 사용하면 표현식 여러 개 작성 가능 (ex. for(var i = 1, sum = 0; ...)) 
- 조건식: 블록 내 문장을 얼마나 반복할지 결정, 조건식이 참인 동안 반복
- 증감식: 초기화식에서 초기화한 변수의 값을 증가 또는 감소시킴

<br/>

- 초기화식, 조건식, 반복식은 모두 생략 가능
	- 조건식을 생략하면 끝없이 반복하겠다는 의미
	- 특정 조건을 만족하면 for 반복문을 빠져나올 수 있도록 break문을 써 주어야 함
- **소괄호 안에 있는 세미콜론은 생략 불가능**

<br/>

##### **· for 반복문의 처리 흐름**

1. 반복문을 시작하기 전에 초기화식 단 한 번 실행
2. 조건식 먼저 평가 -> 결과가 false면 for 반복문을 빠져 나와 다음 처리로 이동 / true면 문장을 실행한 후에 반복문 실행
3. 다시 한 번 for 반복문의 시작 부분으로 돌아가서 조건식을 평가

<br/>
<br/>

##### **· 간단한 예시**

1)

```js
for(var i = 0; i < 10; i++) { ... } // -> i = 0, 1, 2, 3, 4, 5, 6, 7, 8, 9
for(var i = 2; i <= 10; i+= 2) { ... } // -> i = 2, 4, 6, 8, 10
for(var i = 10; i > 0; i--) { ... } // -> i = 10, 9, 8, 7, 6, 5, 4, 3, 2, 1
```

<br/>

2) 초기화식을 for 반복문 이전에 먼저 선언했다면 for 반복문에서는 생략 가능

```js
var num = 1;
for( ; num < 5; num++) {
    // 실행 문장 작성
}
```

<br/>

3) for 반복문 블록 내에 증감식 문장을 포함하면 for 반복문 자체에 증감식 생략 가능

```js
var num = 1;
var st = "ABCDEF";
var ct = st.length;

for( ; num < ct; ) {
    // 실행 문장 작성
    num++;
}
```

<br/>

4) 구구단 2단 출력

```js
let sum = 0;

for(i = 1; i < 10; i++) {
    sum = i * 2;
    document.write(2 + " * " + i + " = " + sum + "<br/>");
}
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbg5ST2%2FbtqL5z3lRIA%2F5a7yd787ejKiZ72k6YBiXK%2Fimg.png)


<br/>
<br/>
- - -
<br/>

#### **1-1. 중첩 for 반복문**

- for 반복문 안에 for 반복문을 작성하면 중첩 반복문 만들기 가능


<br/>
<br/>

##### **· 간단한 예시**

1) 구구단 2, 3단 출력

```js
var x, y;
for(x = 2; x <= 3; x++) {
    document.write("--- " + x + "단 ---<br>");

    for(y = 1; y <= 9; y++) {
        document.write(x + "*" + y + "=" + (x * y) + "<br>");
    }
}
```

<br/>

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FUPE19%2FbtqLXS4dxhL%2FFhlMIOq5N9UBfOBkoZsA10%2Fimg.png)

<br/>
<br/>
- - -
<br/>

#### **1-2. for~in 반복문**

- 객체 안의 프로퍼티를 순회하는 반복문
- 반복문 안에서 문장을 여러 개 실행하려면 여러 문장을 블록으로 묶어서 블록 문장으로 만듦
- for~in 반복문 안에서도 break문과 continue문 사용 가능

<br/>

##### **· for~in 반복문의 처리 흐름**

1. for~in 반복문이 실행되면 먼저 객체 표현식을 평가
2. 객체 표현식이 null 또는 undefined로 평가되면 for~in 반복문을 빠져나와 다음 작업으로 이동 / 객체로 평가되면 객체 프로퍼티 이름이 차례대로 변수에 할당되고 각각의 프로퍼티에 대해서 문장이 한 번씩 실행됨

<br/>
<br/>

##### **· 간단한 예시**

1)

```js
var obj = {a:1, b:2, c:3};

for(var p in obj) {
    console.log("p = " + p);
}
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdmuiB6%2FbtqL38EgaBc%2Fz3P45d8GQaKskp3X3s8jDK%2Fimg.png)

- for~in 반복문은 프로퍼티 이름만 꺼내 변수에 할당

<br/>

2) 반복문 안에 프로퍼티 값 가지고 오기 (괄호 연산자 사용)

```js
var obj = {a:1, b:2, c:3};

for(var p in obj) {
    console.log("obj." + p + "=" + obj[p]);
}
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb2metx%2FbtqLXSiTMqt%2FKthaKj6QnadsqGU3BJKnj0%2Fimg.png)

<br/>
<br/>
- - -
<br/>

#### **2. while 반복문**

- 조건만 맞아떨어지면 일정한 처리를 계속 반복해서 실행
- 반복문 안에서 여러 문장을 실행하려면 여러 문장을 블록으로 묶어서 블록 문장으로 만듦
- while 반복문 안에 break문과 continue문 사용 가능

<br/>

##### **· 작성 방법**

```js
// 1. 기본 작성
let 변수 = 초기값;
while(조건식) {
    조건이 만족될 때까지의 실행 문장;
    증감식;
}
```

- 조건식: 참과 거짓의 조건으로 참인 동안 실행

<br/>

##### **· while 반복문의 처리 흐름**

1. 조건식 평가
2. 조건이 참인 동안 블록 내 문장을 처리, 거짓이면 블록을 벗어나 다음 문장을 처리
	- while 반복문의 조건식을 처음 실행할 때 거짓이면 한 번도 블록 내 문장을 처리하지 못하고 블록을 벗어남
	- 항상 참이면 무한 반복 (문장 실행 후 다시 한 번 while 반복문의 시작 부분으로 돌아가서 조건식을 평가) -> 실행 문장 내에 if 조건문과 break문을 사용하여 특정 조건을 만족하면 반복을 중단하게 해야 함

<br/>
<br/>

##### **· 간단한 예시**

1) 1부터 10까지 나열

```js
let i = 1;

while(i <= 10) {
    document.writeln(i);
    // document.writeln(); -> 문서에 띄어쓰기로 작성
    i++;
}
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FOsJRp%2FbtqL5A3d1sj%2FYmUVDSQVbLId5ukIXBGHc1%2Fimg.png)

<br/>

2) n의 팩토리얼 구하는 함수

```js
function fact(n) {
    var k = 1, i = 1;
    while(i < n) {
        k *= (++i);
    }
    return k;
}

fact(5); // -> 120
```

<br/>

3) 1부터 100까지의 합 구하기

```js
var x = 1, sum = 0;

while(x <= 100) {
    sum += x;
    x++;
}

document.write("1부터 100까지의 합은 " + sum + "입니다.");
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbQrwnU%2FbtqL5A8o5Bn%2FCXNfhAFtkIlNm2EOMx2Q6K%2Fimg.png)

3-1) 1부터 100까지의 합 구하기 - 다른 방법

```js
var x = 1, sum = 0;

while(1) {
    sum += x;
    x++;

    if(x == 101) {
        break;
    }
}

document.write("1부터 100까지의 합은 " + sum + "입니다.");
```

2)와 같은 결과 출력

<br/>

4)1에서 30까지의 숫자 중 2의 배수이고 6의 배수일 경우만 출력

```js
var x = 1;

while(x <= 30) {
    if(x % 2 == 0 && x % 6 ==0) { // 조건이 만족될 때까지의 실행 문장
        document.writeIn(x);
    }
    x++; // 증감식
}
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbB6G0D%2FbtqL2wMDzmV%2FK6ohH0vmBkB3EkYxpKCl8k%2Fimg.png)

<br/>
<br/>
- - -
<br/>

#### **2-1. do~while 반복문**

- 블록 내 문장을 먼저 처리한 후 조건식 체크
	- **블록 내 문장을 한 번 이상 반드시 수행함**
	- 반복 실행 여부를 마지막 부분에서 판단
- 작성 시 끝에 세미콜론(;) **반드시 작성**
- 반복문 안에서 문장을 여러 개 실행하려면 여러 문장을 블록으로 묶어서 블록 문장으로 만듦
- do~while 반복문 안에서 break문과 continue문 사용 가능

<br/>

##### **· 작성 방법**

```js
// 1. 기본 작성
do {
    실행 문장
}
while(조건식);
```

<br/>

##### **· while 반복문의 처리 흐름**

1. 실행 문장 먼저 실행
2. 조건식 평가
3. 결과가 false면 do~while 반복문을 빠져 나와 다음 처리로 이동 / true면 반복문의 시작 부분으로 되돌아감

<br/>
<br/>

##### **· 간단한 예시**

1) 1부터 100까지 합 구하기 - do~while 반복문 방법

```js
var x = 1, sum = 0;

do {
    sum += x;
    x++;
}
while(x <= 100);

document.write("1부터 100까지의 합은 " + sum + "입니다.");
```
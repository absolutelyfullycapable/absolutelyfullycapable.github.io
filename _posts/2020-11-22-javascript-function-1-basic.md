---
title: "JavaScript 함수 (1)"
date: 2020-11-22
categories: [JavaScript]
comments: true
---

## **함수**

- 특정 기능을 수행하는 하나의 모듈 (특정 기능을 제공하기 위한 코드의 집합)
- 호출 통해 값을 얻음
- 한번 선언하면 여러 번 호출하여 사용 가능 (코드의 재사용성! 🌟)
	- 재사용성의 목표: 어떠한 코드가 있을 때 그 코드를 여러 곳에서 사용할 수 있는 형태로 만드는 것 (좋은 부품을 만드는 거라고 생각하면 쉬움!)
	- 재사용성이 높아지면 유지보수가 용이해지고, 가독성이 좋아짐
- 호출할 때마다 어떤 입력값을 주냐에 따라 출력값이 달라짐
- 함수를 선언, 사용하는 이유: **한번 정의한 작업을 필요할 때마다 호출하여 사용하기 위함**

<br>

- - -

<br>

### **· 작성 방법**

```js
function 함수명(매개 변수 1, 매개 변수 2, ...) { // 함수 선언
    실행 문장;
    return 반환값;
}

함수명(인수 1, 인수 2, ...);
```

1. **함수명**
    - 함수 이름
    - 함수명 작성 규칙은 변수명 작성 규칙과 같음 (변수명으로 사용할 수 없는 것은 함수명으로도 사용 불가능)
    - 선택 사항으로 함수명 없이 함수 생성 가능
2. **인수(argument)**: 함수를 호출할 때 전달하는(함수로 유입되는) 입력값
3. **매개 변수(parameter, 인자)**
    - 함수 호출문에서 전달한 인자를 받기 위해 선언된 변수
    - 기본적으로 지역 변수로 정의되어 함수 내에서만 사용 가능
4. **function**: 함수 선언 시 사용되는 키워드
5. **return**: 함수에서 수행한 결괏값을 반환할 때 사용하는 키워드

<br>

- - -

<br>

### **· 함수 정의 방법**

1) 함수 선언문으로 정의

- 함수 선언문의 정의할 때는 함수명 생략할 수 없음 -> 기명 함수
- 매개변수는 0 개 이상의 목록으로 괄호로 감싸고 콤마(,)로 분리
	- 매개변수의 타입을 기술하지 않아 함수 몸체 내에서 매개변수의 타입 체크가 필요할 수 있음
- 함수 선언문으로 정의한 함수는 호출문이 그보다 앞에 위치해도 호출할 수 있음 (자바스크립트 엔진이 함수 선언문을 프로그램의 첫머리 또는 함수의 첫머리로 끌어올리기 때문(호이스팅))
- 함수 선언문도 내부적으로 자바스크립트 엔진이 기명 함수 표현식으로 변환하므로 결국 함수 리터럴 방식으로 정의되는 것과 마찬가지

    ```js
    console.log(square(2)); // -> 4
    function square(x) {
    	return x*x; // return 문으로 결과값 반환 = 반환값 (return value)
    };
    ```

<br>

2) 함수 리터럴로 정의 (표현식으로 작성)

- 리터럴: 코드 상에서 데이터를 표현하는 것
- 함수 표현식: 함수의 일급 객체 특성을 이용하여 함수 리터럴 방식으로 함수를 정의하고 변수에 할당하는 방식
- 함수 리터럴로 정의한 함수는 일급 객체이기 때문에 그 참조를 변수에 할당한 후 호출 가능
	- 이때 변수는 함수명이 아니라 할당된 함수를 가리키는 참조값을 저장하게 됨 -> **함수 호출 시 함수명이 아니라 함수를 가리키는 변수명을 사용하여야 함**
- 함수 표현식 방식으로 정의한 함수는 함수명 생략 가능 -> 익명 함수
	- 함수 표현식에서는 함수명을 생략하는 것이 일반적

    ```js
    var ex1 = function square(x) {
    	return x*x;
    }; // 기명 함수 표현식 (named function expression)
    console.log(ex1(3)); // -> 9
    console.log(square(3)); // -> Uncaught ReferenceError: square is not defined (함수가 할당된 변수로 함수를 호출하지 않고 함수명으로 호출하면 함수 표현식에서 사용한 함수명은 외부 코드에서 접근 불가능하기 때문에 에러 발생)

    var ex2 = function(x) {
        return x+x;
    }; // 익명 함수 표현식 (anonymous function expression)
    console.log(ex2(3)); // -> 6
    ```

<br>

3) Function 생성자로 정의

- Function 생성자로 정의한 함수는 그 참조를 변수에 할당한 후 호출 가능
- 이 방식을 일반적으로 사용하지는 않음

    ```js
    var square = new Function("x", "return x*x");
    console.log(square(2)); // -> 4
    ```

<br>

4) 화살표 함수 표현식으로 정의

- 화살표 함수 표현식으로 정의한 함수는 그 참조를 변수에 할당한 후 호출 가능

    ```js
    var square = x => x*x;
    console.log(square(2)); // -> 4
    ```

<br>

- - -

<br>

### **· 함수 호출**

#### **1. 일반적인 방법 (기본 함수, 선언 함수)**

- 함수를 선언하고 호출하는 일반적인 방법
- 이름을 가진 함수로 직접 호출이 가능
- 스크립트 내 어디서나 선언 가능
- 함수 호출은 함수 선언 전후 상관없이 할 수 있지만 **가급적 함수 선언 후에 할 것을 권장**

<br>

- 작성 방법

```js
function 함수명(매개 변수 1, 매개 변수 2, ...) { // 함수 선언
    실행 문장;
}

함수명(인자 1, 인자 2, ...); // 함수 호출
```

<br>

- 간단한 예시

1)

```js
var before = "함수 선언 전 호출",
    after = "함수 선언 후 호출";

printMsg(before);    // 함수 선언 전 호출

function printMsg(msg) {
    document.write("함수 호출 메시지: " + msg + "<br>");
}

printMsg(after);    // 함수 선언 후 호출
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FLZiSP%2FbtqNYvGj8Kd%2Fsfpr00qVFB4TaURubo4Xk0%2Fimg.png)

<br>

2)

```js
function fx(fruits1, fruits2) { // fx라는 이름을 부여해서 선언한 함수
    alert(fruits1);
    alert(fruits2); 
}

fx("수박", "사과");  // 함수 호출
                    // 함수 fx의 fruits1에는 수박을, fruits2에는 사과를 전달
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F7kO2T%2FbtqN8Zs31IH%2Fr8XPdfOc7PJRjacVA9zi4k%2Fimg.png)

<br>

3) 버튼을 누르면 함수가 출력되는 프로그램 1 (**onclick 속성을 사용하여 함수 호출 가능**)

```html
<body>
    <script>
        function printMsg(name, age) {
            document.write("학생 이름: " + name + "<br>");
            document.write("학생 나이: " + age);
        }
    </script>

    <button type="button" onclick="printMsg('홍길동', 21)">학생 정보</button>
</body>
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F5vCzi%2FbtqN8fBJN2w%2FBYhBv8QxWyc0BCjmEtel0k%2Fimg.png)

<br>

4) 버튼을 누르면 함수가 출력되는 프로그램 2

```html
<body>
    <div class="btn" onclick="fruits()">함수 호출</div>

    <script>
        let num = 0; // 전역 변수: 문서 전역에서 사용

        function fruits() { // 선언 함수: 어느 곳에서든 호출 가능
            // 지역 변수: 함수 내에서만 실행되는 변수, 함수가 실행될 때마다 새로 만들어짐
            // let a = 0;

            num++;
            if(num == 1) {
                alert("사과");
            } else if(num == 2) {
                alert("수박");
            } else {
                alert("복숭아");
            }
        }
    </script>
</body>
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fcgzdqt%2FbtqObX2Brpz%2FAHquvxLnM3q2x5ci7rT031%2Fimg.png)

<br>

#### **2. 함수 표현식으로 작성하는 방법 (무명 함수, 익명 함수)**

- 이름이 없는 함수
- 함수 표현식을 선언하여 변수에 할당하는 방법 (이름이 없기 때문에 변수에 대입하여 주로 사용)
    - 변수를 함수명으로 사용
- 함수명이 생략되기 때문에 **무명 함수, 익명 함수**라고도 함
    - 함수 표현식에서 함수명을 정의할 수 있지만 함수명과 변수명을 서로 다르게 정의해야 함
    - 함수 표현식에서 정의한 함수명은 함수 외부에서 호출하여 사용할 수 없음
- 함수 선언 전에 호출하면 구문 에러(syntax error)가 발생함

<br>

- 작성 방법

```js
var 변수명 = function(매개 변수 1, 매개 변수 2, ...) { // 함수 선언
    실행 문장;
}

변수명(인자 1, 인자 2, ...); // 함수 호출
```

<br>

- 무명(익명) 함수 호출

```js
var before = "함수 선언 전 호출 에러",
    after = "함수 선언 후 호출만 가능";

// printMsg(before);    -> 함수 선언 전 호출 에러

var printMsg = function(msg) {
    document.write("함수 호출 메시지: " + msg + "<br>");
}

printMsg(after);    // 함수 선언 후 호출
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FmJwFg%2FbtqNZNmtAd9%2FcnCe8X2gTp0HFN0DOUDwq1%2Fimg.png)

<br>

- 기본 함수와 무명 함수 호출의 우선순위
    - 자바스크립트에서 기본 함수와 무명 함수가 같은 이름을 사용하면 무명 함수가 호출됨

```js
var printMsg = function(msg) { // 무명 함수 선언
    document.write("무명 함수: " + msg + "<br>");
}

function printMsg(msg) { // 기본 함수 선언
    document.write("기본 함수: " + msg + "<br>");
}

printMsg("호출되었습니다."); // 함수 호출
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FXjhvs%2Fbtq0SlKIe2X%2Fw1kkZROXJAICLAOQp9uWVk%2Fimg.png)

<br>

- - -

<br>

### **· 함수 반환값 출력**

- 함수 수행 결괏값을 반환할 때(함수를 호출한 코드(caller)에게 값을 반환할 때) **'return'** 키워드 사용
    - 함수 안에서 선언된 변수나 값의 경우 외부에서 접근 불가능하기 때문에 return 키워드 사용하여 호출한 코드 돌려 줌
    - 함수 실행 후 결과를 다시 얻으려면 리턴 키워드 사용
    - 배열 등을 이용하여 한 번에 여러 개의 값 리턴 가능
- 반환값(return value): 반환된 값
- 함수는 반환을 생략할 수 있음 (암묵적으로 undefined 반환)
    - 반환할 결괏값이 없는 경우에도 return문 생략 가능
- 반환값을 저장하기 위한 변수 미리 선언해야 함
    - 작성 방법에 있는 변수 'result'가 그 역할
- 함수 처리가 완료되면 자동으로 함수를 호출한 시점으로 돌아가 프로그램 계속 수행
    - 만약 return 키워드 이후에 다른 구문이 존재하면 그 구문은 실행되지 않음

<br>

- 작성 방법

```js
function 함수명(매개 변수 1, 매개 변수 2, ...) { // 함수 선언
    실행 문장;
    return 반환값;
}

result = 함수명(인자 1, 인자 2, ...); // 함수 호출
```

<br>

- 간단한 예시

1) a * b 값을 반환

```js
function num(a, b) { // 매개 변수 a, b를 이용하여 a * b 값 반환
    let sum = a * b;
    console.log(sum);
    return sum;
    // 함수 안에서 선언된 변수나 값의 경우 외부에서의 접근이 불가능하기 때문에 매개 변수(인자)와 리턴 키워드 사용
}

// a: 10, b: 30
alert(num(10, 30)); // 인자 10, 30을 함수 num에게 넘겨 줌

// a: 20, b: 400
alert(num(20, 400));

// a: 15, b: 33
alert(num(15, 33));
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FuaYCA%2FbtqTcP7yffi%2FUqoAepOgliQXk2qRy38skK%2Fimg.png)

<br>

2) 변수 이용하여 반환값 출력

```js
var result; // result는 반환값을 저장하는 변수

function add(name, n) {
    document.write(name + " 학생이 1부터 " + n + "까지 덧셈 수행<br>");
    var sum = 0;
    for(var i = 1; i <= n; i++) {
        sum+=i;
    }
    return sum;
}

result = add('홍길동', 10);
document.write("결과: " + result + "<br>");

result = add('이영희', 100);
document.write("결과: " + result);
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FAulat%2FbtqN2VK3461%2FkL8TyBhO7ELcoZ2dcprh01%2Fimg.png)

<br>

3) 변수 없이 반환값 출력하기

```js
function add(name, n) {
    document.write(name + " 학생이 1부터 " + n + "까지 덧셈 수행<br>");
    var sum = 0;
    for(var i = 1; i <= n; i++) {
        sum+=i;
    }
    return sum;
}

document.write("결과: " + add('홍길동', 10) + "<br>");
document.write("결과: " + add('이영희', 100));
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FAulat%2FbtqN2VK3461%2FkL8TyBhO7ELcoZ2dcprh01%2Fimg.png)

<br>

4) 서로 다른 변수로 같은 함수 반환값 출력하기

- 자바스크립트 함수에서는 여러 변수명으로 하나의 함수를 사용할 수 있음

```js
function add(x, y) {
    return x+y;
}

var calSum = add;   // 함수를 변수에 할당
var addUp = add;    // 함수를 변수에 할당

document.write("결과 1: " + calSum(5, 10) + "<br>");
document.write("결과 2: " + addUp(3, 20));
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdGt3R0%2FbtqNZNz8cqW%2FEyxzXPj0eXy9kiElGnEsck%2Fimg.png)

<br>

5) 복수 값의 반환

```js
function getSize(width, height, depth) {
    var area = width * height,
        volume = width * height * depth;
    return [area, volume];
}

document.write('area is ' + getSize(3, 2, 3)[0]); // -> area is 6
document.write('volume is ' + getSize(3, 2, 3)[1]); // -> volume is 18
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FNEd01%2Fbtq7L1F0IQ3%2FexCzUoINGdMiRGP0apLUr0%2Fimg.png)

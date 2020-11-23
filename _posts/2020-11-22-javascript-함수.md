---

layout: post

title: "JavaScript 함수"

description: "JavaScript 함수에 대해 알아보자"

date: 2020-11-22

tags: JavaScript 함수

comments: true

---

## **함수**

- 특정 기능을 수행하는 하나의 모듈
- 한번 선언하면 여러 번 호출하여 사용 가능
    - 호출할 때마다 어떤 입력값을 주냐에 따라 출력값이 달라짐
- 함수를 선언, 사용하는 이유: **한번 정의한 작업을 필요할 때마다 호출하여 사용하기 위함**

- - -

<br>

#### **· 작성 방법**

```js
function 함수명(매개 변수 1, 매개 변수 2, ...) { // 함수 선언
    실행 문장;
    return 반환값;
}

함수명(인자 1, 인자 2, ...);
```

1. **함수명**
    - 함수 이름
    - 함수명 작성 규칙은 변수명 작성 규칙과 같음 (변수명으로 사용할 수 없는 것은 함수명으로도 사용 불가능)
2. **인자**: 함수를 호출할 때 전달하는 입력값
3. **매개 변수**
    - 함수 호출문에서 전달한 인자를 받기 위해 선언된 변수
    - 기본적으로 지역 변수로 정의되어 함수 내에서만 사용 가능
4. **function**: 함수 선언 시 사용되는 키워드
5. **return**: 함수에서 수행한 결괏값을 반환할 때 사용하는 키워드

- - -

<br>

#### **· 함수 호출**

##### **1. 일반적인 방법 (기본 함수)**

- 함수를 선언하고 호출하는 일반적인 방법
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
var before = "함수 선언 전 호출";
var after = "함수 선언 후 호출";

printMsg(before);    // 함수 선언 전 호출

function printMsg(msg) {
    document.write("함수 호출 메시지: " + msg + "<br>");
}

printMsg(after);    // 함수 선언 후 호출
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FLZiSP%2FbtqNYvGj8Kd%2Fsfpr00qVFB4TaURubo4Xk0%2Fimg.png)

<br>

2) 버튼을 누르면 메시지가 출력되는 프로그램 (**onclick 속성을 사용하여 함수 호출 가능**)

```js
<body>
    <script>
        function printMsg(name, age) {
            document.write("학생 이름: " + name + "<br>");
            document.write("학생 나이: " + age + "<br>");
        }
    </script>

    <button type="button" onclick="printMsg('홍길동', 21)">학생 정보</button>
</body>
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F5vCzi%2FbtqN8fBJN2w%2FBYhBv8QxWyc0BCjmEtel0k%2Fimg.png)

<br>

##### **2. 함수 표현식으로 작성하는 방법 (무명 함수)**

- 함수 표현식을 선언하여 변수에 할당하는 방법
    - 변수를 함수명으로 사용
- 함수명이 생략되기 때문에 **무명 함수**라고도 함
    - 함수 표현식에서 함수명을 정의할 수 있지만 함수명과 변수명을 서로 다르게 정의해야 함
    - 함수 표현식에서 정의한 함수명은 함수 외부에서 호출하여 사용할 수 없음

    ```js
    var before = "함수 선언 전 호출 에러";
    var after = "함수 선언 후 호출만 가능";

    var printMsg = function myMsg(msg) {
        document.write("함수 호출 메시지: " + msg + "<br>");
        myMsg("함수 표현");   // 호출 가능
    }

    printMsg(after);   // 함수 호출 가능
    myMsg(after); // 함수 호출 에러
    ```

- 이 방법 사용 시 **함수 선언 전에 함수 호출을 할 수 없다는 점에 주의해야 함**
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

- 무명 함수 호출

```js
var before = "함수 선언 전 호출 에러";
var after = "함수 선언 후 호출만 가능";

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

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FmJwFg%2FbtqNZNmtAd9%2FcnCe8X2gTp0HFN0DOUDwq1%2Fimg.png)

- - -

<br>

#### **· 함수 반환값 출력**

- 함수 수행 결괏값을 반환할 때는 **'return'** 키워드 사용
- 반환할 결괏값이 없다면 return문 생략 가능
- 반환값을 저장하기 위한 변수 미리 선언해야 함
    - 작성 방법 예시에서는 'result'가 그 역할
- 함수 처리가 완료되면 자동으로 함수를 호출한 시점으로 돌아가 프로그램 계속 수행

<br>

- 작성 방법

```js
function 함수명(매개 변수 1, 매개 변수 2, ...) { // 함수 선언
    실행 문장;
    return 반환값;
}

result = 함수명(인자 1, 인자 2, ...); // 함수 호출
```


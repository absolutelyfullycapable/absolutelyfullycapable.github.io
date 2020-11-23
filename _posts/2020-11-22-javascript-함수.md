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

<br>

#### **· 함수 호출**

#####**1. 일반적인 방법 (기본 함수)**

- 함수를 선언하고 호출하는 일반적인 방법
- 스크립트 내 어디서나 선언 가능
- 함수 호출은 함수 선언 전후 상관없이 할 수 있지만 **가급적 함수 선언 후에 할 것을 권장**

<br>

- 작성 방법

```js
function 함수명(매개 변수 1, 매개 변수 2, ...) { // 함수 선언
    실행 문장;
}

함수명(인자 1, 인자 2, ...);
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

#####**2. 함수 표현식으로 작성하는 방법 (무명 함수)**
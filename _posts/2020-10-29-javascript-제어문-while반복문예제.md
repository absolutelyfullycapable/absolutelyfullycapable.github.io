---

layout: post

title: "JavaScript 제어문 (2) 반복문 - while 반복문 예제"

description: "제어문의 반복문 중 while 반복문의 다양한 예제를 작성해 보자"

date: 2020-10-30

tags: JavaScript 제어문 반복문 중첩 while반복문

comments: true

---

### **· while 반복문 예제**

<br/>

1) 구구단 8단 출력

```js
let i = 1; // 1~9 곱할 값
let num = 8; // 8단

while(i <= 9) {
    sum = num * i;
    document.write(num + " * " + i + " = " + sum + "<br>");
    i++;
}
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F9VIPn%2FbtqL8nhtrD4%2FDoj6wIvw4lKd2AcSKlMfK1%2Fimg.png)

<br/>

2) 구구단 2단부터 4단까지 출력

```js
let num = 1; // 2~4단
let i = 1; // 곱하기 1~9

while (num < 4) {
    num++;
    document.write("<h2>--" + num + "단--</h2>");

    while(i <= 9) {
        let sum = num * i;
        document.write(num + " * " + i + " = " + sum + "<br>");
        i++;
    }
    i = 1; // 변수값 초기화
}
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Flku4t%2FbtqL6JlhgGg%2FgvxPWl6WzniQnFK3Re3sD0%2Fimg.png)

<br/>

3) 1에서 30까지의 숫자 중 2의 배수이고 6의 배수일 경우만 출력

```js
let i = 1;

while(i <= 30) {
    if(i % 2 == 0 && i % 6 ==0) {
        document.writeln(i);
    }
    i++;
}
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FrVCij%2FbtqL8VSzhY1%2FRlami1QsiX2ZrVZvQnql1K%2Fimg.png)

<br/>

4) 1부터 1000까지의 합

```js
let i = 1;
let sum = 0;

while(i <= 1000) {
    sum += i;
    i++;
}

document.body.innerHTML = "<h2>1부터 1000까지의 합은 " + sum + "입니다.</h2>";
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fda4P7r%2FbtqL8U0tnIF%2Frk43lgKVc5EzgIUTEK3yTK%2Fimg.png)

<br/>

5) 1부터 몇까지 더해야 3000을 넘길 수 있는지 확인

```js
let i = 1;
let sum = 0;

while(1) { // true, 1(true를 숫자로 치환한 것)..을 넣으면 끝도 없이 반복됨
    sum += i;
    // i++; <- 여기에 넣으면 빠져나갔을 때 i가 1 더해진 값으로 출력되기 때문에 if문 다음에 작성해야 함
    if(sum > 3000) {
        break;
    }
    i++;
}

document.write("1부터 " + i + "까지 더하면 " + sum + "으로 3000이 넘는다.");
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F8bZuo%2FbtqL3uCnWac%2F3mRN1CDLBAtt9XMzZWLsbK%2Fimg.png)
---
title: "JavaScript 제어문 (2) 반복문 - for 반복문 예제"
date: 2020-10-29
categories: [JavaScript]
comments: true
---

### **· for 반복문 예제**

<br>

1) 1부터 10까지의 합 구하기

```js
let sum = 0; // 값이 대입되어 있지 않거나 변수 선언이 되지 않은 상태에서 작성되면 식 안에서 변수의 성격을 파악할 수 없기 때문에 숫자로 초기화함

for(let i = 1; i <= 10, i++) {
    sum += i;
}

document.body.innerHTML = "<h1>1부터 10까지의 합은 " + sum + "입니다.</h1>";
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fpgugc%2FbtqL3wlCI9G%2FTG8b4TL4dYah73pkycR1ek%2Fimg.png)

<br>

2) 3, 5, 7, 9의 합

```js
let sum = 0;

for(let i = 3; i <= 9; i += 2) {
    sum += i;
}

document.body.innerHTML = "<h1>3, 5, 7, 9의 합은 " + sum + "입니다.</h1>";
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbawZXM%2FbtqL1oBVmgm%2FnUB3nGxF2Zc5zZz6QBBynK%2Fimg.png)

<br>

3) 1부터 입력한 숫자를 모두 더해 출력

```js
let num = prompt("더할 숫자를 입력해 주세요.");
num = Number(num);
let sum = 0;

for(let i = 1; i <= num; i++) {
    sum += i;
}

document.inner.HTML = "<h1>1부터 " + num + "까지의 합은 " + sum + "입니다.</h1>"
```

<br>

4) 1부터 100까지 중에 3의 배수이지만 7의 배수는 아닌 숫자만 출력

```js
for(let i = 1; i <= 100; i++) {
    if(i % 3 == 0 && i % 7 != 0) {
        document.writeln(i);
    }
}
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdKAKmO%2FbtqL6HUqF1T%2F1ZEK0VX6b5pmz4IZO6F8u0%2Fimg.png)

<br>

5) 입력 받은 구구단 출력

```js
let num = prompt("2단부터 9단 사이의 원하는 구구단을 입력하세요.");
num = Number(num);
let sum = 0;

if(num >= 2 && num <= 9) {
    document.write("<h1>" + num + "단</h1>");

    for(i = 1; i <= 9; i++) {
        sum = i * num;
        document.write(num + " * " + i + " = " + sum + "<br>");
    }
} else {
    alert("2부터 9까지의 숫자만 입력해 주세요.");
    window.location.reload();
}
```

<br>

6) 별 쌓기 - **중첩 반복문**

```js
for(let i = 1; i <= 9; i++) {// 줄 수
    for(let star = 1; star <= i; star++) {// 별 수
        document.write("*");
    }
    document.write("<br>");
}
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FIPlYi%2FbtqL2PFZFiY%2FgYzvDbVsZkVTqNKWF8oIP0%2Fimg.png)
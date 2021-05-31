---
title: "JavaScript 함수 (3) 예제"
date: 2021-01-13
categories: [JavaScript]
comments: true
---

1) 입력한 값의 부가세 (가격의 10%) 포함 값을 출력

> ex) 1000(제품가) * 0.1(부가세) + 1000(제품가) = 1100(부가세 포함 값)

```js
let price = prompt("금액을 입력해 주세요.");
price = Number(price);

function sum(price) {
    let tax = 0.1;
    return price * tax + price;
}

document.write("<h3>입력한 값의 부가세 포함 가격은 " + sum(price) + "원입니다.</h3>");
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbvsPJJ%2FbtqTrTzSGzD%2FdLuTDjwfudbfxiOR2h1DRK%2Fimg.png)

<br>

2) 과일에 맞는 가격 출력

```js
function fruit(name) {
    let msg = "오천 원입니다."
    if(name == "수박") {
        msg = "만 원입니다."
    } else if(name == "복숭아") {
        msg = "이만 원입니다."
    }

    document.write(name + ': ' + msg + '<br>'); // 출력값까지 함수 내부에 존재 -> return 키워드는 필요하지 않음
}

fruit("사과"); // "오천 원입니다." 출력
fruit("수박"); // "만 원입니다." 출력
fruit("복숭아"); // "이만 원입니다." 출력
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcGOn8B%2FbtqTvR2VRVP%2F7kk3FEzlnFO2qAlHP8K9K0%2Fimg.png)

<br>

3) 1부터 n까지의 합을 구하는 프로그램

```js
// 방법 1
function sum(n) {
    for(var i = 1, total = 0; i <= n; i++) {
        total += i;
    }
    return total;
}
document.write(sum(100));

// 방법 2
function sum(n) {
    let i = 1, total = 0;
    while(i <= n) {
        total += i;
        i++;
    }
    return total;
}
document.write(sum(100));
```

![return](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F3BiaV%2FbtqTrTAgUXE%2FsIulEPbHfOQz1EqBUbMTPk%2Fimg.png)

<br>

4) 구구단 3단의 여섯 개, 6단의 네 개만 출력

```js
// 방법 1
function out(n, limit) {
    document.write('<h2>--' + n + '단--</h2>');
    for(let i = 1; i <= limit; i++) {
        let total = n * i;
        document.write(n + ' * ' + i + ' = ' + total + '<br>');
    }
}
out(3, 6);
out(6, 4);

// 방법 2
function out(n, limit) {
    document.write('<h2>--' + n + '단--</h2>');
    for(let i = 1; i < 10; i++) {
        if(i == (limit + 1)) {
            break;
        }
        sum = n * i;
        document.write(n + ' * ' + i + ' = ' + sum + '<br>');
    }
}
out(3, 6);
out(6, 4);
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbTRhqU%2FbtqTox5TTeh%2FWgOP7OQjqm7J0DtaAjMMkk%2Fimg.png)

<br>

5) 1부터 100 중 임의의 수가 홀수인지 짝수인지 고르는 프로그램 (방법 1)

```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <title>함수 예제 연습</title>
        <style>
            div { display:inline-block;  border:1px solid #000; width:200px; height:50px; line-height:50px; text-align:center; cursor:pointer; transition:0.3s; font-size:1.4em; font-weight:bold; }
            div:hover { background-color:#000; color:#fff; }
        </style>
        <script>
            window.onload = function() { // window.onload -> 자바스크립트에서 페이지가 로드되면 자동으로 실행되는 전역 콜백 함수
                let num = Math.floor(Math.random() * 100 + 1);
                // Math.random(); -> 0 이상 1 미만의 난수(정의된 범위 내에서 무작위로 추출된 수)
                // Math.floor(x); -> x 이하의 최대 정수
                console.log(num);

                if(num % 2 == 0) { // num이 짝수일 때
                    document.getElementById('odd').onclick = function() {
                        // document.getElementById('id 값'); -> id 값으로 요소 객체를 가져올 때 사용하는 메서드
                        alert('틀렸습니다. 짝수입니다.');
                    }
                    document.getElementById('even').onclick = function() {
                        alert('정답입니다.');
                    }
                } else { // num이 홀수일 때
                    document.getElementById('odd').onclick = function() {
                        alert('정답입니다.');
                    }
                    document.getElementById('even').onclick = function() {
                        alert('틀렸습니다. 홀수입니다.');
                    }
                }
            }
        </script>
    </head>

    <body>
        <div id="odd">홀수</div>
        <div id="even">짝수</div>
    </body>
</html>
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbZ4gmj%2FbtqTvSnrYRr%2FklzRomS1fppxMOC6a68OyK%2Fimg.png)

<br>

6) 1부터 100 중 임의의 수가 홀수인지 짝수인지 고르는 프로그램 (방법 2)

```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <title>함수 예제 연습</title>
        <style>
            div { display:inline-block;  border:1px solid #000; width:200px; height:50px; line-height:50px; text-align:center; cursor:pointer; transition:0.3s; font-size:1.4em; font-weight:bold; }
            div:hover { background-color:#000; color:#fff; }
        </style>
        <script>
            window.onload = function() {
                let num = Math.floor(Math.random() * 100 + 1);
                console.log(num);

                function odd() { // 홀수일 때
                    if(num % 2 != 0) {
                        alert('정답입니다.');
                    } else {
                        alert('틀렸습니다. 짝수입니다.');
                    }
                }

                function even() { // 짝수일 때
                    switch (num % 2) {
                        case 0:
                            alert('정답입니다.');
                            break;
                        default:
                            alert('틀렸습니다. 홀수입니다.');
                    }
                }

                document.getElementById('odd').onclick = function() {
                    odd();
                }

                let evenBtnClick = document.getElementById('even');
                evenBtnClick.onclick = function() {
                    even();
                }
            }
        </script>
    </head>

    <body>
        <div id="odd">홀수</div>
        <div id="even">짝수</div>
    </body>
</html>
```

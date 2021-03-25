---
title: "JavaScript 배열 (2) 예제"
date: 2021-01-15
categories: [JavaScript]
comments: true
---

(1) 좋아하는 과일 4개를 배열로 만들고 반복문을 이용하여 알림창을 순차적으로 출력

```js
var fruit = ["수박", "딸기", "복숭아", "사과"];

// 방법 1
for(var i = 0; i < fruit.length; i++) {
	alert(fruit[i]);
}

// 방법 2
var i = 0;
while(i < fruit.length) {
	alert(fruit[i]);
    	i++;
}

// 방법 3
for(var i in fruit) {
	alert(fruit[i]);
}
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcF9Ksp%2FbtqTAFbTS2C%2FB9sBeQO9NecKEBam0o6ek1%2Fimg.png)

<br>

(2) 배열 요소가 5개인 배열을 만들고 배열의 인덱스와 그에 맞는 배열 요소를 문서에 출력

```js
// 방법 1
var five = [5, 10, 15, 20, 25];

var i = 0;
while(i < five.length) {
	document.write('<h2>배열의 인덱스 ' + i + '의 배열 요소는 ' + five[i] + '입니다</h2>');
	i++;
}

// 방법 2
for(var i = 0; i < five.length; i++) {
	document.write('<h2>배열의 인덱스 ' + i + '의 배열 요소는 ' + five[i] + '입니다</h2>');
}

// 방법 3
for(var i in five) {
	document.write('<h2>배열의 인덱스 ' + i + '의 배열 요소는 ' + five[i] + '입니다</h2>');
}
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Ft4yOw%2FbtqTADZrqxH%2F7bImdKB1CHFRXgLzGmSGs0%2Fimg.png)

<br>

(3) 4명의 점수를 받아 총점과 평균을 구하고 출력

```js
// 방법 1
var num = new Array(4), // 배열 요소(데이터) 값이 4개인 배열 생성
    i = 0, // 인덱스
    sum = 0; // 합계

while(i < num.length) {
    var score = prompt('점수를 입력해 주세요.');
    score = Number(score); // 입력 받은 숫자형 문자열을 숫자로 리턴하여 재대입 -> prompt에서 입력 받은 값이 숫자형 문자열이라 숫자열로 변경해야 됨
    num[i] = score; // 각각의 배열 요소에 대입
    sum += num[i];
    i++;
}

document.write('<h2>총점은 ' + sum + '점이고, 평균은 ' + sum / num.length + '입니다.</h2>');


// 방법 2 -> n 명의 점수를 받아 총점과 평균을 구하는 프로그램 방식
function score(n) {
	var studentScore = new Array(n);
	for(var i = 0, sum = 0; i < n; i++) {
		studentScore[i] = Number(prompt('점수를 입력해 주세요.'));
		sum += studentScore[i];
	}
	var average = (sum / n);
	document.write('입력한 점수의 총점은 ' + sum + '이고, 평균은 ' + average + '입니다.');
}
score(4);
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbpWXvL%2FbtqTENAiuSB%2FwSQtdQ1GJYkpJqxMU9x48K%2Fimg.png)

<br>

(4) 제시된 점수 중 제일 높은 점수, 제일 낮은 점수, 평균 점수를 각각 출력 (평균 점수는 소수점 이하 반올림하여 나타내기) (🥲)

- 제시된 점수: 60, 66, 95, 80, 100, 92

```js
// 방법 1
var score = [60, 66, 95, 80, 100, 92];

// 제일 높은 점수 출력
var i = 0,
    max = 0;

while(i < score.length) {
    switch(max < score[i]) {
        case: true: // 위의 조건이 참인 경우
            max = score[i]; // 변수 max에 재대입
            // 0 < 60 -> true -> max = 60;
            // 60 < 66 -> true -> max = 66;
            // 66 < 95 -> true -> max = 95;
            // 95 < 80 -> false -> max = 95;
            // 95 < 100 -> true -> max = 100;
            // 100 < 92 -> false -> max = 100;
            break;
    }
    i++;
}

document.write('<h2>제일 높은 점수는 ' + max + '점입니다.</h2>');



// 제일 낮은 점수 출력
var a = 0,
    min = 100;

while(a < score.length) {
    if(min > score[a]) { // 참인 경우
        min = acore[a];
        // 100 > 60 -> true -> min = 60; (a = 0일 때)
        // 60 > 66 -> false -> min = 60; (a = 1일 때)
        // 60 > 95 -> false -> min = 60; (a = 2일 때)
        // 60 > 80 -> false -> min = 60; (a = 3일 때)
        // 60 > 100 -> false -> min = 60; (a = 4일 때)
        // 60 > 92 -> false -> min = 60; (a = 5일 때)
    }
    a++;
}

document.write('<h2>제일 낮은 점수는 ' + min + '점입니다.</h2>');

// 평균 점수 출력
var sum = 0;

for(var x = 0; x < score.length; x++) {
    score[x] = Number(score[x]);
    sum += score[x];
}

aver = sum / arr.length;
aver = Math.round(aver); // 소수점 이하 반올림

document.write('<h2>평균 점수는 약 ' + aver + '점입니다.</h2>');
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fcw01rr%2FbtqTDcU5Jld%2FcWsJKHkLz2QKHti2hk31S1%2Fimg.png)

```js
var score = [60, 66, 95, 80, 100, 92],
    sum = 0,
    max = 0,
    min = 100,
    average;

for(var i in score) {
	sum += score[i];
	switch(max < score[i]) {
		case true:
			max = score[i];
			break;
	}
	switch(min > score[i]) {
		case true:
			min = score[i];
			break;
	}
}
average = Math.round((sum / score.length));

document.write('<h2>제시된 점수의 최저점은 ' + min + '점이고, 최고점은 ' + max + '점이며 평균은 약 ' + average + '점입니다.</h2>');
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FRU6Lq%2Fbtq037qk8hC%2FSaGDlVBCUCWKF66gcrEdck%2Fimg.png)

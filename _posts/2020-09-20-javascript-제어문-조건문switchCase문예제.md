---
title: "JavaScript 제어문 (1) 조건문 - switch~case문 예제"
date: 2020-09-20
categories: [JavaScript]
comments: true
---

### **· switch~case문 예제**

<br>

1) 원하는 사이트 입력 후 해당 사이트로 이동

```js
let site = prompt('네이버, 구글, 다음 중 원하는 사이트를 입력해 주세요.');
let url;

switch(site) {
    case '네이버':
    	// window.open("about:blank").location.href = "https://www.naver.com"; - 방법 1
        url = "https://www.naver.com"; // - 방법 2
        break;
    case '구글':
    	// window.open("about:blank").location.href = "https://www.google.com";
        url = "https://www.google.com";
        break;
    case '다음':
    	// window.open("about:blank").location.href = "https://www.daum.net";
        url = "https://www.daum.net";
        break;
    default :
    	alert('제시된 사이트만 입력해 주세요.');
}

if(url) { // url 데이터가 있는 경우만 실행 - 방법 2
	window.open("about:blank").location.href = url;
}

// window.location.href = ""; 사이트 이동
// window.open("about:blank").location.href = ""; 새 창으로 사이트 이동
```

<br>

2) 1~4번까지의 번호를 입력하면 해당되는 번호의 이미지 출력 / 다른 번호를 선택하면 '1~4번까지만 선택해 주세요.' 출력

```js
let num = prompt('1~4번까지의 번호 중 마음에 드는 번호를 입력해 주세요.');
num = Number(num);

switch(num) {
    case 1:
    	document.body.innerHTML = '<img src="img1.jpg" alt="image 1">';
        break;
    case 1:
    	document.body.innerHTML = '<img src="img2.jpg" alt="image 2">';
        break;
    case 1:
    	document.body.innerHTML = '<img src="img3.jpg" alt="image 3">';
        break;
    case 1:
    	document.body.innerHTML = '<img src="img4.jpg" alt="image 4">';
        break;
    default:
    	alert(''1~4번까지만 선택해 주세요.');
        window.location.reload();
}
```

<br>

3) 입력 받은 값이 홀수인 경우 '입력한 값 ..는/은 홀수입니다.' / 짝수인 경우 '입력한 값 ..는/은 짝수입니다.' 출력

```js
let num = prompt('숫자를 입력해 주세요.');

switch(num % 2) { // 문자열이지만 식을 통해 자동으로 숫자로 변환되어 연산 -> 숫자형 데이터
    case 0: // 입력 받은 값이 짝수인 경우
    	alert('입력한 값 ' + num + '은 짝수입니다.');
    	break;
    default: // 입력 받은 값이 홀수인 경우
    	alert('입력한 값 ' + num + '은 홀수입니다.');
}
```

<br>

4) 아메리카노: 10000원, 카페라테: 16000원, 카페모카: 17000원, 바닐라라테: 20000원일 때 입력 받은 커피명을 통해 '주문한 ..은/는 ..원입니다.' 출력

```js
let coffee = prompt('아메리카노, 카페라테, 카페모카, 바닐라라테 중 하나를 입력해 주세요.');
let price = ""; // 변수 초기화

switch(coffee) {
    case '아메리카노':
    	// document.write('주문한 + coffee + '는/은 10000원입니다.');
        price = 10000;
        break;
    case '카페라테':
        price = 16000;
        break;
    case '카페모카':
        price = 17000;
        break;
    case '바닐라라테':
        price = 20000;
        break;
    default:
    	alert('적혀 있는 메뉴 중에서 입력해 주세요.');
}

document.write.innerHTML = '<h1>주문한 ' + coffee + '는/은 ' + price + '원입니다.</h1>';
```

<br>

5) ID는 abc, 비밀번호는 1234를 입력 받아 참인 경우 비밀번호를 입력 받고, 비밀번호도 참인 경우 '로그인되었습니다.' 출력

```js
let id = "abc", pw = 1234;
let user_id = prompt('아이디를 입력해 주세요.', '여기에 입력해 주세요.');

switch(id == user_id) {
    case true:
    	let user_pw = prompt('비밀번호를 입력해 주세요.', '여기에 입력해 주세요.');
        user_pw = Number(user_pw);

        switch(user_pw) {
        	case 1234:
            	alert('로그인되었습니다.');
                break;
            default:
            	alert('비밀번호가 일치하지 않습니다.');
        }
        break; // 비교값이 실행되면 다음을 읽지 않고 구문을 빠져나옴
    default:
    	alert('아이디가 일치하지 않습니다.');
}
```

<br>

6) 요일을 알려 주는 프로그램

```js
var day;
var week = new Date().getDay(); // 0(일요일)~6(토요일)

switch(week) {
    case 0:
    	day = "일요일";
        break;
    case 1;
    	day = "월요일";
        break;
    case 2:
    	day = "화요일";
        break;
    case 3;
    	day = "수요일";
        break;
    case 4:
    	day = "목요일";
        break;
    case 5;
    	day = "금요일";
        break;
    case 6:
    	day = "토요일";
        break;
}

document.write.innerHTML = '<h1>오늘은 ' + day + '입니다.';
```

<br>

7) 요일별 일정을 알려 주는 프로그램 (월, 화요일: HTML5 / 수, 목요일: 자바스크립트 / 금, 토요일: 영어 학습 / 일요일: 수영)

```js
var work;
var week = new Date().getDay();

switch(week) {
    case 0:
    	work = '수영';
        break;
    case 1:
    case 2:
    	work = 'HTML5';
        break;
    case 3:
    case 4:
    	work = '자바스크립트';
    case 5:
    case 6:
    	work = '영어 학습';
        break;
}

document.write('<h1>오늘은 ' + work + ' 일정이 있는 날입니다.<h1>');
```
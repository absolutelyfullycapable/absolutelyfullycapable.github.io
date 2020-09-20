---

layout: post

title: "Javascript 제어문 (1) 조건문 - if~else문, 다중 if~else문 예제"

description: "제어문의 조건문 중 if~else문, 다중 if~else문의 다양한 예제를 작성해 보자"

date: 2020-09-20

tags: javascript 제어문 조건문 중첩 if~else문 다중if~else문

comments: true

---

### **1. if~else문 예제**
<br/>

1) 걸음수를 입력하고 걸음수에 맞는 값 출력하기 (입력한 값이 6000 이상이면 '좋은 습관을 가지고 있습니다.' / 6000 미만이면 '운동이 필요합니다.' 출력)

```js
const walk = prompt('하루에 걷는 걸음은 몇 보입니까?');

if(walk >= 6000) {
	alert('좋은 습관을 가지고 있습니다.');
} else {
	alert('운동이 필요합니다.');
}
```

<br/>

2) 입력 받은 값이 10보다 작으면 '입력한 값이 10보다 작습니다.' / 입력 받은 값이 10보다 크면 '입력 받은 값이 10보다 큽니다.' 출력

```js
const num = prompt('숫자를 입력해 주세요.');

if(num < 10) {
	alert('입력한 값이 10보다 작습니다.');
} else {
	alert('입력한 값이 10보다 큽니다.');
}
```

<br/>

3) 숫자를 입력 받아 짝수면 '짝수입니다.' / 홀수면 '홀수입니다.' 출력

```js
let num = prompt('숫자를 입력해 주세요.');

if(num % 2 == 0) {
	alert('짝수입니다.');
} else {
	alert('홀수입니다.');
}

// 나머지 값을 이용해 짝수, 홀수 많이 사용함
```

<br/>

4) 확인 버튼을 누르면 '탈퇴 처리가 되었습니다.' / 취소 버튼을 누르면 '탈퇴 취소되었습니다.' 출력

```js
let a = confirm('탈퇴하시겠습니까?');

if(a == 1) {
	alert('탈퇴 처리가 되었습니다.');
} else {
	alert('탈퇴 취소되었습니다.');
}

// 확인 버튼 클릭 시 == true == 1
// 취소 버튼 클릭 시 == false == 0
```

<br/>

5) ID가 web, 비밀번호가 12345일 때 로그인

```js
const id = "web", pw = "12345";
const user_id = prompt('아이디를 입력해 주세요.');

if(id == user_id) { // 아이디 일치
	const user_pw = prompt('비밀번호를 입력해 주세요.');
    if(pw == user_pw) { // 아이디 일치, 비밀번호 일치
    	alert('로그인되었습니다.');
    } else { // 아이디 일치, 비밀번호 불일치
    	alert('비밀번호가 일치하지 않습니다.');
        window.location.reload();
    }
} else { // 아이디 불일치
	alert('아이디가 일치하지 않습니다.');
    window.location.reload();
}

// window.location.reload(); 브라우저 새로 고침
```

<br/>
<br/>
- - -
<br/>

### **2. 다중 if~else문 예제**
<br/>

1) 점수를 입력 받아 60점 이상은 합격 / 60점 미만은 불합격 출력

```js
let score = prompt('점수를 입력해 주세요.');

if(score > 100) {
	alert('100점 이하로 작성해 주세요.');
} else if(score >= 60) {
	alert(score + '점은 합격입니다.');
} else if(score < 60) {
	alert(score + '점은 불합격 입니다.');
} else {
	alert('숫자만 입력해 주세요.');
}
```

<br/>

2) 입력 받은 두 수를 비교하여 어떤 숫자가 더 큰지 / 작은지 / 같은지 출력

```js
// 입력창이나 폼으로 입력 받은 숫자의 저장은 문자열로 저장
let num1 = Number(prompt('첫 번째 숫자를 입력해 주세요.')); // 숫자로 변환하는 방법 1
let num2 = prompt('두 번째 숫자를 입력해 주세요.');
num2 = Number(num2); // 숫자로 변환하는 방법 2

if(num1 > num2) {
	alert(num1 + '은/는 ' + num2 + '보다 큽니다.');
} else if(num1 < num2) {
	alert(num1 + '은/는 ' + num2 + '보다 작습니다.');
} else if(num1 === num2) {
	alert(num1 + '과/와 ' + num2 + '는 같습니다.');
} else {
	alert('숫자로만 입력해 주세요.');
}
```

<br/>

3) 입력한 점수와 함께 90점 이상은 A / 80점 이상은 B / 70점 이상은 C / 60점 이상은 D / 그 밑은 F 등급 출력

```js
let score = prompt('점수를 입력해 주세요.'); // 점수
let grade // 등급 선언

if(score >= 90 && score <= 100) {
	grade = "A";
} else if(score >= 80) {
	grade = "B";
} else if(score >= 70) {
	grade = "C";
} else if(score >= 60) {
	grade = "D";
} else if(score < 60 && score >0) {
	grade = "F"
} else {
	alert('0과 100 사이 숫자로만 입력해 주세요.');
}

document.body.innerhtml = '<h1>' + score + '점은 ' + grade + '등급입니다.</h1>';
// document.body.innerhtml; html의 body 태그 안쪽에 작성한다는 뜻
```

<br/>

4) 1과 4 사이의 숫자를 입력하면 해당되는 번호의 이미지를 출력 / 1과 4 사이의 숫자가 아닌 예외 숫자 입력 시에는 '해당 번호로만 선택해 주세요.' 출력한 다음 '새로 고침 후 다시 번호를 선택해 주세요.' 출력

```js
let random = prompt('1~4번까지 번호를 선택하세요.', '이곳에 작성하세요.');

if(random == 1) {
	document.write('<img src="img1.jpg" alt="image 1">');
} else if(random == 2) {
	document.write('<img src="img2.jpg" alt="image 2">');
} else if(ramdom == 3){
	document.write('<img src="img3.jpg" alt="image 3">');
} else if(random == 4) {
	document.write('<img src="img4.jpg" alt="image 4">');
} else {
	alert('해당 번호로만 입력해 주세요.');
    alert('새로 고침 후 다시 번호를 입력해 주세요');
}
```

![ex_screenshot](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FRe9Uo%2FbtqI6N4P4ye%2F7shglXYuXkXVlM1dAb9bPK%2Fimg.png)

- 해당 예제의 prompt 창은 이렇게 뜸
	- prompt('a', 'b');일 때 a는 입력창 위에, b는 입력창에 표시됨

<br/>

5) 3~5월: '봄입니다.'/ 6~8월: '여름입니다.' / 9~11월: '가을입니다.' / 12~2월: '겨울입니다.' 출력

```js
let month = prompt('좋아하는 달을 입력해 주세요.', '숫자로만 입력해 주세요.');
month >= 1, month <= 12;

if(month >= 3 && month <= 5) {
	alert('봄입니다.');
} else if(month >= 6 && month <= 8) {
	alert('여름입니다.');
} else if(month >= 9 && month <= 11) {
	alert('가을입니다.');
} else if(month <= 12 || month <= 2) { // 12보다 작고 2보다 작은 것 둘 다 만족시키면 값은 1밖에 없으므로 둘 중 하나만 만족시키는 걸로 해야 함
	alert('겨울입니다.');
} else {
	alert('1~12 사이ㅢ 숫자만 입력해 주세요.');
}

// && 논리곱 연산자: A 조건, B 조건 모두 만족시켜야만 실행
// || 논리합 연산자: A 조건이나 B 조건 중 하나만 만족시켜도 실행
```

<br/>

6) 입력한 점수에 따라 상(100~81) / 중(80~61) / 하(60~41) / 탈락(40~0)으로 나누고 해당 알림창 띄우기

```js
let score = prompt('점수를 입력해 주세요.');

if(score <= 100 && score > 80) {
	alert(score + '점은 상입니다.');
} else if(score <= 80 && score > 60) {
	alert(score + '점은 중입니다.');
} else if(score <= 60 && score > 40) {
	alert(score + '점은 하입니다.');
} else if(score <= 40 && score >= 0} {
	alert(score + '점은 탈락입니다.');
} else {
	alert('0에서 100 사이 숫자로만 입력해 주세요');
}
```
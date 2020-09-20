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

1) 걸음수를 입력하고 걸음수에 맞는 값 출력하기 (입력한 값이 6000 이상이면 '좋은 습관을 가지고 있습니다.' 출력 / 6000 미만이면 '운동이 필요합니다.' 출력)

```js
const walk = prompt('하루에 걷는 걸음은 몇 보입니까?');

if(walk >= 6000) {
	alert('좋은 습관을 가지고 있습니다.');
} else {
	alert('운동이 필요합니다.');
}
```

<br/>

2) 입력 받은 값이 10보다 작으면 '입력한 값이 10보다 작습니다.' 출력 / 입력 받은 값이 10보다 크면 '입력 받은 값이 10보다 큽니다.' 출력

```js
const num = prompt('숫자를 입력해 주세요.');

if(num < 10) {
	alert('입력한 값이 10보다 작습니다.');
} else {
	alert('입력한 값이 10보다 큽니다.');
}
```

<br/>

3) 숫자를 입력 받아 짝수이면 '짝수입니다.' 출력 / 홀수이면 '홀수입니다.' 출력

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

4) 확인 버튼을 누르면 '탈퇴 처리가 되었습니다.' 출력 / 취소 버튼을 누르면 '탈퇴 취소되었습니다.' 출력

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
let grade = ""; // 등급

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
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

if (walk >= 6000) {
	alert('좋은 습관을 가지고 있습니다.');
} else {
	alert('운동이 필요합니다.');
}
```
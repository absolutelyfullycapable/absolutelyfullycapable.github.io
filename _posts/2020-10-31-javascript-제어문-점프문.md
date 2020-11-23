---

layout: post

title: "JavaScript 제어문 (3) 점프문"

description: "제어문 중 점프문에 대해 알아보자"

date: 2020-10-31

tags: JavaScript 제어문 점프문

comments: true

---





### **점프문**

- 프로그램에서 다른 위치로 이동하는 제어 구문
	- break문, continue문, etc...
- 문장에 라벨을 붙이면 break문이나 continue문을 실행한 후에 점프할 수 있는 위치가 됨

<br>

#### **1. label문**

- 제어를 직접 지정할 때 사용
- 자바스크립트에서는 모든 문장에 라벨을 붙일 수 있지만 **라벨로 점프할 수 있는 문장은 break문과 continue문**
	- break문은 switch문과 반복문 안에서만 사용 가능, continue문은 반복문 안에서만 사용 가능
- 프로그램 처리 구조에 주의해야 함
	- 너무 많이 사용하면 프로그램의 논리성이 약해지고, 순환 구조로 프로그래밍하면 무한 반복에 빠질 수 있음

<br>

##### **· 작성 방법**

```js
// 1. 기본 작성
라벨 이름: 문장
```

라벨 이름에는 모든 식별자를 사용할 수 있음

<br>

##### **· label문의 처리 흐름 예시**

```js
loop: while(true) {
    ...
    if(confirm("종료하시겠습니까?")) break loop;
    ...
}
```

break loop;를 실행하면 앞과 뒤 코드와 상관없이 loop라는 라벨이 붙은 while문에서 빠져나옴

<br>
<br>
- - -
<br>

#### **2. break문**

- 해당 블록을 강제적으로 벗어나 다음 문장을 처리하도록 할 때 사용
	- 제어를 블록 바깥으로 옮김
- **switch문이나 반복문 안에서만 사용 가능**
- break문을 실행하면 가장 안쪽에 있는 반복문이나 switch문에서 빠져나옴
- **반복문을 완전히 벗어나게 하는 역할**

<br>

##### **· 작성 방법**

```js
// 1. 기본 작성
break;

// 2. 점프할 라벨 지정 시
break 라벨 이름;
```

- 라벨을 지정한 break문은 주로 중첩된 반복문의 안쪽 반복문 안에서 전체 반복문을 빠져나올 때 사용
- 라벨을 지정한 break문은 switch문과 반복문에서 사용 가능
	- 라벨을 지정한 모든 문장에서 사용 가능
- 라벨을 지정한 break문을 실행하면 라벨이 붙은 문장 끝으로 점프
	- 이때 break문에서 지정한 라벨이 없으면 문법 오류 발생
- break문과 라벨 이름 사이에는 줄 바꿈 문자를 넣지 않도록 주의
	- 줄 바꿈 문자를 넣으면 자바스크립트 엔진이 내부적으로 세미콜론을 추가하므로 라벨을 지정하지 않은 break문으로 해석하기 때문

<br>
<br>

##### **· 간단한 예시**

1) 1부터 100까지의 수 중 3의 배수 합 구하기

```js
var x = 0, sum = 0;

while(1) {
   x += 3; // 3의 배수
   if(x > 100) {
       break;
   }
   sum += x;
   document.writeln(x);
}
document.write("<br>1부터 100까지의 수 중 3의 배수의 합은 " + sum + "이다.");
```

<br>

2) 배열 a와 배열 b에서 같은 값을 가진 요소를 발견하면 전체 반복문에서 빠져나오기

```js
var a = [2, 4, 6, 8, 10], b = [1, 3, 5, 6, 9, 11];

loop: for(var i = 0; i < a.length; i++) {
    for(var j = 0; j < b.length; j++) {
       if(a[i] == b[j]) {
           break loop;
       }
    }
}

console.log("a[" + i + "] = b[" + j + "]");
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F17fWY%2FbtqMfjMxBxH%2FiIPqgZ3fcAyjkn88jJqdB0%2Fimg.png)

<br>

3) 0에서 100까지 0을 포함한 3의 배수 출력 -> 20 이상인 3의 배수는 출력 제외

```js
for(i = 0; i <= 100; i += 3) {
    if(i >= 20) {
       break;
    }
    document.writeln(i);
}
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FvgIir%2FbtqMdWLhvoX%2F20im2mikM7GWjtBCFaXdTk%2Fimg.png)

<br>

4) 10번의 알림값을 가지고 있으나 3번의 알림 후 실행되지 않음

```js
for(i = 1; i <= 10; i++) {
    if(i >= 4) {
        break;
    }
    alert(i + "번째 알림입니다.");
}
alert("프로그램이 종료되었습니다.");
```

<br>
<br>
- - -
<br>

#### **3. continue문**

- if문과 함께 많이 사용
	- if문의 조건식이 참이면 continue 이후의 문장을 처리하지 않고 제어를 반복문의 시작 위치로 옮기는 역할
- **제어를 반복문의 시작 위치로 이동시킴**
- continue문을 실행하면 반복문 실행을 멈추고 반복을 새로 시작
	- 이때의 동작이 반복문에 따라 다름
		- **while문: 반복문의 처음으로 되돌아가 조건식을 다시 평가 / true면 반복문 처음부터 실행**
		- **do~while문: 중간을 건너뛰고 반복문의 마지막 조건식 평가 / true면 반복문 처음부터 실행**
		- **for문: 반복식을 실핸한 후에 조건식 평가 / true면 반복문 이어서 실행**
		- **for~in문: 반복문의 처음으로 되돌아감 / 지정한 변수에 할당되어 있는 프로퍼티의 다음 프로퍼티를 대상으로 작업 실행**

<br>

##### **· 작성 방법**

```js
// 1. 기본 작성
continue;

// 2. 점프할 라벨 지정 시
continue 라벨 이름;
```

- continue문은 라벨 지정 여부와 관계없이 **반복문 안에서만 사용 가능**

<br>
<br>

##### **· 간단한 예시**

1) for 중첩문과 함께 사용할 때

```js
var i, j;

outloop: // label name
for(i = 0; i < 3; i++) {
    inloop: // label name
    for(j = 0; j < 3; j++) {
        if(i === 1 && j === 0) {
            continue outloop;
        }
     document.write("i = " + i + ", j = " + j + "<br>");
    }
}
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbnbIpL%2FbtqMdinOMV8%2FzQII1EQ940TQFsrtrp5MyK%2Fimg.png)

<br>

2) 1부터 100까지 수 중 3의 배수의 합 구하기

```js
var sum = 0;

for(x = 1; x <= 100; x++) {
   if(x % 3 != 0) {
       continue;
   }
   sum += x;
   document.writeln(x);
}

document.write("<br>1부터 100까지의 수 중 3의 배수의 합은 " + sum + "이다.");
```

<br>

3) 배열 a 안에서 값이 0 이상인 요소의 값을 모두 더하기

```js
var a = [2, 5, -1, 7, -3, 6, 9];

for(var i = 0, sum = 0; i < a.length; i++) {
    if(a[i] < 0) {
        continue;
    }
    sum += a[i];
}
console.log(sum); // -> 29
```

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F0rMjr%2FbtqMckmiY7L%2Fzk1tWPqQMWxn1UhFC4Poik%2Fimg.png)
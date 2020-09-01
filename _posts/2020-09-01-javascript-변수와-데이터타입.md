---
layout: post
title: "Javascript 변수와 데이터 타입"
description: "변수와 데이터 타입에 대해 알아보자"
date: 2020-09-01
tags: javascript
comments: false
---

## 변수
- 변수: 문자나 숫자 같은 데이터 값을 담는 데이터 저장 공간 (메모리 공간)

<br>
- - -
<br>

### **변수 선언**
**var a;**

- var
	- 자바스크립트 키워드로 변수를 선언하기 위한 선언자
	- 변수는 반드시 선언하고 사용
- a
	- 변수 이름
	- 변수 이름으로 변수 값을 읽거나 쓸 수 있음

- 변수 여러 개를 한 문장으로 선언 시 쉽표 사용

	`` var a, b, c; ``

- 변수를 선언하기만 하면 변수 안에는 정의되지 않았음을 뜻하는 **undefined** 값 들어감

	```
    var a;
    console.log(x); // => undefined
    ```
    - console.log(); => 소괄호 안에 든 값을 콘솔 화면에 표시하라는 뜻
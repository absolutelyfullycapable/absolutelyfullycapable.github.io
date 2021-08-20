---
title: "JavaScript 이벤트 등록, 이벤트 버블링, 이벤트 캡처링, 이벤트 위임"
date: 2021-08-19
categories: [JavaScript]
comments: true
---

## 1. 이벤트 등록

  - 웹 애플리케이션에서 사용자의 입력을 받기 위해 필요한 기능
  - `addEventListener()` 웹 API 사용
    - 화면에서 동적인 기능을 추가하기 위해 자연스럽게 접하게 되는 기본적인 기능
    - 사용자의 입력에 따라 추가 동작을 구현할 수 있는 방법

<br />

## 2. 브라우저가 이벤트를 감지하는 방식

  **(1) 이벤트 버블링 (Event Bubbling)**

  > Trigger clicks all the way up

  - 특정 화면 요소에서 이벤트가 발생했을 때 해당 이벤트가 상위의 화면 요소들로 전달되어 가는 특성
  - **상위의 화면 요소**란?
    - HTML은 기본적으로 트리 구조를 가짐
    - 트리 구조상 한 단계 위에 있는 요소를 상위 요소라고 함

    ![이벤트 버블링](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbaZAab%2FbtrcHEjBZZ8%2FuhbwRRdFQSPgkmZS3WRAek%2Fimg.png)
    <br />
    ⬆️ 하위의 클릭 이벤트가 상위로 전달되어 가는 이미지

      ```html
      <body>
        <div class="one">
          <div class="two">
            <div class="three">
              <!-- 이벤트 발생 -->
            </div>
          </div>
        </div>
      </body>
      ```

      ```js
      const $divs = document.querySelectorAll("div");

      $divs.forEach(function(div) {
        div.addEventListener("click", logEvent);
      })
      function logEvent(e) {
        console.log(e.currentTarget.className);
      }
      ```

      > `forEach` 메소드는 인수로 받은 함수를 배열의 요소별로 한 번씩 실행함 <br />
      그 함수에는 인수 세 개(value, index, array)가 전달됨 (예시처럼 하나만 넣으면 그건 value)
      
      <br />

      ![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FMuKcO%2Fbtrczp2Ymis%2FggwFG4HkJxTHF9xMs8IMLk%2Fimg.png)
      <br />
      ⬆️ 예제 코드를 실행했을 때 나오는 결과

      > ❓ 왜 클래스명이 three인 div 태그 한 개만 클릭했을 뿐인데 왜 세 개의 이벤트가 발생되나요? <br />
      → 브라우저가 이벤트를 감지하는 방식 때문입니다! <br />
      <br />
      브라우저는 특정 화면 요소에서 이벤트가 발생했을 때 그 이벤트를 최상위에 있는 화면 요소까지 전파시킵니다. <br />
      따라서 (클래스명) three → two → one 순서대로 등록된 이벤트가 실행됩니다. <br />
      <br />
      여기서 클래스명이 two인 div 태그를 클릭했다면 two → one 순서대로 이벤트 실행됩니다.

  <br />

  **(2) 이벤트 캡처링 (Event Capturing)**

   - 이벤트 버블링과 반대 방향으로 진행되는 이벤트 전파 방식

      ![이벤트 캡처링](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FCDsSF%2FbtrcHFQmWwp%2FW1U3ginQvgHjlsN0Y6sKx1%2Fimg.png)
      <br />
      ⬆️ 클릭 이벤트가 발생한 지점을 찾아 내려가는 이미지

      ```html
      <body>
        <div class="one">
          <div class="two">
            <div class="three">
              <!-- 이벤트 발생 -->
            </div>
          </div>
        </div>
      </body>
      ```

      ```js
      const $divs = document.querySelectorAll("div");

      $divs.forEach(function(div) {
        div.addEventListener("click", logEvent, {
          capture: true // default 값은 false
        })
      });
      function logEvent(e) {
        console.log(event,currentTarget.className);
      }
      ```

      ![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbvITXR%2FbtrcEw1aAeL%2FMcUdOYSK8j4If0aeWhGejk%2Fimg.png)
      <br />
      ⬆️ 예제 코드를 실행했을 때 나오는 결과

<br />

## 3. 이벤트 전파 막기

  - `.stopPropagation()` 웹 API 사용

    ```js
    function logEvent(e) {
      e.stopPropagation();
      ...
    }
    ```

  - 이벤트 버블링의 경우에는 클릭한 요소의 이벤트만 발생시킴
    - 상위 요소로 이벤트를 전달하는 것을 막음(방해함)
  - 이벤트 캡처링의 경우에는 클릭한 요소의 최상위 요소의 이벤트만 동작시킴
    - 하위 요소들로 이벤트를 전달하지 않음

<br />
<br />

> 참고 문서 📝<br>
1. [이벤트 버블링, 이벤트 캡처 그리고 이벤트 위임까지](https://joshua1988.github.io/web-development/javascript/event-propagation-delegation/)

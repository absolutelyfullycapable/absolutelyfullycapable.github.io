---
title: "CSS3 flexible box (flexbox)"
date: 2021-02-06
categories: [CSS3]
comments: true
---

## **flexible box (flexbox)**

- 뷰포트나 요소의 크기가 정확하지 않을 때, 동적 변화가 필요할 때 사용
- 상속되지 않음
- 부모 박스(flex container)와 자식 박스(flex item)로 구성
    - flex container: flex-direction, flex-wrap, justify-content, align-items, align-content 속성과 함께 쓰임
    - flex item: flex, flex-grow, flex-shink, flex-basis, order 속성과 함께 쓰임
- 모던 브라우저(해결 방법을 사용하지 않고 웹 표준에 따라 웹사이트를 올바르게 렌더링하는 브라우저)를 대상으로 제작할 때 추천
    - [IE 10부터 지원](https://caniuse.com/?search=flex)
    - prefix()로 -ms-, -webkit-(일부 브라우저 버전) 필요 => 기본적으로 붙이는 것이 좋음
- `display:flex;` 사용 시 부모 박스(flex container) 주의 사항
    - `column-*`, `float`, `clear` 사용 불가
    - `position:realative`, `position:fixed` 사용 시 자식 박스(flex-item)에서 제외됨
    - 브라우저마다 구현이 다를 수 있으므로 margin과 padding 값은 %로 주지 않도록 해야 함

[참고 - nanalike 님 블로그](https://nykim.work/4?category=692675)

<br>

- - -

<br>

### **사용 방법**

1) 부모 박스에 `display:flex;` 요소 작성
- 아래 코드에서는 .container가 부모 박스에 해당

```html
<!DOCTYPE html>
<html lang='ko'>
    <head>
        <meta charset='utf-8'>
        <meta http-equiv='X-UA-Compatible' content='IE=edge'>
        <meta name='viewport' content='width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no'>
        <title>flexible box - display:flex</title>
        <style>
            body { margin:0; font-size:28px; font-weight:bold; text-align:center; }

             .container { border:#000 solid 4px; width:200px; display:flex; }

             .container div { height:100px; }
             .box1 { background-color:steelblue; }
             .box2 { background-color:tan; }
             .box3 { background-color:#eee; }
        </style>
    </head>

    <body>
        <div class="container"> <!-- flex container의 역할 -->
            <div class="box1">box1</div> <!-- flex item의 역할 -->
            <div class="box2">box2</div> <!-- flex item의 역할 -->
            <div class="box3">box3</div> <!-- flex item의 역할 -->
        </div>
    </body>
</html>
```

![result1](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FoRrBg%2FbtqVkLthBRh%2F6jemcZ6vivNVHbHpKIjfI1%2Fimg.png)

- `display:flex;` 작성 전

<br>

![result2](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FlR7aG%2FbtqVdMT1JxE%2FzNoaGHoOPjEZ3ywyk1K8k0%2Fimg.png)

- `display:flex;` 작성 후
    - 자식 박스들(flex item)이 자동으로 정렬되는 것을 확인할 수 있음

<br>

- - -

<br>

### display:inline-flex와 display:flex의 차이점

1) `display:inline-flex`

- 부모 박스는 인라인 성격을 가진 상태로 flex 적용됨

![example](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fcg0wJW%2FbtqXb1OuuQU%2FgFdrsb9VpKmLONN3xH5qV0%2Fimg.png)

2) `display:flex`

- 부모 박스는 블록 성격을 가진 상태로 flex 적용됨

![example](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbT4DLI%2FbtqWVRGYRS7%2FPkUv6qDexaN2kEUgJhYFak%2Fimg.png )

<br>

- - -

<br>

### flex-direction

![주축과 교차축](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcXykji%2FbtqVh8I3s7j%2FK2koykcLSZnuOghBzgUbw1%2Fimg.png)

- flexible box를 다루려면 주축과 교차축에 대한 정의가 선행되어야 함
- 주축은 `flex-direction` 속성에 의해 변할 수 있음 (교차축은 이에 수직인 축으로 지정됨)
- `flex-direction`은 자식 박스가 나열되는 방향을 변경할 때 사용
    - `flex-direction`은 4개의 값을 가짐
        - `row`: 기본값 / 주축은 가로, 왼쪽에서 오른쪽으로 배치
        - `row-reverse`: 주축은 가로, 오른쪽에서 왼쪽으로 배치
        - `column`: 주축은 세로, 위에서 아래로 배치
        - `column-reverse`: 주축은 세로, 아래에서 위로 배치

<br>

1) `row`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdlLq1O%2FbtqVddj4ZSC%2FkK5pU8a0egk5WyLlCvefDk%2Fimg.png)

2) `row-reverse`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F7Lue9%2FbtqVdNFq7DB%2FsY1q4PTMNyUsl7FH0PQCM1%2Fimg.png)

3) `column`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbJ6EoC%2FbtqVdMT2CmG%2FIckijQ0uhD0BAqZE8JOhIK%2Fimg.png)

4) `column-reverse`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FBQb1j%2FbtqU94aBZ8x%2F9NlWzIi0zmYJVVKPXeMLR0%2Fimg.png)

<br>

- - -

<br>

### flex-wrap

- 자식 박스(flex item)를 한 줄에 배치할지, 여러 줄로 나열할지 제어하는 요소
- `flex-wrap`은 3개의 값을 가짐
    - `nowrap`: 기본값, 자식 박스 한 줄 배치
    - `wrap`: 여러 줄 배치
    - `wrap-reverse`: 역방향 여러 줄 배치

```html
<!DOCTYPE html>
<html lang='ko'>
    <head>
        <meta charset='utf-8'>
        <meta http-equiv='X-UA-Compatible' content='IE=edge'>
        <meta name='viewport' content='width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no'>
        <title>flexible box: flex-wrap</title>
        <style>
            body { margin:0; font-size:28px; font-weight:bold; text-align:center; }

             .container { border:#000 solid 4px; width:200px; display:flex; }

             .container div { width:50%; height:100px; }
             .box1 { background-color:steelblue; }
             .box2 { background-color:tan; }
             .box3 { background-color:#eee; }
        </style>
    </head>

    <body>
        <div class="container"> <!-- flex container의 역할 -->
            <div class="box1">box1</div> <!-- flex item의 역할 -->
            <div class="box2">box2</div> <!-- flex item의 역할 -->
            <div class="box3">box3</div> <!-- flex item의 역할 -->
        </div>
    </body>
</html>
```

일 때

1) `nowrap`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F30AfI%2FbtqVbv6QMJR%2FuSxs0Y9kQqrkwky8ICpcQk%2Fimg.png)

2) `wrap`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbTqSDJ%2FbtqVbvy1wlr%2FRbFKxmRXiDWtKxlaoXu7L1%2Fimg.png)

3) `wrap-reverse`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbYs3OY%2FbtqVbWDakQc%2Fm30xekbfeXWLTWDYfgYog1%2Fimg.png)

<br>

- - -

<br>

### flex-flow

- 자식 박스의 방향과 여러 줄 배치를 동시에 지정하는 속성
- `flex-flow:(flex-direction 값) (flex-wrap 값);`으로 작성
- ex) `flex-wrap` 예시 코드에 `flex-flow:row-reverse wrap` 작성 시

    ![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fv1dRT%2FbtqVh7QXXRm%2FkIg5n7IUx3ef2dgfqVZQo1%2Fimg.png)

<br>

- - -

<br>

### justify-content

- **주축(main-axis)**을 따라 자식 박스를 정렬하는 방식 지정
    - 자식 박스와 여백을 **주축을 기준**으로 배치
- `justify-content`는 7개의 값을 가짐
    - `flex-start`: 기본값, 주축을 기준으로 시작점부터 배치
    - `flex-end`: 주축을 기준으로 끝점부터 배치
    - `center`: 주축을 기준으로 중앙 배치
    - `space-around`: 주축 기준으로 여백 포함 양 끝 배치
        - 자식 박스들의 **둘레**에 균일한 간격 만들어 줌
    - `space-between`: 주축을 기준으로 양 끝에 자식 박스를 붙이고 나머지 자식 박스를 동일한 간격으로 배치
        - 자식 박스들의 **사이**에 균일한 간격 만들어 줌
    - `space-evenly`: 주축을 기준으로 자식 박스의 **사이와 양 끝**에 균일한 간격을 만들어 배치
        - IE 지원하지 않음

```html
<!DOCTYPE html>
<html lang='ko'>
    <head>
        <meta charset='utf-8'>
        <meta http-equiv='X-UA-Compatible' content='IE=edge'>
        <meta name='viewport' content='width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no'>
        <title>flexible box: justify-content</title>
        <style>
            body { margin:0; font-size:28px; font-weight:bold; text-align:center; }

             .container { border:#000 solid 4px; width:500px; display:flex; }

             .container div { width:100px; height:100px; }
             .box1 { background-color:steelblue; }
             .box2 { background-color:tan; }
             .box3 { background-color:#eee; }
        </style>
    </head>

    <body>
        <div class="container"> <!-- flex container의 역할 -->
            <div class="box1">box1</div> <!-- flex item의 역할 -->
            <div class="box2">box2</div> <!-- flex item의 역할 -->
            <div class="box3">box3</div> <!-- flex item의 역할 -->
        </div>
    </body>
</html>
```

일 때

1) `flex-start`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbCclKf%2FbtqV8Fr9kW2%2FpJCPvfhQNGbBi4y9IZdVP1%2Fimg.png)

2) `flex-end`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdzToIC%2FbtqV2WVxhAc%2FUEdDjKkQ9B4XWp01jKJPBk%2Fimg.png)

3) `center`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fdhvrv3%2FbtqV36cvKuL%2FMZvuIspd9lxUH2isUuSUrk%2Fimg.png)

4) `space-around`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FuNaQ2%2FbtqVV23Pa7y%2F7SEFmKHkapQHeuvM0Ruzo1%2Fimg.png)

5) `space-between`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbXEoU9%2FbtqV08ITlrZ%2Foxc9TkviTIPS59PtZhK49K%2Fimg.png)

6) `space-evenly`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FtHpwJ%2FbtqV0FmHmxF%2FgGN4e9a5MGsVMfS4bhSzl1%2Fimg.png)

<br>

- 헷갈리는 `space-around`, `space-between`, `space-evenly` 비교하기!

![comparison](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fc2aWnf%2FbtqXb18zi6z%2Fm8iakwVQTkXK3kuxntYM21%2Fimg.jpg)

<br>

- - -

<br>

### align-items

- **교차축(cross-axis)**을 따라 자식 박스를 정렬하는 방식 지정
- `align-items`는 5개의 값을 가짐
    - `flex-start`: 교차축을 기준으로 시작점(top)에서 끝점(bottom)으로 배치
    - `flex-end`: 교차축을 기준으로 끝점(bottom)에서 시작점(top)으로 배치
    - `center`: 교차축을 기준으로 중앙 배치
    - `baseline`: 자식 박스 시작점에서 배치되는 글자 baseline에 맞춤

    ![baseline](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FosQZQ%2FbtqWU7QFZnE%2Fr2ezAIpvHsuD1MWgeh77v1%2Fimg.png)

    - `stretch`: 기본값, 높이값이 지정되지 않았을 때 자식 박스 확장 배치

```html
<!DOCTYPE html>
<html lang='ko'>
    <head>
        <meta charset='utf-8'>
        <meta http-equiv='X-UA-Compatible' content='IE=edge'>
        <meta name='viewport' content='width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no'>
        <title>flexible box: align-items</title>
        <style>
            body { margin:0; font-size:28px; font-weight:bold; text-align:center; }

             .container { border:#000 solid 4px; width:500px; height:300px; display:flex; }

             .container div { width:100px; height:100px; }
             .box1 { background-color:steelblue; }
             .box2 { background-color:tan; font-size:20px; }
             .box3 { background-color:#eee; font-size:15px; }
        </style>
    </head>

    <body>
        <div class="container"> <!-- flex container의 역할 -->
            <div class="box1">ex 1</div> <!-- flex item의 역할 -->
            <div class="box2">ex 2</div> <!-- flex item의 역할 -->
            <div class="box3">ex 3</div> <!-- flex item의 역할 -->
        </div>
    </body>
</html>
```

일 때

1) `flex-start`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FoSfGh%2FbtqWX4STdZX%2F2BXbrrWv1CyPlWXiyiKaKK%2Fimg.png)

2) `flex-end`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcNOHPd%2FbtqW1s62jJ7%2FAMkXbzBKXl73mWlxv3zcKK%2Fimg.png)

3) `center`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fm3qOc%2FbtqWXaFQyiP%2FOEcV9d4xelX1Uf1iIqFhCk%2Fimg.png)

4) `baseline`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fba8bht%2FbtqW4hc34sT%2F3EM8SBccC2PW308OJclTFK%2Fimg.png)

5) `stretch`

- 높이값이 지정되지 않았을 때 적용되므로 `.container div { width:100px; height:100px; }`에서 height 값을 제외한 후 봐야 함

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbFhG5H%2FbtqWX4yBBXn%2FjnsD9KhSBsTapgGS7Jzznk%2Fimg.png)

<br>

- - -

<br>

### align-self

- `align-items` 속성의 개별 배치
    - 속성값도 같음
- 자식 박스에 적용

```html
<!DOCTYPE html>
<html lang='ko'>
    <head>
        <meta charset='utf-8'>
        <meta http-equiv='X-UA-Compatible' content='IE=edge'>
        <meta name='viewport' content='width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no'>
        <title>flexible box: align-self</title>
        <style>
            body { margin:0; font-size:28px; font-weight:bold; text-align:center; }

             .container { border:#000 solid 4px; margin:20px; width:500px; height:300px; display:flex; justify-content:space-between; align-items:center; }

             .container div { width:20%; }
             .box1 { background-color:steelblue; }
             .box2 { background-color:tan; }
             .box3 { background-color:#eee; }
        </style>
    </head>

    <body>
        <div class="container"> <!-- flex container의 역할 -->
            <div class="box1">box1</div> <!-- flex item의 역할 -->
            <div class="box2">box2</div> <!-- flex item의 역할 -->
            <div class="box3">box3</div> <!-- flex item의 역할 -->
        </div>
    </body>
</html>
```

일 때 결과

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F1uXZz%2FbtqWUMy8JTf%2F82e4DdejnYBiYUJrsD01wk%2Fimg.png)

1) .box1에 `align-self:flex-start` 적용 시

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdVt7LU%2FbtqW1szc8RI%2Fku8kdrNt0XqofDEz17r150%2Fimg.png)

2) .box3에 `align-self:flex-end` 추가 적용 시

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdFh6qe%2FbtqWWsGJUvC%2FkF1hsILZnkyIBUo8zj1h3K%2Fimg.png)

<br>

- - -

<br>

### align-content

- `flex-wrap:wrap`이 설정된 상태에서 **교차축(cross-axis)**을 따라 두 줄 이상의 자식 박스(flex item)를 정렬하는 방식 지정
- `align-content`는 7개의 값을 가짐
    - `flex-start`: 교차축을 기준으로 시작점(top)에서 시작
    - `flex-end`: 교차축을 기준으로 끝점(bottom)에서 시작
    - `center`: 교차축을 기준으로 중앙 배치
    - `space-around`: 교차축 여백 포함 양 끝을 기준으로 배치
    - `space-between`: 교차축의 양 끝을 기준으로 자식 박스(flex items)를 배치하고, 남은 자식 박스(flex items)를 여백 포함 동일한 간격으로 배치
    - `space-evenly`: 교차축을 기준으로 끝점(bottom)에서 시작
        - IE 지원하지 않음
    - `stretch`: 기본값, 높이값이 지정되지 않았을 때 자식 박스(flex items) 확장 배치

```html
<!DOCTYPE html>
<html lang='ko'>
    <head>
        <meta charset='utf-8'>
        <meta http-equiv='X-UA-Compatible' content='IE=edge'>
        <meta name='viewport' content='width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no'>
        <title>flexible box: align-content</title>
        <style>
            body { margin:0; font-size:28px; font-weight:bold; text-align:center; }

             .container { border:#000 solid 4px; width:500px; height:300px; display:flex; flex-wrap:wrap; }

             .container div { width:50%; }
             .box1 { background-color:steelblue; }
             .box2 { background-color:tan; }
             .box3 { background-color:#eee; }
        </style>
    </head>

    <body>
        <div class="container"> <!-- flex container의 역할 -->
            <div class="box1">box1</div> <!-- flex item의 역할 -->
            <div class="box2">box2</div> <!-- flex item의 역할 -->
            <div class="box3">box3</div> <!-- flex item의 역할 -->
        </div>
    </body>
</html>
```

일 때

1) `flex-start`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbSfy4D%2FbtqW8Ho15xV%2FIcLYj6QiWBiHIhHnmRb1M1%2Fimg.png)

2) `flex-end`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FsW5LS%2FbtqW4gL26YI%2Feau7TzPeOm6VQBWTKWoXQ1%2Fimg.png)

3) `center`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FQKTLT%2FbtqW8FEKzY8%2FwNhzSkPPf5tGlhDafIJ5K1%2Fimg.png)

4) `space-around`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FpD1I3%2FbtqWXaeMW21%2FPNpaLtxtlmj0i445VIKuT1%2Fimg.png)

5) `space-between`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F5e1BD%2FbtqWWtr8F9a%2F9fTbBIYD3FQVtFF14D2vL0%2Fimg.png)

6) `space-evenly`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fm8CfW%2FbtqW1r784kk%2F6E87L1Fid5Z4fH7dJG0ya0%2Fimg.png)

7) `stretch`

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcTscFb%2FbtqXb1AK3zF%2FAseKRJojLTVFEO3tDRaFl0%2Fimg.png)

<br>

- - -

<br>

### order

- 자식 박스 배치 순서 결정
- `display:flex;` 값 있어야 `order` 적용 가능
- 정렬 순서는 오름차순 `order` 값
    - 같은 값일 경우 소스 코드의 순서대로 정렬
- 논리적인 순서나 탭 순서와는 상관 없이 **화면에 보이는 순서에만** 영향 줌
    - 비시각적 매체에 적용해서는 안 됨

[참고](https://developer.mozilla.org/ko/docs/Web/CSS/order)

```html
<!DOCTYPE html>
<html lang='ko'>
    <head>
        <meta charset='utf-8'>
        <meta http-equiv='X-UA-Compatible' content='IE=edge'>
        <meta name='viewport' content='width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no'>
        <title>flexible box: order</title>
        <style>
            body { margin:0; font-size:20px; font-weight:bold; text-align:center; }
            .container { border:#000 solid 4px; width:600px; height:300px; display:flex; justify-content:space-around; align-items:center; }
            .container div { width:15%; border:1px solid #000; }
            .box1 { background-color:steelblue; order:5; }
            .box2 { background-color:tan; order:4; }
            .box3 { background-color:#eee; order:3; }
            .box4 { background-color:rosybrown; order:2; }
            .box5 { background-color:antiquewhite; order:1; }
        </style>
    </head>

    <body>
        <div class="container"> <!-- flex container -->
            <div class="box1">box1</div> <!-- flex item -->
            <div class="box2">box2</div> <!-- flex item -->
            <div class="box3">box3</div> <!-- flex item -->
            <div class="box4">box4</div> <!-- flex item -->
            <div class="box5">box5</div> <!-- flex item -->
        </div>
    </body>
</html>
```

일 때 결과

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FddYwee%2FbtqWXa0k6mZ%2FnQ2kTCPKrTlKtwi5pADzb1%2Fimg.png)

<br>

- - -

<br>

### flex-grow

- 자식 박스에 적용
    - 부모 박스에 여백이 있는 경우 지정한 값에 따라 자동적으로 늘어나 여백을 채우게 됨
- 자식 박스가 늘어나는 배율 지정
    - 자식 박스의 증가 비율을 설정하는 단축 속성
- 숫자가 클수록 더 큰 영역 가짐
- 가변값이 아니거나 0인 경우 적용되지 않음
- 정수(+)만 가능, 음수(-)는 불가능
- 개별로 지정한 경우, 지정하지 않은 자식 박스는 최소치가 됨
- IE 10에서는 `-ms-flex-positive` 사용

<br>

- 간단한 예시

```html
<!DOCTYPE html>
<html lang='ko'>
    <head>
        <meta charset='utf-8'>
        <meta http-equiv='X-UA-Compatible' content='IE=edge'>
        <meta name='viewport' content='width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no'>
        <title>flexible box: flex-grow</title>
        <style>
            ul { list-style:none; margin:10px; padding:0; text-align:center; font-weight:bold; font-size:25px; background-color:#eee; display:flex; width:600px; height:60px; }
            li { width:0; }
            li:first-child { background-color:steelblue; }
            li:nth-child(2) { background-color:tan; }
            li:last-child { background-color:rosybrown; }

            .box1 > li { flex-grow:0; } /* 기본값, 커지지 않음 */

            .box2 > li { flex-grow:1; } /* 균일하게 커져서 부모 요소를 채움 */

            .box3 > li:first-child { flex-grow:1; } /* 1/5 == 20% 차지 */
            .box3 > li:nth-child(2) { flex-grow:2; } /* 2/5 == 40% 차지 */
            .box3 > li:last-child { flex-grow:2; } /* 2/5 == 40% 차지 */

            .box4 > li:first-child { flex-grow:1; } /* 1/4 == 25% 차지 */
            .box4 > li:nth-child(2) { flex-grow:2; } /* 2/4 == 50% 차지 */
            .box4 > li:last-child { flex-grow:1; } /* 1/4 == 25% 차지 */
        </style>
    </head>

    <body>
        <h2>flex-grow: 0</h2>
        <ul class="box1"> <!-- flex container -->
            <li>item 1</li> <!-- flex item -->
            <li>item 2</li> <!-- flex item -->
            <li>item 3</li> <!-- flex item -->
        </ul>
        <h2>flex-grow: 1</h2>
        <ul class="box2"> <!-- flex container -->
            <li>item 1</li> <!-- flex item -->
            <li>item 2</li> <!-- flex item -->
            <li>item 3</li> <!-- flex item -->
        </ul>
        <h2>flex-grow: 1 / flex-grow: 2</h2>
        <ul class="box3"> <!-- flex container -->
            <li>item 1</li> <!-- flex item -->
            <li>item 2</li> <!-- flex item -->
            <li>item 3</li> <!-- flex item -->
        </ul>
        <h2>flex-grow: 1 / flex-grow: 2 / flex-grow: 1</h2>
        <ul class="box4"> <!-- flex container -->
            <li>item 1</li> <!-- flex item -->
            <li>item 2</li> <!-- flex item -->
            <li>item 3</li> <!-- flex item -->
        </ul>
    </body>
</html>
```

일 때 결과

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F1KUEf%2FbtqWX4S6Pxx%2F9Rg7IMuyGKm8PKuOyOKW41%2Fimg.png)

<br>

- - -

<br>

### flex-shirink

- 자식 박스에 적용
- 자식 박스가 줄어드는 배율 지정
    - 자식 박스의 감소 비율을 설정하는 단축 속성
- 숫자가 클수록 더 큰 영역이 감소됨
- 가변값이 아니거나 0인 경우 적용되지 않음
- IE 10에서는 `-ms-flex-negative`로 사용

<br>

- 간단한 예시

```html

<!DOCTYPE html>
<html lang='ko'>
    <head>
        <meta charset='utf-8'>
        <meta http-equiv='X-UA-Compatible' content='IE=edge'>
        <meta name='viewport' content='width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no'>
        <title>flexible box 10: flex-shrink</title>
        <style>
            ul { list-style:none; margin:10px; padding:0; text-align:center; font-weight:bold; font-size:25px; outline:6px solid #000; display:flex; width:600px; height:60px; }
            li { width:300px; }
            li:first-child { background-color:steelblue; }
            li:nth-child(2) { background-color:tan; }
            li:last-child { background-color:rosybrown; }

            .box1 > li { flex-shrink:0; } /* 작아지지 않고 그냥 그대로 넘침 (자기가 가지고 있는 크기대로) */

            .box2 > li { flex-shrink:1; } /* 기본값, 균일하게 작아져서 부모 요소를 채움 */

            .box3 > li:first-child { flex-shrink:1; } /* 1/5 li:300px + (-300/5)*1 = 240 */
            .box3 > li:nth-child(2) { flex-shrink:2; }/* 숫자가 크면 더 많은 값이 감소 */
            /* 1/5 li:300px + (-300/5)*2 = 180 */
            .box3 > li:last-child { flex-shrink:2; }
            /* 1/5 li:300px + (-300/5)*2 = 180 */

            .box4 > li:first-child { flex-shrink:0; } /* 300px */
            .box4 > li:nth-child(2) { flex-shrink:1; } /* 150px */
            .box4 > li:last-child { flex-shrink:1; } /* 150px */
        </style>
    </head>

    <body>
        <h2>flex-shrink: 0</h2>
        <ul class="box1"> <!-- flex container -->
            <li>item 1</li> <!-- flex item -->
            <li>item 2</li> <!-- flex item -->
            <li>item 3</li> <!-- flex item -->
        </ul>
        <h2>flex-shrink: 1 (기본값)</h2>
        <ul class="box2"> <!-- flex container -->
            <li>item 1</li> <!-- flex item -->
            <li>item 2</li> <!-- flex item -->
            <li>item 3</li> <!-- flex item -->
        </ul>
        <h2>flex-shrink: 1 / flex-shrink: 2</h2>
        <ul class="box3"> <!-- flex container -->
            <li>item 1</li> <!-- flex item -->
            <li>item 2</li> <!-- flex item -->
            <li>item 3</li> <!-- flex item -->
        </ul>
        <h2>flex-shrink: 0 / flex-shrink: 1</h2>
        <ul class="box4"> <!-- flex container -->
            <li>item 1</li> <!-- flex item -->
            <li>item 2</li> <!-- flex item -->
            <li>item 3</li> <!-- flex item -->
        </ul>
    </body>
</html>
```

일 때 결과

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FpCCKj%2FbtqWW91uLD1%2Fh5mxbQC4mKGFMk6Sbi1SNK%2Fimg.png)

<br>

- - -

<br>

### flex-basis

- 자식 박스에 적용
- 자식 박스의 기본 너비값 설정
    - 자식 박스의 기본 배율 지정 (자식 박스의 기본 비율을 설정하는 단축 속성)
    - flex-grow나 flex-shrink 값을 주기 위한 기준
        - `flex-basis:100px;`: 100px의 크기를 기준으로 잡고 나머지 부분을 `flex-grow`와 `flex-shrink`가 조절
        - `flex-basis:0;`: 전 영역을 `flex-grow`와 `flex-shrink`가 조절
        - `flex-basis:auto;`: 콘텐츠가 가진 영역을 뺀 나머지 부분을 `flex-grow`와 `flex-shrink`가 조절
    - `flex-direction`이 `row`일 때는 너비, `column`일 때는 높이
- auto인 경우 width, height 등의 속성으로 너비 설정 가능하나 단위값이 주어진 경우 설정할 수 없음
- width, height 값과 flex-basis 값을 선언하는 것은 결과적으로 동일한 값을 만듦
    - width 값과 flex-basis 값을 동시 선언하는 경우 flex-basis 값이 우선 적용 -> 하지만 같이 잘 쓰지 않음

<br>

- 간단한 예시

```html

<!DOCTYPE html>
<html lang='ko'>
    <head>
        <meta charset='utf-8'>
        <meta http-equiv='X-UA-Compatible' content='IE=edge'>
        <meta name='viewport' content='width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no'>
        <title>flexible box: flex-basis</title>
        <style>
            ul { list-style:none; margin:10px; padding:0; text-align:center; font-weight:bold; font-size:25px; background-color:#eee; outline:6px solid #000; display:flex; width:600px; height:60px; }

            li:first-child { background-color:steelblue; }
            li:nth-child(2) { background-color:tan; }
            li:last-child { background-color:rosybrown; }

            .box1 > li { flex-basis:auto; } /* 기본값, li의 width 값 선언 시 선언된 width 값 적용, width 값 없으면 콘텐츠가 가진 만큼 width 값 설정됨 */
            .box2 > li { flex-basis:0; } /* flex-basis 값을 안 준다는 뜻 -> 여백 X */
            .box3 > li { flex-basis:150px; }
            .box4 > li { flex-basis:300px; } /* 기본값인 flex-shrink:1; 덕분에 넘치지 않음 */
        </style>
    </head>

    <body>
        <h2>flex-basis: auto (기본값)</h2>
        <ul class="box1"> <!-- flex container -->
            <li>item 1</li> <!-- flex item -->
            <li>item 2</li> <!-- flex item -->
            <li>item 3</li> <!-- flex item -->
        </ul>
        <h2>flex-basis: 0</h2>
        <ul class="box2"> <!-- flex container -->
            <li>item 1</li> <!-- flex item -->
            <li>item 2</li> <!-- flex item -->
            <li>item 3</li> <!-- flex item -->
        </ul>
        <h2>flex-basis: 150px</h2>
        <ul class="box3"> <!-- flex container -->
            <li>item 1</li> <!-- flex item -->
            <li>item 2</li> <!-- flex item -->
            <li>item 3</li> <!-- flex item -->
        </ul>
        <h2>flex-basis: 300px; ==> 기본값으로 flex-shrink:1; 설정되어 있기 때문에 부모 요소를 넘기지 못하고 자동으로 작아짐</h2>
        <ul class="box4"> <!-- flex container -->
            <li>item 1</li> <!-- flex item -->
            <li>item 2</li> <!-- flex item -->
            <li>item 3</li> <!-- flex item -->
        </ul>
    </body>
</html>
```

일 때 결과

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fblob4Z%2FbtqWWt64THh%2FpVuD19oMEonyjGOre4F8W0%2Fimg.png)

<br>

- - -

<br>

### flex-grow와 flex-basis

- `flex-shrink`와 `flex-basis`가 만나면 계산이 복잡해져 같이 잘 사용하지 않고, 사용하더라도 각각 사용
- `flex-grow`와 `flex-basis`는 같이 잘 사용하는 편

<br>

- 간단한 예시

```html
<!DOCTYPE html>
<html lang='ko'>
    <head>
        <meta charset='utf-8'>
        <meta http-equiv='X-UA-Compatible' content='IE=edge'>
        <meta name='viewport' content='width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no'>
        <title>flexible box: flex-grow와 flex-basis</title>
        <style>
            ul { list-style:none; margin:10px; padding:0; text-align:center; font-weight:bold; font-size:25px; background-color:#eee; outline:6px solid #000; display:flex; width:600px; height:60px; }

            li:first-child { background-color:steelblue; flex-grow:1; }
            li:nth-child(2) { background-color:tan; flex-grow:1; }
            li:last-child { background-color:rosybrown; flex-grow:2; }

            .box1 > li { flex-basis:auto; } /* 자식 박스의 콘텐츠 크기에 맞춰 flex-grow 비율 설정 */
            .box2 > li { flex-basis:0; } /* 고정 비율에 맞춰 flex-grow 설정, flex item 크기에 맞춰 비율 설정 */
            .box3 > li { flex-basis:100px; } /* 고정값 100px에 맞춰 flex-grow 설정 */
        </style>
    </head>

    <body>
        <h2>flex-basis: auto (기본값)</h2>
        <ul class="box1"> <!-- flex container -->
            <li>item 1</li> <!-- flex item -->
            <li>2</li> <!-- flex item -->
            <li>flex item 3</li> <!-- flex item -->
        </ul>
        <h2>flex-basis: 0 ==> 부모의 크기가 600px일 때 1(150):1(150):2(300) 비율 가짐</h2>
        <ul class="box2"> <!-- flex container -->
            <li>item 1</li> <!-- flex item -->
            <li>2</li> <!-- flex item -->
            <li>flex item 3</li> <!-- flex item -->
        </ul>
        <h2>flex-basis: 100px</h2>
        <ul class="box3"> <!-- flex container -->
            <li>item 1</li> <!-- flex item -->
            <li>2</li> <!-- flex item -->
            <li>flex item 3</li> <!-- flex item -->
        </ul>
    </body>
</html>
```

일 때 결과

![result](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcNGn4t%2FbtqW1tkUJNh%2FjvcxcR7Jrh5OSeQP7uoSxK%2Fimg.png)

▼ 이해하기 쉽게 설명하자면...

![explain](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbD7MaI%2FbtqXgnDScHx%2FECBTFsKkz8VsadkbmoJhHK%2Fimg.jpg)
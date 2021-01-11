---
title: "Bootstrap 호환성"
date: 2021-01-11
categories: [Bootstrap]
comments: true
---

# 부트스트랩의 호환성

<br/>

- 기본적으로 모든 주요 브라우저와 플랫폼의 최신 버전 지원
- 부트스트랩의 호환성에 관한 사소한 차이점은 [여기](https://getbootstrap.com/docs/4.5/getting-started/introduction)에서 확인

<br/>

- - -

<br/>

### 모바일 브라우저

- Opera Mini, Opera Mobile의 Turbo 모드, UC Browser Mini, Amazon Silk와 같은 프록시 브라우저는 지원 안 됨

|  | Chrome | Firefox | Safari | Android Brower & WebView | Microsoft Edge |
|--------|--------|--------|--------|--------|--------|
|  Android | 지원됨 | 지원됨 | 해당 없음 | Android 5.0 이상 지원됨  | 해당 없음 |
| iOS | 지원됨 | 지원됨 | 지원됨 | 해당 없음 | 해당 없음 |
| Window 10 Mobile | 해당 없음 | 해당 없음 | 해당 없음 | 해당 없음 | 지원됨 |

<br/>

### 데스크탑 브라우저

- Firefox의 경우 최신 표준 안정 버전 외 최신 ESR (Extended Support Release) 버전 지원
- Internet Explorer 10(IE10) 이상 지원
    - IE9 이하는 지원하지 않음
        - 만약 IE8이나 IE9의 지원이 필요하다면 부트스트랩 3을 사용하도록 권장되지만 최근 IE8이나 IE9는 거의 쓰지 않음
        - IE8은 미디어쿼리를 지원하기 위해 Respond.js가 요구됨
    - 일부 HTML5 요소 및 CSS3 속성은 IE10에서도 지원되지 않음
        - 전체 기능에 대해 미리 정의된 속성 필요하다는 점 항상 생각!
    - IE는 웹 표준을 따르지 않아 크로스 브라우징에서 문제가 생길 수 있음을 파악해야 함
- Chromium 및 Linux 용 Chrome, Linux 용 Firefox 및 Internet Explorer 9에서 충분히 보이고 작동될 수 있음 (비공식적)

|  | Chrome | Firefox | Internet Explorer | Microsoft Edge | Opera | Safari |
|--------|--------|--------|--------|--------|--------|--------|
| Mac | 지원됨 | 지원됨 | 해당 없음 | 해당 없음 | 지원됨 | 지원됨 |
| Window | 지원됨 | 지원됨 | 지원됨 (IE10 이상) | 지원됨 | 지원됨 | 지원되지 않음 |




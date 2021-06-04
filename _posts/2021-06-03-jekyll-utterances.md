---
title: "Jekyll 블로그에 Utterances로 댓글 기능 추가하기 (+ 적용되지 않을 때 해결법)"
date: 2021-06-03
categories: [etc]
comments: true
---

## 제가 Utterances를 사용한 이유는요..
<br>
시작하기 앞서 저는 작년 9월부터 Jekyll 블로그를 사용하다가 `댓글 기능이 없어 타인과 글에 대해 소통하기 불편할 것 같다`의 이유로 올해 4월 다른 플랫폼으로 블로그를 이사한 적이 있습니다. (물론 다른 사람에게 보여 주거나 소통을 최우선으로 두고 작성한 글들이 아니라 스스로 공부한 내용을 정리한 형식이긴 하지만요..)<br>
<br>
이사한 블로그는 잘 구축되어 있는 플랫폼이라 여러 방면에서 운영하기 좋았지만 작년부터 남긴 기록이 아깝기도 했고, 결정적으로 `Jekyll 블로그도 댓글 기능을 추가할 수 있다`는 사실을 알고 '새로 시작하는 것도 좋지만 있던 블로그를 잘 관리해 보자' 생각이 들어 다시 돌아오게 되었습니다.<br>
<br>
Jekyll 블로그에 댓글 기능을 추가할 수 있는 프로그램은 [Disqus](https://disqus.com/), [Utterances](https://github.com/apps/utterances), [Gitalks](https://github.com/gitalk/gitalk) 등등 여러 개가 있지만 그 중에서도 쉽게 설치할 수 있고, UI가 괜찮고, 댓글을 Repo Issue로 관리할 수 있는 **Utterances**을 사용했습니다.<br>
<br>
Utterances 사용 방법에 대한 글은 구글링만 해도 정말 많이 나오지만, 그래도 스스로 정리하면서 같은 문제로 댓글 기능 추가에 어려움을 느끼고 있는 분들에게 '이런 문제 때문일 수도 있어요!'라고 알려 주고 싶어 글을 작성합니다.<br>
<br>
**포스팅 내용에 대한 피드백은 언제나 환영입니다! 😎**

<br>
<hr>
<br>

## 그래서 Utterances가 뭔가요?
<br>
![Utterances](https://blog.kakaocdn.net/dn/l7y0h/btq6vxduluD/1aXOWbNJLLK4ub4kUwmifK/img.png)

<br>

말 그대로 Github Issue를 기반으로 만든 댓글 위젯입니다.<br>
<br>
[Github issue search API](https://developer.github.com/v3/search/#search-issues)를 사용하여 `url`, `pathname`, 혹은 `title`를 기반한 페이지 관련 Issue를 찾아 Github Issue로 관리합니다.(댓글을 보는 것뿐만 아니라 작성, 삭제 등등 여러 기능들이 가능하더라고요? 😯 와우..)<br>
<br>
광고가 없는 오픈 소스라 Disqus 대체로 많이 사용하는 것 같습니다.<br>

<br>
<hr>
<br>

## 그러면 이제 Utterances를 적용해 봅시다!

<br>

### 1. Github에 신규 Repository 만들기 (생략 가능)

![댓글 관리용 신규 Repository](https://blog.kakaocdn.net/dn/C2O9I/btq6rn2KKXe/KA79o2hPKd2RD9k8Kfze9K/img.png)

댓글을 관리하는 신규 Repository를 만듭니다. **(기존 블로그 Repo에서 한꺼번에 관리하고 싶다면 새로 만들지 않고 블로그 Repo를 연결해도 됩니다!)**<br>
보통 이름은 `blog-comments`나 `blog_comments`로 많이 만드시더라구요. 꼭 저렇게 해야 하는 건 아니니 각자 원하는 대로 작성해 주시면 될 것 같습니다.<br>
<br>
여기서 주의할 점은 ✨ 꼭 **Public**으로 만드셔야 합니다! ✨<br>

<br>
<br>

### 2. Utterances 설치하기

먼저 [Utterances 사이트](https://github.com/apps/utterances)로 이동합니다.

![Install Utterances 1](https://blog.kakaocdn.net/dn/bYQHbm/btq6lYjkRut/VTtEOjNQYBzQzPtxi2R5q0/img.png)

Install 버튼을 누르면 요런 페이지가 뜨는데요.

![Install Utterances 2](https://blog.kakaocdn.net/dn/MdXfb/btq6q1UQkOR/4jRfdCKLgMorysNa3RpEp1/img.png)

제 Github에 있는 모든 Repo에 적용하지 않을 거고, 댓글 관리용 Repo를 만들었기 때문에 **Only select repositories**를 선택하고 앞서 만든 댓글 관리용 Repo를 선택합니다.<br>
댓글 관리용 Repo를 만들지 않았다면 Utterances와 연결할 Repo를 선택하면 됩니다!<br>
<br>
그 후 Install 버튼 다시 클릭!

<br>
<br>

그러면 아래 보이는 사이트로 이동하게 됩니다.

![Utterances 사이트](https://blog.kakaocdn.net/dn/cdnI2C/btq6n6VJD4z/gRovZi7Rbv6GzNwc1uXtak/img.png)

해당 페이지에서는 Utterances에 대한 소개와 Repo 지정, Issue Mapping 방법, Issue label 및 Theme 옵션 설정, Utterances를 활성화해 줄 스크립트가 나옵니다.<br>
<br>
차근차근 완성해 볼까요?

<br>

#### 1) Utterances와 연결할 Repo 작성하기

<br>

![Repo](https://blog.kakaocdn.net/dn/bmI2RJ/btq6uIT59DR/D9h61keqgp9VCmYgYvpSk1/img.png)

Repo는 앞서 만든 댓글 관리용 Repo를 작성해 주시면 됩니다.

<br>
<br>

#### 2) Issue Mapping 방법 선택하기

<br>

![Issue Mapping](https://blog.kakaocdn.net/dn/deD2jr/btq6rwUBSSd/QyKeYoPKtjTn0eZG3OOej1/img.png)

그 다음은 글과 Issue를 어떻게 매핑할 건지 선택하는 창이 나오는데요. (어떤 건지 설명) 여섯 가지 선택지 중 각자 블로그에 맞는 선택지로 고르면 됩니다!<br>
참고로 저는 `Issue title contains page pathname`을 선택했어요.

<br>
<br>

#### 3) Issue label 작성하기

<br>

![Issue label](https://blog.kakaocdn.net/dn/coPtju/btq6rnwo592/d3ZRUQj1BHhaHoMCO1CdI1/img.png)

그 후 Issue label을 설정해 줍니다. 설정된 label은 댓글 issue 뒤에 붙습니다.<br>
이모지도 지원되는 걸 보면 이 부분은 각자 잘 알아볼 수 있는 방법으로 자유롭게 설정 가능한 것 같아요.

<br>
<br>

#### 4) Utterances theme 선택하기

<br>

![Utterances Theme](https://blog.kakaocdn.net/dn/bmFTd9/btq6uJlezvP/NuqBcilPtbMNZKjwxGpuQ1/img.png)

Theme 옵션은 여러 개가 있습니다. 이것 또한 각자 블로그에 맞게 선택하시면 됩니다.<br>
저는 심플 이즈 더 베스트라 생각하여 가장 기본인 Github Light로 설정했습니다. 😎

<br>
<br>

#### 5) Utterances script 복사 후 댓글 기능이 필요한 페이지에 붙여넣기

<br>

![Utterances Script](https://blog.kakaocdn.net/dn/n0DUe/btq6q2sFYJk/YCXwewvvlhBkv8eOmFfrlK/img.png)

그 후 설정에 맞게 완성된 script를 복사합니다.<br>
저는 포스트에만 댓글을 설정해 줄 거기 때문에 복사한 script를 `_layouts/post.html`에 넣었습니다. (댓글 기능이 필요한 페이지에 넣으면 될 것 같아요!)<br>
<br>
신나게 등록하고 Jekyll 블로그를 열어 댓글창이 생긴 걸 확인한 뒤, 테스트 댓글을 작성하려고 Sign with Github 버튼을 누르는 순간 이런 화면을 마주했습니다.

<br>
<br>
<br>

![404 Error](https://blog.kakaocdn.net/dn/bEAz5V/btq6oDy0mwn/D6rcMuwHSfc9crijW1LHmk/img.png)

왜.. 뭐가 문제인데.. 😥

<br>
<br>

### 3. 왜 적용이 안 됐을까?

<br>

보통의 경우에 복사한 script를 넣은 뒤 정상적으로 작동해야 합니다. 그런데 저는 (단계들을 잘 밟으면서 온 것 같은데..) Github 연동 로그인이 되지 않아 애를 먹었습니다.<br>
구글링을 해 봐도 비교적 쉽게 설치할 수 있는 거라 그런지 저와 같은 문제를 겪고 있는 사람을 찾기 어렵더라구요. (물론 제 구글링 실력이 나빠서 못 발견했을 수도 있..)<br>
<br>
그래서 제가 설치할 때 참고한 [HAHWUL 님 블로그 포스팅](https://www.hahwul.com/2020/08/08/jekyll-utterances/)에 문의 댓글을 우다다 달았는데요..

<br>

![HAHWUL 님 댓글 1](https://blog.kakaocdn.net/dn/IdSoO/btq6w60EfZB/KKKvlKVJ4beXFHLM0j34KK/img.png)
![HAHWUL 님 댓글 2](https://blog.kakaocdn.net/dn/bnqmKS/btq6qRElilW/hgx3XAzWCu95DB44mQenx0/img.png)

세상에 😱!!!!!<br>
<br>
이 Issue 때문에 404 Error 페이지가 뜨는 것 같다고 [링크](https://github.com/utterance/utterances/issues/443#issuecomment-774536781)와 함께 해결 방법을 알려 주셨습니다.. 😮<br>
(너무 친절하고 자세하게 설명해 주셔서 감동받았던.. 이 포스팅을 통해 다시 감사의 인사를 드립니다. (--)(__) ♡)<br>
<br>
생각보다 해결하기 어려운 문제는 아니라 안심하며 바로 수정에 들어갔습니다.<br>

<br>

![404 Error](https://blog.kakaocdn.net/dn/ZCjNM/btq6rvmc4ce/hkke2aDElKaD838gjdxF70/img.png)

왜.. 뭐가 문제인데.. 😥 22<br>
<br>
그런데 분명 파일명을 전부 소문자 영어로 바꾸었는데도 작동이 되지 않았습니다.<br>
하지만 이제는 어떤 부분이 잘못되면 문제가 발생하는지 알았으니 그 부분을 다시 보기로 했습니다.

<br>

![연결된 링크와 실제 페이지 링크가 달라서 생겼던 문제였음!](https://blog.kakaocdn.net/dn/dPtzn2/btq6qoOCyMH/xpZkKw8LFUFmyYkElhdMEk/img.png)

연결된 링크와 실제 페이지 링크가 아직도 서로 달라 그런 거였습니다. 저 `/test`는 도대체 어디서 나온 아이일까.. 싶어 가장 기본적인 내용을 담고 있는 `_config.yml`부터 확인했습니다.

<br>

![_config.yml에서 발견한 오류](https://blog.kakaocdn.net/dn/cpT4Gx/btq6n6anIxL/N4QgTFOFjesXgdgBwr1lZK/img.png)

범인을 드디어 찾았군요. 😎 기본적으로 설정한 url 때문이었습니다.<br>
<br>
저처럼 파일명까지 제대로 지정해서 저장했는데 없는 페이지라고 뜨는 분은 `_config.yml`에서 **작성한 url과 실제 페이지의 url이 일치하는지 잘 확인**해 보시면 좋을 것 같습니다.<br>
(사실 저 부분은 제가 직접 작성한 건데 작년 9월 블로그를 개설하던 저는 왜 마지막에 /test를 입력했을까요? 아직도 의문..)

<br>

![잘 작동하는 Utterances](https://blog.kakaocdn.net/dn/bfnSfq/btq6q1r5Ixg/Rz2hY2HjL5kQkRjBkei4lk/img.png)

문제를 해결하니 잘 작동합니다. 해당 댓글은 댓글 관리용으로 만든 Repo에서도 확인이 가능했습니다.<br>
<br>

![Repo의 Issue 카테고리에서 확인 및 관리 가능한 댓글](https://blog.kakaocdn.net/dn/HKycu/btq6u2Y70SC/K46vGLervSdECC8B7HzQTK/img.png)

별거 아닌데도 해결하고 보니 뿌듯뿌듯.. 😏

<br>
<br>

### 4. 그 외의 팁 - Utterances 가로 사이즈 넓히기

그런데 적용된 Utterances를 보니 뭔가 2% 부족한 느낌이 들었습니다.

![첫 적용 이후](https://blog.kakaocdn.net/dn/ckTNeA/btq6skGbdFE/SD4fkKuMTTTFqwtUlf9LYK/img.png)

Utterances의 기본 최대 가로 사이즈가 760px이라 옆 여백이 참 많이 남아 허전해 보였던 겁니다. 😓<br>
'뭔가 포스팅 가로 부분을 꽉 채우고 싶은데..'라는 생각이 들었을 때 Utterances 페이지에서 본 문구가 떠올랐습니다.

<br>

![레이아웃 수정 방법 문구](https://blog.kakaocdn.net/dn/L7BxN/btq6w51UFy5/IHrmlW3KyCsQhkFl9eXvhK/img.png)

레이아웃을 수정하고 싶으면 CSS에서 `.utterances`나 `.utterances-frame` 선택자를 사용하여 수정하면 된다고 합니다.

<br>

![레이아웃 수정](https://blog.kakaocdn.net/dn/cielsd/btq6qibbOav/JGrU1TBqumO4TZuqOgpK30/img.png)

저는 가로 부분을 꽉 채우기 위해 최대 가로 사이즈를 100%로 주었습니다.

<br>

![가로 사이즈 수정 완료](https://blog.kakaocdn.net/dn/b62Hoj/btq6sd7XXp3/LbXD4dGtG7NTQQ1K2O96F0/img.png)

제가 원하는 방식대로 뜨는 게 보이시죠? 😎

<br>
<hr>
<br>

## 마치며

다른 사람들과의 교류가 있는 블로그가 아니라 댓글 기능이 있으면 좋겠다 싶다가도 쓸 일이 없을 것 같아 기능 추가를 망설였는데요.<br>
하지만 먼 미래에는 어떻게 될지 모르기도 하고, 타 플랫폼에서 썼던 글을 옮기면서 내용을 다시 보는데 '포스팅 내용에 대한 피드백은 언제나 환영입니다! 😎'라는 문구가 있더라고요.<br>
<br>
그냥 문구를 삭제할 수도 있지만 시도해 보기도 전에 포기하고 싶지 않기도 하고, 기능을 추가해 더 다채로운(ㅋㅋ) 블로그가 됐으면 해서 도전해 봤습니다.<br>
생각보다 정말정말 쉬우니 혹시 이 글을 보신 분들 중 시도해 보지 않은 분이 있다면 꼭 해 보세요!<br>
<br>
그럼 글 끝까지 읽어 주셔서 감사하고, 해당 포스팅에 대한 질문이 있다면 댓글 남겨 주세요. ✏

<br>
<br>

> 참고 문서 📝<br>
1. [HAHWUL 님 블로그](https://www.hahwul.com/2020/08/08/jekyll-utterances/)
2. [Utterances Repo Issue - 404 error occur when I click utterance comment button #443](https://github.com/utterance/utterances/issues/443#issuecomment-774536781)

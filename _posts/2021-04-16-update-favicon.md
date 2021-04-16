---
title:  "[Blog] Favicon 파비콘이 설정 안되었던 이유"
excerpt: "https://kairos03.github.io/jekyll/2017/09/11/learing-Up-Confusion-Around-baseurl.html"
toc: True
toc_sticky: True
toc_label: "Contents"
categories:
  - blog
tags:
  - favicon
  - html
  - jekyll
---

### 원인
> URL을 본인 환경에 맞게 바꾸어야 한다.
> url/baseurl/pagepath 의 이해

### AS-IS
```html
<link rel="apple-touch-icon" sizes="57x57" href="/assets/favicon/Snoopy-icon.png">
<link rel="icon" href="/assets/favicon/Snoopy-icon.png">
```

### TO-BE

```html
<link rel="apple-touch-icon" sizes="57x57" href="{{site.baseurl}}/assets/favicon/Snoopy-icon.png">
<link rel="icon" href="{{site.baseurl}}/assets/favicon/Snoopy-icon.png">
```


> **Shout out to**
[https://kairos03.github.io/jekyll/2017/09/11/learing-Up-Confusion-Around-baseurl.html

---
title:  "[Github.io] solved.ac sidebar 추가하기"
excerpt: Sidebar 꾸며보자
toc: False
toc_sticky: False
toc_label: "Contents"

sidebar:
  - title: "solved.ac"
    image: https://camo.githubusercontent.com/79fcbf056ec4786197f8a86132aeb99b66bde335982a6b7a41822dd3c122c912/687474703a2f2f6d617a617373756d6e6964612e7774662f6170692f6d696e692f67656e65726174655f62616467653f626f6a3d736e6f6f5f7079
    text: "![solved.ac snoo_py](https://camo.githubusercontent.com/f3f9383373ad9de51bd943325a32385a6790abaff724d37a55ede446710a80a0/687474703a2f2f6d617a617373756d6e6964612e7774662f6170692f76322f67656e65726174655f62616467653f626f6a3d736e6f6f5f7079)"

author_profile: true
categories:
  - blog
tags:
  - jekyll
---



[참고자료](https://mmistakes.github.io/minimal-mistakes/docs/layouts/)

### Create README.md on your repository

![](https://images.velog.io/images/snoo_py/post/fb125ec6-3728-4b7d-a216-d56d17ce6706/image.png)


```markdown
READ.md
ID: snoo_py

[![Solved.ac tier](http://mazassumnida.wtf/api/mini/generate_badge?boj=snoo_py)](https://solved.ac/profile/snoo_py)  
[![solved.ac tier](http://mazassumnida.wtf/api/generate_badge?boj=snoo_py)](https://solved.ac/profile/snoo_py)
```



### Copy URL on READ.md

![](https://images.velog.io/images/snoo_py/post/0d3cf9a2-d56a-477f-bbad-81271b1a2b02/image.png)



```yaml
sidebar:
  - title: "solved.ac"
    image: https://camo.githubusercontent.com/79fcbf056ec4786197f8a86132aeb99b66bde335982a6b7a41822dd3c122c912/687474703a2f2f6d617a617373756d6e6964612e7774662f6170692f6d696e692f67656e65726174655f62616467653f626f6a3d736e6f6f5f7079
    text: "![solved.ac snoo_py](https://camo.githubusercontent.com/f3f9383373ad9de51bd943325a32385a6790abaff724d37a55ede446710a80a0/687474703a2f2f6d617a617373756d6e6964612e7774662f6170692f76322f67656e65726174655f62616467653f626f6a3d736e6f6f5f7079)"

author_profile: true
```

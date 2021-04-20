---
title:  "[Giuhub.io] solved.ac 티어 추가하기"
excerpt: "https://mmistakes.github.io/minimal-mistakes/docs/layouts/"
toc: False
toc_sticky: False
toc_label: "Contents"
categories:
  - blog
tags:
  - jekyll
---

```yaml
#/_data/navigation.yml
# main links
main:
  - title: "Repositories"
    url: https://github.com/suzinee
  - title: "Monthly"
    url: /month-archive/
  - title: "Categories"
    url: /categories/
  - title: "Tags"
    url: /tags/
```

```markdown
---
title: "Posts by Tag"
permalink: /tags/
layout: tags
author_profile: true
---
/_pages/tag-archive.md
```

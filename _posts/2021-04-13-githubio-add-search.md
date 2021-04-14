---
title:  "[Github.io] Enabling search on github pages"
excerpt: "Github pages 검색 창을 만들어 보자"
toc: true
toc_sticky: true
toc_label: "Contents"
categories:
  - blog
tags:
  - tipue-search
---

> **Shout out to**
[https://theorydb.github.io/envops/2019/05/11/envops-blog-tipue-search/#tipue-search-환경설정](https://theorydb.github.io/envops/2019/05/11/envops-blog-tipue-search/#tipue-search-%ED%99%98%EA%B2%BD%EC%84%A4%EC%A0%95)

# My Development Environment

- Windows 10
- Jekyll
- Theme: Minimal mistakes

# Steps

you can see more details in [this website](https://theorydb.github.io/envops/2019/05/11/envops-blog-tipue-search/#tipue-search-%ED%99%98%EA%B2%BD%EC%84%A4%EC%A0%95) I shouted out.

1. Git clone [`https://github.com/jekylltools/jekyll-tipue-search`](https://github.com/jekylltools/jekyll-tipue-search)
2. Find `search.html` and copy `search.html` to your main directory where it inclues `_config.yml`
3. Then, copy `/tipuesearch` directory under your assets again.
4. Set your files

    /_config.yml
    ```
     tipue_search:
         include:
             pages: false
             collections: []
         exclude:
             files: [search.html, index.html, tags.html]
             categories: []
             tags: []
    ```

    /_includes/head.html
    ```
    <!-- tipuesearch--><link rel="stylesheet" href="/assets/tipuesearch/css/tipuesearch.css"><script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
    <script src="/assets/tipuesearch/tipuesearch_content.js"></script>
    <script src="/assets/tipuesearch/tipuesearch_set.js"></script>
    <script src="/assets/tipuesearch/tipuesearch.min.js"></script>
    ```

    /search.html
    ```
    ---
    title: Search
    description: "Search this site"
    layout:
    permalink: /search/
    tipue_search_active: true
    exclude_from_search: true
    ---

    <form action="{{ page.url | relative_url }}">
      <div class="tipue_search_left"><img src="{{ "/assets/tipuesearch/search.png" | relative_url }}" class="tipue_search_icon"></div>
      <div class="tipue_search_right"><input type="text" name="q" id="tipue_search_input" pattern=".{3,}" title="At least 3 characters" required></div>
      <div style="clear: both;"></div>
    </form>

    <div id="tipue_search_content"></div>

    <script>
    $(document).ready(function() {
      $('#tipue_search_input').tipuesearch({
        'wholeWords' : false,
        'showTime' : false,
        'minimumLength': 1
      });
    });
    </script>
    ```

    /_includes/sidebar.html
    ```
    {% if s.nav %}{% include nav_list nav=s.nav %}
          
            <form action="/search">
            <div class="tipue_search_left">
            <img src="/assets/tipuesearch/search.png" class="tipue_search_icon">
            </div>
            <div class="tipue_search_right">
            <input type="text" name="q" id="tipue_search_input" pattern=".{1,}" title="At least 1 characters" required></div>
            <div style="clear: both;"></div>
            </form>  
          
          {% endif %}
    ```

# Done
![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/71d29892-408c-4e03-af14-6a1720063dd5/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/71d29892-408c-4e03-af14-6a1720063dd5/Untitled.png)
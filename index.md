---
title : Index
layout : post
date_of_modification : "#date 2023-07-16 21:25 1689528308458334495 GMT"
---


N.B : this page is not meant to be seen.If you are there, well, you can look around, but expect for barebones and random changes :

- [Timeline](https://jeremyvlegros.github.io/website/timeline.html)
- [Links](https://jeremyvlegros.github.io/website/links)

posts :

{% capture post_list %}
{% include as_html_the_post_list_with_url_from_posts.liquid posts=site.posts %}
{% endcapture %}

{{ post_list }}



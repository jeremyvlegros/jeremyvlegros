---
date_of_creation         : "#date 2023-06-29 16:53 1688043201580071656 GMT"
---


# printing everything in posts

<ul>
{%- for post in posts -%}
  <li>
  {{ post.content }}
  </li>
  {% endfor%}
</ul>

---
date_of_creation         : "#date 2023-06-29 16:53 1688043201580071656 GMT"
---


# URL TESTING

<ul>
{%- for post in site.posts -%}
  <li>
  <a href="#{{ post.title }}"> {{ post.title | escape }} </a>
  </li>
  {% endfor%}
</ul>

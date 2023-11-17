---
title                : "About me : identity"
date_of_creation     : "#date 2023-05-19 00:00 1684454400000000000 GMT"
date_of_modification : "#date 2023-11-15 12:20 1700036405502184887 GMT"
permalink            : /post/1684454400000000000
tags                 : 
- "#posts"
- "#about"
- "#jeremyvlegros"
---


{%- comment -%} year {%- endcomment -%}
{%- include as_integer_the_year.liquid -%}
{%- assign year = return -%}
{%- assign return = null -%}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}


My name is Jeremy Legros, I am French, {{ year | minus : 1985 }} years old

{%- assign year = null -%}
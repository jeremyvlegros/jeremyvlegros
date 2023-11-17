---
title                : "About me : identity"
date_of_creation     : "#date 2023-05-19 00:00 1684454400000000003 GMT"
date_of_modification : "#date 2023-11-17 09:22 1700198548750968010 GMT"
permalink            : /post/1684454400000000003
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
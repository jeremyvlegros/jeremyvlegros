---
title                : "status > website"
date_of_creation     : "#date 2023-09-19 02:14 1695075266894964254 GMT"
date_of_modification : null
permalink            : "/posts/1695075266894964254"
tags :
- "#posts"
- "#status"
- "#website"
- "#python"
- "#jekyll"
---

## Automating tasks with `Python`

Currently, I am writing functions to :
- check `%- include -%` undefined and unused usages 
- check `from_...` parameters key names
- automate the build page `liquid` parts:
  - code snippets are not enough to deal with the code chunks
  - listing functions that have not been tested

## Writing a `array_post` structure in `Liquid`

As for include tags, I am emulating a structure from `Liquid` code using arrays and access functions, instead of using `site.posts` directly. 

Because `Jekyll` posts :
- are made with a structure that doesn't exist in `Liquid`
- fields and field access are obscure, I can't waste more time on this
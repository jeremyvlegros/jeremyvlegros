---
title                : sandbox
layout               : base
print_array          : print_array_content.html
---

## test `ARRAY_EMPTY`

```liquid
{% comment %}{% endcomment %}

{%- assign liquid_empty_array = "" | split :"" -%}
{%- if  site.ARRAY_EMPTY == liquid_empty_array -%}
    successful test for empty array
{%- endif -%}
{% comment %}{% endcomment %}
```

## `append` array to `""`

```liquid
{% comment %} {% endcomment %} 

{%- assign array = "1,2,3,4" | split :"," -%}

{%- assign expected = array -%}

{%- comment -%} result {%- endcomment -%}
{%- assign result = array | append : null -%}

{%- comment -%} procedure_assert_from_this_and_from_that {%- endcomment -%}
{% include procedure_assert_from_this_and_from_that.liquid from_this=expected from_that=result with_success="1" with_warning="1" with_name="array append '' " %}

{%- assign expected = null -%}
{%- assign result   = null -%}
{%- assign input    = null -%}

{% comment %} {% endcomment %}

```

## `append` array to `null`

```liquid
{% comment %} {% endcomment %} 

{%- assign array = "1,2,3,4" | split :"," -%}

{%- assign expected = array -%}

{%- comment -%} result {%- endcomment -%}
{%- assign result = array | append : null -%}

{%- comment -%} procedure_assert_from_this_and_from_that {%- endcomment -%}
{% include procedure_assert_from_this_and_from_that.liquid from_this=expected from_that=result with_success="1" with_warning="1" with_name="array append null " %}

{%- assign expected = null -%}
{%- assign result   = null -%}
{%- assign input    = null -%}

{% comment %} {% endcomment %}
```

## `append` `null` to array

```liquid
{% comment %} {% endcomment %} 

{%- assign array = "1,2,3,4" | split :"," -%}

{%- assign expected = array -%}

{%- comment -%} result {%- endcomment -%}
{%- assign result = null | append : array -%}

{%- comment -%} procedure_assert_from_this_and_from_that {%- endcomment -%}
{% include procedure_assert_from_this_and_from_that.liquid from_this=expected from_that=result with_success="1" with_warning="1" with_name="null append array" %}

{%- assign expected = null -%}
{%- assign result   = null -%}
{%- assign input    = null -%}

{% comment %} {% endcomment %}
```

## empty `capture` returning null

```liquid
{% comment %}{% endcomment %}
{%- capture null_variable -%}
{%- endcapture -%}

{%- assign input    = null_variable -%}
{%- assign expected = null -%}


{%- comment -%} procedure_assert_from_this_and_from_that {%- endcomment -%}
{% include procedure_assert_from_this_and_from_that.liquid from_this=expected from_that=result with_success="1" with_warning="" with_name="an empty capture is null"%}


{%- assign expected = null -%}
{%- assign result   = null -%}
{%- assign input    = null -%}
{%- assign null_variable = null -%}

{% comment %}{% endcomment %}
```

## `post` structure

```liquid
{% comment %}{% endcomment %}
{%- assign posts= site.posts -%}
{%- assign post= posts[-1] -%}

{{ post | jsonify }}

{% for post in posts %}
    
  post title : `{{post.title}}`
  
  creation date : `{{post.date}}`
   
  tags : `{{post.tags}}` 
   
{% endfor %}

{% comment %}{% endcomment %}
```

## `post` `date_of_creation` ?

post date of creation (mine) : `{{site.posts[0].date_of_creation}}`

```liquid
{% comment %}{% endcomment %}
{% raw %}
post date of creation (mine) : `{{site.posts[0].date_of_creation}}`
{% endraw %}
{% comment %}{% endcomment %}
```


## `includes` > testing as a function

expected :

```
1
2
3
4
5
```

result :

```liquid
{% comment %}{% endcomment %}
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{%- include print_array_content.html array = array_numbers  -%}
{% comment %}{% endcomment %}
```

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{%- include print_array_content.html array = array_numbers  -%}
{% endraw %}
{% comment %}{% endcomment %}
```

## `includes` > as a function called with a variable

expected :

```
1
2
3
4
5
```

result :

```liquid
{% comment %}{% endcomment %}
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{% assign print_array = page.print_array %}
{%- include {{print_array}} array=array_numbers  -%}
{% comment %}{% endcomment %}
```

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{% assign print_array = page.print_array %}
{%- include {{print_array}} array=array_numbers  -%}
{% endraw %}
{% comment %}{% endcomment %}
```


## `includes` > as a function with file extension `.liquid`

expected

```
1
2
3
4
5
```

result :

```liquid
{% comment %}{% endcomment %}
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{%- include print_array.liquid array=array_numbers  -%}
{% comment %}{% endcomment %}
```

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{%- include print_array.liquid array=array_numbers  -%}
{% endraw %}
{% comment %}{% endcomment %}
```


## `includes` > as a sum function not printing variable

expected :

```
5 
```

result :

```liquid
{% comment %}{% endcomment %}
{%- include function_persistent_sum_of_a_and_b.liquid a=3 b=2  -%}
{% comment %}{% endcomment %}
```

```liquid
{% comment %}{% endcomment %}
{% raw %}
{%- include function_persistent_sum_of_a_and_b.liquid a=3 b=2  -%}
{% endraw %}
{% comment %}{% endcomment %}
```


## `includes` > as a sum function printing variable

expected :

```
5 
```

result :

```liquid
{% comment %}{% endcomment %}
{%- include function_persistent_sum_of_a_and_b.liquid a=3 b=2  -%}
{{ result }}
{% comment %}{% endcomment %}
```

```liquid
{% comment %}{% endcomment %}
{% raw %}
{%- include function_persistent_sum_of_a_and_b.liquid a=3 b=2  -%}
{{ result }}
{% endraw %}
{% comment %}{% endcomment %}
```
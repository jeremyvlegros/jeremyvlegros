---
title                : sandbox
print_array          : procedure_print_array_content.html
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
{% include procedure_assert_from_this_and_from_that_with_success_with_warning_with_name.liquid from_this=expected from_that=result with_success="1" with_warning="1" with_name="array append '' " %}

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
{% include procedure_assert_from_this_and_from_that_with_success_with_warning_with_name.liquid from_this=expected from_that=result with_success="1" with_warning="1" with_name="array append null " %}

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
{% include procedure_assert_from_this_and_from_that_with_success_with_warning_with_name.liquid from_this=expected from_that=result with_success="1" with_warning="1" with_name="null append array" %}

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
{% include procedure_assert_from_this_and_from_that_with_success_with_warning_with_name.liquid from_this=expected from_that=result with_success="1" with_warning="" with_name="an empty capture is null"%}


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
    
  post title    : `{{post.title}}`
  
  creation date : `{{post.date}}`
   
  tags          : `{{post.tags}}` 
   
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
{%- include procedure_print_array_content.html array = array_numbers  -%}
{% comment %}{% endcomment %}
```

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{%- include procedure_print_array_content.html array = array_numbers  -%}
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
{%- include procedure_print_array.liquid array=array_numbers  -%}
{% comment %}{% endcomment %}
```

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{%- include procedure_print_array.liquid array=array_numbers  -%}
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

    
## `as_posts_from_tag.liquid`

STATUS

```liquid
{% comment %}{% endcomment %}
{%- comment -%} posts {%- endcomment -%}
{%- include as_posts_from_tag.liquid from_tag="#status" -%}
{%- assign posts = return -%}
{%- assign return = null -%}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

{% for post in posts %}
    {{ post.title }}
{% endfor %}
{% comment %}{% endcomment %}
```
ABOUT

```liquid
{% comment %}{% endcomment %}

{%- comment -%} posts {%- endcomment -%}
{%- include as_posts_from_tag.liquid from_tag="#about" -%}
{%- assign posts = return -%}
{%- assign return = null -%}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

{% for post in posts %}
    {{ post.title }}
{% endfor %}
{% comment %}{% endcomment %}
```

EMPTY TAG

```liquid
{% comment %}{% endcomment %}
{%- comment -%} posts {%- endcomment -%}
{%- include as_posts_from_tag.liquid from_tag="" -%}
{%- assign posts = return -%}
{%- assign return = null -%}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

{%- for post in posts -%}

    {{ post.title }}

{%- endfor -%}
{% comment %}{% endcomment %}
```

TAG NOT PRESENT

```liquid
{% comment %}{% endcomment %}
{%- comment -%} posts {%- endcomment -%}
{%- include as_posts_from_tag.liquid from_tag="fdhfhzeuihfzeuh" -%}
{%- assign posts = return -%}
{%- assign return = null -%}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

{%- for post in posts -%}

    {{ post.title }}

{%- endfor -%}

{% comment %}{% endcomment %}
```

## `as_html_the_post_index_list_from_posts.liquid`


```liquid
{% comment %}{% endcomment %}
{% include as_html_the_post_index_list_from_posts.liquid from_posts=site.posts %}
    {{ return }}
{% comment %}{% endcomment %}
```


## `as_html_the_post_list_with_url_from_posts.liquid`


```liquid
{% comment %}{% endcomment %}
{% include as_html_the_post_list_with_url_from_posts.liquid from_posts=site.posts %}
{{ return }}
{% comment %}{% endcomment %}
```

## `as_html_the_post_list_from_posts.liquid`


```liquid
{% comment %}{% endcomment %}
{% include as_html_the_post_list_from_posts.liquid from_posts=site.posts %}
{{ return }}
{% comment %}{% endcomment %}
```
## website tags

{% for tag in site.tags %}

  <a class="col button" style="text-decoration:none;background-color: rgba(0,0,0,45%)" href="/tag/{{tag[0]}}"> {{tag[0]}}</a>

{% endfor %}

## `as_array_the_website_tags.liquid`

```liquid
{% comment %}{% endcomment %}
{%- comment -%} tags {%- endcomment -%}
{%- include as_array_the_website_tags.liquid -%}
{%- assign tags = return -%}
{%- assign return = null -%}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

{{tags | jsonify}}

{% comment %}{% endcomment %}
```

## `as_string_word_with_inseparable_spaces_from_word.liquid`

```liquid
{% comment %} {% endcomment %} 

{%- assign input    = "aaa aaa" -%}
{%- assign expected = "aaa&nbsp;aaa" -%}

{%- comment -%} result {%- endcomment -%}
{% include as_string_word_with_inseparable_spaces_from_word.liquid from_word=input %}
{%- assign result = return -%}
{%- assign return = null -%}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

{%- comment -%} procedure_assert_from_this_and_from_that {%- endcomment -%}
{% include procedure_assert_from_this_and_from_that_with_success_with_warning_with_name.liquid from_this=expected from_that=result with_success=true with_warning=true with_name="" %}

{%- assign expected = null -%}
{%- assign result   = null -%}
{%- assign input    = null -%}

{% comment %} {% endcomment %}
```

```liquid
{% comment %} {% endcomment %} 

{%- assign input    = null -%}
{%- assign expected = "" -%}

{%- comment -%} result {%- endcomment -%}
{% include as_string_word_with_inseparable_spaces_from_word.liquid from_word=input %}
{%- assign result = return -%}
{%- assign return = null -%}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

{%- comment -%} procedure_assert_from_this_and_from_that {%- endcomment -%}
{% include procedure_assert_from_this_and_from_that_with_success_with_warning_with_name.liquid from_this=expected from_that=result with_success=true with_warning=true with_name="null" %}

{%- assign expected = null -%}
{%- assign result   = null -%}
{%- assign input    = null -%}

{% comment %} {% endcomment %}
```

```liquid
{% comment %} {% endcomment %} 

{%- assign input    = "" -%}
{%- assign expected = "" -%}

{%- comment -%} result {%- endcomment -%}
{% include as_string_word_with_inseparable_spaces_from_word.liquid from_word=input %}
{%- assign result = return -%}
{%- assign return = null -%}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

{%- comment -%} procedure_assert_from_this_and_from_that {%- endcomment -%}
{% include procedure_assert_from_this_and_from_that_with_success_with_warning_with_name.liquid from_this=expected from_that=result with_success=true with_warning=true with_name="empty string" %}

{%- assign expected = null -%}
{%- assign result   = null -%}
{%- assign input    = null -%}

{% comment %} {% endcomment %}
```

## `as_html_the_tag_from_word.liquid`

{% include as_html_the_tag_from_word.liquid from_word="aaaaaa" %}
{{return}}


{% include as_html_the_tag_from_word.liquid from_word="#aaaaaa" %}
{{return}}

## url relative with a space

"/tag/x corp"

{{"/tag/x corp" | relative_url}}


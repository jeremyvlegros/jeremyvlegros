---
title                : sandbox
layout               : post
print_array          : procedure_print_array_content.liquid
---

## test `ARRAY_EMPTY`

```liquid
{% comment %}{% endcomment %}

{%- assign liquid_empty_array = "" | split :"" -%}
{%- if  site.ARRAY_EMPTY == liquid_empty_array -%}
    [passed] empty array
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
{% include procedure_assert_from_this_and_from_that_with_success_with_warning_with_name_with_input.liquid from_this=expected from_that=result with_success="1" with_warning="1" with_name="array append '' " %}

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
{% include procedure_assert_from_this_and_from_that_with_success_with_warning_with_name_with_input.liquid from_this=expected from_that=result with_success="1" with_warning="1" with_name="array append null " %}

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
{% include procedure_assert_from_this_and_from_that_with_success_with_warning_with_name_with_input.liquid from_this=expected from_that=result with_success="1" with_warning="1" with_name="null append array" %}

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
{% include procedure_assert_from_this_and_from_that_with_success_with_warning_with_name_with_input.liquid from_this=expected from_that=result with_success="1" with_warning="" with_name="an empty capture is null"%}


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
{%- include procedure_print_array_content.liquid array = array_numbers  -%}
{% comment %}{% endcomment %}
```

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{%- include procedure_print_array_content.liquid array = array_numbers  -%}
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
{%- include test_function_persistent_sum_of_a_and_b.liquid a=3 b=2  -%}
{% comment %}{% endcomment %}
```

```liquid
{% comment %}{% endcomment %}
{% raw %}
{%- include test_function_persistent_sum_of_a_and_b.liquid a=3 b=2  -%}
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
{%- include test_function_persistent_sum_of_a_and_b.liquid a=3 b=2  -%}
{{ result }}
{% comment %}{% endcomment %}
```

```liquid
{% comment %}{% endcomment %}
{% raw %}
{%- include test_function_persistent_sum_of_a_and_b.liquid a=3 b=2  -%}
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

## `as_string_the_html_posts_for_the_index_from_posts.liquid`


```liquid
{% comment %}{% endcomment %}
{% include as_string_the_html_posts_for_the_index_from_posts.liquid from_posts=site.posts %}
    {{ return }}
{% comment %}{% endcomment %}
```


## `as_html_the_post_list_with_url_from_posts.liquid`


```liquid
{% comment %}{% endcomment %}
{% include as_string_the_html_post_links_from_posts.liquid from_posts=site.posts %}
{{ return }}
{% comment %}{% endcomment %}
```

## `as_string_the_html_post_contents_from_posts.liquid`


```liquid
{% comment %}{% endcomment %}
{% include as_string_the_html_post_contents_from_posts.liquid from_posts=site.posts %}
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

## `as_string_the_word_with_inseparable_spaces_from_word.liquid`

```liquid
{% comment %} {% endcomment %} 

{%- assign input    = "aaa aaa" -%}
{%- assign expected = "aaa&nbsp;aaa" -%}

{%- comment -%} result {%- endcomment -%}
{% include as_string_the_word_with_inseparable_spaces_from_word.liquid from_word=input %}
{%- assign result = return -%}
{%- assign return = null -%}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

{%- comment -%} procedure_assert_from_this_and_from_that {%- endcomment -%}
{% include procedure_assert_from_this_and_from_that_with_success_with_warning_with_name_with_input.liquid from_this=expected from_that=result with_success=true with_warning=true with_name="" %}

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
{% include as_string_the_word_with_inseparable_spaces_from_word.liquid from_word=input %}
{%- assign result = return -%}
{%- assign return = null -%}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

{%- comment -%} procedure_assert_from_this_and_from_that {%- endcomment -%}
{% include procedure_assert_from_this_and_from_that_with_success_with_warning_with_name_with_input.liquid from_this=expected from_that=result with_success=true with_warning=true with_name="null" %}

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
{% include as_string_the_word_with_inseparable_spaces_from_word.liquid from_word=input %}
{%- assign result = return -%}
{%- assign return = null -%}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

{%- comment -%} procedure_assert_from_this_and_from_that {%- endcomment -%}
{% include procedure_assert_from_this_and_from_that_with_success_with_warning_with_name_with_input.liquid from_this=expected from_that=result with_success=true with_warning=true with_name="empty string" %}

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

## testing building an array of posts (this time I'll keep the code as reminder)

```liquid
{% comment %}{% endcomment %}
{%- assign array = site.EMPTY_ARRAY -%}

{%- for post in site.posts -%}

    {%- assign array = array | push : post -%}
          
{% endfor %}

JSONIFIED {{ array | jsonify }}
{% comment %}{% endcomment %}
```

## testing flattening posts

```liquid
{% comment %}{% endcomment %}
{% comment %}{% endcomment %}
{%- assign array = site.EMPTY_ARRAY -%}

{{site.posts | compact | jsonify }}
{% comment %}{% endcomment %}
```

## testing flattening each post of posts into an array

```liquid
{% comment %}{% endcomment %}
{%- assign array = site.EMPTY_ARRAY -%}

{%- for post in site.posts -%}

    {%- assign inner_post = post -%}
    
    {%- assign inner_post = post | compact -%}

    {%- assign array = array | push : inner_post -%}
          
{% endfor %}

JSONIFIED {{ array | jsonify }}
{% comment %}{% endcomment %}
```

## testing post index list from tags

```liquid
{% comment %}{% endcomment %}
{%- assign tags = "#about #jekyll" | split :" " -%}

{%- comment -%} post html index list {%- endcomment -%}
{%- include as_array_the_html_posts_for_the_index_from_array_of_tags.liquid from_array_of_tags=tags -%}

{{ return }}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

{% comment %} {% endcomment %}

```

## testing `as_array_the_first_and_last_post_id_from_array_of_tags.liquid`

```liquid
{% comment %}{% endcomment %}

{%- assign tags = "#about #jekyll" | split :" " -%}
{%- include as_array_the_first_and_last_post_id_from_array_of_tags.liquid from_array_of_tags= tags-%}
{%- assign array = return -%}
{%- assign return = null -%}
{{ array | jsonify }}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

{% comment %}{% endcomment %}
```

## testing array `| first` on string 

```liquid
{% comment %}{% endcomment %}
printing first element of string {{ "first_element middle element last_element" | first }}

=> array first don't crash if used on string
{% comment %}{% endcomment %}
```

## testing flattening `|compact` a string like an array

```liquid
{% comment %}{% endcomment %}
flattening the string {{ "first_element middle element last_element" | compact }}

=> array flattening don't crash if used on string
{% comment %}{% endcomment %}
```

## testing flattening `|compact` an array of tags

```liquid
{% comment %}{% endcomment %}
{% assign array = site.ARRAY_EMPTY | push : "#about" | push : "#me" %}

array : {{ array | jsonify }} 

flattening the array {{ array | compact | jsonify }}

the array not jsonified : {{ array | compact }}

=> works as expected, I will have to split on the hashtag, and maybe re-add it
{% comment %}{% endcomment %}
```

## testing  `as_array_clean_from_array_of_tags`

```liquid
{% comment %}{% endcomment %}
{% assign array = site.ARRAY_EMPTY | push : "#about" | push : "#me" %}

{%- comment -%} cleaned_array {%- endcomment -%}
{%- include as_array_the_tags_from_array_of_compacted_tags.liquid from_array_of_compacted_tags=array-%}
{%- assign cleaned_array = return -%}
{%- assign return = null -%}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

{{cleaned_array}}
{% comment %}{% endcomment %}
```

## testing  `as_array_clean_from_array_of_tags` with string converted to array

```liquid
{% comment %}{% endcomment %}
{% assign array = site.ARRAY_EMPTY | push : "#about" | push : "#me" %}
{%- assign tags = array | compact -%}
{%- assign tags = tags | split :"#" -%}

{%- comment -%} cleaned_array {%- endcomment -%}
{%- include as_array_the_tags_from_array_of_compacted_tags.liquid from_array_of_compacted_tags=tags-%}
{%- assign cleaned_array = return -%}
{%- assign return = null -%}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

{{cleaned_array}}
{% comment %}{% endcomment %}
```

## testing pop array

```liquid
{% comment %}{% endcomment %}
{% assign array = site.ARRAY_EMPTY | push : "1" | push : "2" | push : "3" | push : "4" | push : "5" %}

array {{ array | jsonify }}

array pop 1 {{ array[0] | pop | jsonify }}
{% comment %}{% endcomment %}
```

## testing array offset going over the limit

 ```liquid
 {% comment %}{% endcomment %}
 {% assign array = site.ARRAY_EMPTY | push : "1" | push : "2" | push : "3" %}
 
 {%- for value in array offset:20 -%}
   <br>  value : {{ value }}  <br>  
 {%- endfor -%}
 
 => it didn't crash, I can use it without mercy
 {% comment %}{% endcomment %}
 ```

## testing `as_array_without_duplicates_from_array.liquid`


```liquid
{% comment %}{% endcomment %}
{% assign array = site.ARRAY_EMPTY | push : "1" | push : "2" | push : "3" | push : "3" | push : "5" %}

array before : {{array | jsonify}}

{%- comment -%} array {%- endcomment -%}
{%- include as_array_posts_without_duplicates_from_array.liquid from_array=array -%}
{%- assign array = return -%}
{%- assign return = null -%}
{%- comment -%} `Liquid` does not have functions {%- endcomment -%}

array after : {{array | jsonify}}
{% comment %}{% endcomment %}
```

## displaying `site.post[0].content`


```liquid
{% comment %}{% endcomment %}
{%- assign post = site.posts[0].content -%}
{{ post }}
<!---->
{% comment %}{% endcomment %}
```

## displaying `site.post[0].output`

```liquid
{% comment %}{% endcomment %}
{%- assign post = site.posts[0].output -%}
{{ post }}
<!---->
{% comment %}{% endcomment %}
```

## Empty array boolean value

```liquid
{% comment %}{% endcomment %}

{%- if site.ARRAY_EMPTY -%}
    Empty array is boolean True
{%- else -%}
    Empty array is boolean False
{%- endif -%}

{% comment %}{% endcomment %}
```

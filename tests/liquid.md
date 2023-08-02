---
title  : "Learning `Jekyll` and `Liquid`"                                         
layout : post
test_list :
- "a"
- "b"
- "c"

date_of_creation     : "#date 2023-06-20 00:00 0000000000000000000 GMT"
date_of_modification : "#date 2023-07-16 22:23 1689531810469969567 GMT"
---

## Assigning a variable `test_list`

{% assign test_list = page.test_list %}

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% assign test_list = page.test_list %}
{% endraw %}
{% comment %}{% endcomment %}
```

## Printing a `HTML` character

{% assign character = ">" %}
{% assign character = character | replace : ">","&gt;" %}

html character greater than "{{character}}"

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% assign character  = ">" %}
{% assign character  = character | replace : ">","&gt;" %}
                                                 
html character greater than "{{character}}"
{% endraw %}
{% comment %}{% endcomment %}
```

## Prefixing an HTML character by `NBSP`

{% assign title = page.title %}
{% if title %}
{% assign title = title | escape | replace : " &gt;","&nbsp;&gt;" %}
{% endif %}

this should not break : {{title}}

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% assign title = page.title %}
{% if title %}
{% assign title = title | escape | replace : " &gt;","&nbsp;&gt;" %}
{% endif %}

this should not break : {{title}}
{% endraw %}
{% comment %}{% endcomment %}
```

## Accessing the local variable `test_list`

The loop :

{% for value in test_list %}
value : {{ value }}
{% endfor %}

printing `test_list` : `{{ test_list }}`

printing `test_list`  as json :  `{{ test_list | jsonify}}`

```liquid
{% comment %}{% endcomment %}
{% raw %}
The loop :

{% for value in test_list %}
value : {{ value }}
{% endfor %}

printing `test_list` : `{{ test_list }}`

printing `test_list`  as json :  `{{ test_list | jsonify}}`
{% endraw %}
{% comment %}{% endcomment %}
```

## The To string function `inspect`

{% assign test_list = page.test_list %}
The `test_list` as a string : `{{ test_list | inspect }}`

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% assign test_list = page.test_list %}
The `test_list` as a string : `{{ test_list | inspect }}`
{% endraw %}
{% comment %}{% endcomment %}
```

## Displaying list elements

```liquid
{% comment %}{% endcomment %}
{% for value in test_list %}
{{ value }}
{% endfor %}
{% comment %}{% endcomment %}
```


```liquid
{% comment %}{% endcomment %}
{% raw %}
{% comment %}{% endcomment %}
{% for value in test_list %}
{{ value }}
{% endfor %}
{% comment %}{% endcomment %}
{% endraw %}
{% comment %}{% endcomment %}
```


## `unless`

Unless 1 > 4 print 1 is smaller than 4

```liquid
{% comment %}{% endcomment %}
{% unless 1 > 4 %}
1 is smaller than 4
{% endunless %}
{% comment %}{% endcomment %}
```

```liquid
{% comment %}{% endcomment %}
{% raw %}

{% unless 1 > 4 %}
1 is smaller than 4
{% endunless %}

{% endraw %}
{% comment %}{% endcomment %}
```

## String `contains`

{% if "abc" contains "a" %}
abc contains a
{% endif %}

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% if "abc" contains "a" %}
abc contains a
{% endif %}
{% endraw %}
{% comment %}{% endcomment %}
```

## Accessing `Jekyll` variables >`site.name`

`{{site.name}}`

## Accessing `Jekyll` variables >`page.url`

`{{page.url}}`

## Accessing `Jekyll` variables >`site.url`

`{{site.url}}`

## Accessing `Jekyll` variables > `post.id` and `post.url`

<ul>

{% for post in site.posts %}

<li>
POST ID : `{{post.id}}`
</li>

<li>
POST URL : `{{post.url}}`
</li>

{% break %}

{% endfor %}

</ul>

```liquid
{% comment %}{% endcomment %}
{% raw %}
<ul>

{% for post in site.posts %}

<li>
POST ID : `{{post.id}}`
</li>

<li>
POST URL : `{{post.url}}`
</li>

{% break %}

{% endfor %}

</ul>
{% endraw %}
{% comment %}{% endcomment %}
```

## Constructed canonical page `URL` 

(need to set name in `_config.yml`)

`{{ site.url | append :"/" | append : site.name | append : page.url }}`

```liquid
{% comment %}{% endcomment %}
{% raw %}
`{{ site.url | append :"/" | append : site.name | append : page.url }}`
{% endraw %}
{% comment %}{% endcomment %}
```

## `slugify`


"Dummy > something > something" :

- value                         : {{ "Dummy > something > something" | slugify }}
- expecting something like this : `dummy--something--something`

## `case` > split cases / non traversal

expected : "letter a"

{% assign letter = "a" %}

{% case letter %}
{% when "a" %}
`letter a`
{% when "b" %}
`letter b`
{% when "c" %}
`letter c`
{% else %}
`not a nor b nor c`
{% endcase %}

expected : "letter b"

{% assign letter = "b" %}

{% case letter %}
{% when "a" %}
`letter a`
{% when "b" %}
`letter b`
{% when "c" %}
`letter c`
{% else %}
`not a nor b nor c`
{% endcase %}

expected : "not a nor b nor c"

{% assign letter = "d" %}

{% case letter %}
{% when "a" %}
`letter a`
{% when "b" %}
`letter b`
{% when "c" %}
`letter c`
{% else %}
`not a nor b nor c`
{% endcase %}

```liquid
{% comment %}{% endcomment %}
{% raw %}
expected : "letter a"

{% assign letter = "a" %}

{% case letter %}
  {% when "a" %}
  `letter a`
  {% when "b" %}
  `letter b`
  {% when "c" %}
  `letter c`
  {% else %}
  `not a nor b nor c`
{% endcase %}

expected : "letter b"

{% assign letter = "b" %}

{% case letter %}
  {% when "a" %}
  `letter a`
  {% when "b" %}
   `letter b`
  {% when "c" %}
  `letter c`
  {% else %}
  `not a nor b nor c`
{% endcase %}


expected : "not a nor b nor c" 

{% assign letter = "d" %}

{% case letter %}
  {% when "a" %}
    `letter a`
  {% when "b" %}
    `letter b`
  {% when "c" %}
    `letter c`
  {% else %}
    `not a nor b nor c`
{% endcase %}
{% endraw %}
{% comment %}{% endcomment %}
```

## `case` >  multiple cases / traversal / like in `C`

expected : "a letter among a,b,c,d"

{% assign letter = "a" %}
{% case letter %}
{% when "a", "b", "c", "d" %}
`a letter among a,b,c,d`
{% else %}
`not a letter among a,b,c,d`
{% endcase %}

expected : "a letter among a,b,c,d"

{% assign letter = "d" %}
{% case letter %}
{% when "a", "b", "c", "d" %}
`a letter among a,b,c,d`
{% else %}
`not a letter among a,b,c,d`
{% endcase %}

expected : "not a letter among a,b,c,d"

{% assign letter = "e" %}
{% case letter %}
{% when "a", "b", "c", "d" %}
`a letter among a,b,c,d`
{% else %}
`not a letter among a,b,c,d`
{% endcase %}

```liquid
{% comment %}{% endcomment %}
{% raw %}
expected : "a letter among a,b,c,d"

{% assign letter = "a" %}
{% case letter %}
{% when "a", "b", "c", "d" %}
`a letter among a,b,c,d`
{% else %}
`not a letter among a,b,c,d`
{% endcase %}

expected : "a letter among a,b,c,d"

{% assign letter = "d" %}
{% case letter %}
{% when "a", "b", "c", "d" %}
`a letter among a,b,c,d`
{% else %}
`not a letter among a,b,c,d`
{% endcase %}

expected : "not a letter among a,b,c,d"

{% assign letter = "e" %}
{% case letter %}
{% when "a", "b", "c", "d" %}
`a letter among a,b,c,d`
{% else %}
`not a letter among a,b,c,d`
{% endcase %}
{% endraw %}
{% comment %}{% endcomment %}
```


## Global variable > `YAML` > `_config` >  `for` > `dictionary`

Results for `link`

```liquid
{% comment %}{% endcomment %}
{% for link in site.social_links %}
  link      : {{ link }}

  link name : {{ link.name }}

  link url  : {{ link.url }}
{% endfor %}
{% comment %}{% endcomment %}
```

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% comment %}{% endcomment %}
{% for link in site.social_links %}
link : {{ link }}

link name : {{ link.name }}

link url : {{ link.url }}
{% endfor %}
{% comment %}{% endcomment %}
{% endraw %}
{% comment %}{% endcomment %}
```


## Global variable `_config.yml` > external image with `HTML`

<!--suppress HtmlUnknownTarget -->
<img src="{{site.image_color_1}}" alt="image_color_1">

## Global variable `_config.yml` > external image in a `Markdown` link

![image_color_1]({{site.image_color_1}})

## `Jekyll` > `includes` > testing  example


`Liquid` file

```liquid
{% comment %}{% endcomment %}
{% raw %}
<figure>
    <a href=" {{include.url}} ">
        <img src=" {{include.file}} " style="max-width:  include.max-width ;"
             alt=" {{include.alt}} "/>
    </a>
    <figcaption> {include.caption}</figcaption>
</figure>
{% endraw %}
{% comment %}{% endcomment %}
```


`HTML` file

```liquid
{% comment %}{% endcomment %}
{% raw %}
{%- include testing_jekyll_example.html url="https://jekyllrb.co -m" max-width="200px" file="logo.png" alt="Jekyll logo" caption="This is the Jekyll logo." -%}
{% endraw %}
{% comment %}{% endcomment %}
```

## `capture` > testing text

{% capture captured_text %}

this is the text to capture

{%- endcapture -%}

expected :

```
this is the text to capture
```

result :

```liquid
{% comment %}{% endcomment %}
{{ captured_text }}
{% comment %}{% endcomment %}
```

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% capture captured_text %}
  this is the text to capture
{%- endcapture -%}

{{ captured_text }}
{% endraw %}
{% comment %}{% endcomment %}
```

## `capture` >`Shopify` > example

expected :

```
I am 35 and my favourite food is pizza.
```
                                       
result :

```liquid
{% comment %}{% endcomment %}
{% assign favorite_food = "pizza" %}
{% assign age = 35 %}

{% capture about_me %}
I am {{ age }} and my favorite food is {{ favorite_food }}.
{%- endcapture -%}

{{ about_me }}
{% comment %}{% endcomment %}
```

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% assign favorite_food = "pizza" %}
{% assign age = 35 %}

{% capture about_me %}
I am {{ age }} and my favorite food is {{ favorite_food }}.
{%- endcapture -%}

{{ about_me }}
{% endraw %}
{% comment %}{% endcomment %}
```

## `capture` > testing content

{% capture captured_text %}
this is the text to capture
{%- endcapture -%}

expected : `this,is,the,text,to,capture`
result   : `{{ captured_text|replace : " ", "," }}`

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% capture captured_text %}
this is the text to capture
{%- endcapture -%}

expected : `this,is,the,text,to,capture`
result   : `{{ captured_text|replace : " ", "," }}`
{% endraw %}
{% comment %}{% endcomment %}
```



#date 2023-07-06 11:48

## `capture` > `include`

```liquid
{% comment %}{% endcomment %}
{%- capture captured_text -%}
  {%- include function_persistent_sum_of_a_and_b.liquid a=3 b=2  -%}
{%- endcapture -%}
{% comment %}{% endcomment %}
```

expected :`5`
result : `{{ captured_text }}`


```liquid
{% comment %}{% endcomment %}
{% raw %}
{% comment %}{% endcomment %}
{%- capture captured_text -%}
  {%- include function_persistent_sum_of_a_and_b.liquid a=3 b=2  -%}
{%- endcapture -%}
{% comment %}{% endcomment %}

expected :`5`
result : `{{ captured_text }}`

{% endraw %}
{% comment %}{% endcomment %}
```


## `capture` > `include` > internal variable persistency

Resetting the `result` variable

{% assign result = null %}

value of result before call include : `{{ result }}`

{% capture captured_text %}
  {%- include function_persistent_sum_of_a_and_b.liquid a=3 b=2  -%}
{%- endcapture -%}

value of result after call include : `{{ result }}`

```liquid
{% comment %}{% endcomment %}
{% raw %}
Resetting the `result` variable

{% assign result = null %}

value of result before call include : `{{ result }}`

{% capture captured_text %}
  {%- include function_persistent_sum_of_a_and_b.liquid a=3 b=2  -%}
{% endcapture %}

value of result after call include : `{{ result }}`
{% endraw %}
{% comment %}{% endcomment %}
```


## `capture` >`include` > function non-persistent

Resetting the `result` variable

{% assign result = null %}

value of result before call include : `{{ result }}`

{% capture sum %}
  {%- include function_sum_of_a_and_b.liquid a=3 b=2 -%}
{% endcapture %}

value of result after call include : `{{ result }}`
 
value of the function : `{{ sum }}`

```liquid
{% comment %}{% endcomment %}
{% raw %}
{% comment %}{% endcomment %}
Resetting the `result` variable

{% assign result = null %}

value of result before call include : `{{ result }}`

{% capture sum %}
  {%- include function_sum_of_a_and_b.liquid a=3 b=2 -%}
{% endcapture %}

value of result after call include : `{{ result }}`
 
value of the function : `{{ sum }}`

{% endraw %}
{% comment %}{% endcomment %}
```

## Liquid empty array

```liquid
{% comment %}{% endcomment %}

{{ "" | split :"" | jsonify }}

{% comment %}{% endcomment %}
```

## testing `concat`

```liquid
{% comment %}{% endcomment %}
{%- assign array = "#status #about #liquid" | split : " " -%}

{%- assign array = array | concat : site.ARRAY_EXAMPLE_INTEGER -%}

{{ array | jsonify }}

{% comment %}{% endcomment %}


```
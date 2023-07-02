---
title : "Title > Testing > variables"
layout : post
test_list :
  - "a"
  - "b"
  - "c"
---
## assigning a variable `test_list`

{% assign test_list = page.test_list%}

```
{%raw%}
{% assign test_list = page.test_list%}
{% endraw %}
```

## printing a html character

{% assign character  = ">" %}
{% assign character  = character | replace : ">","&gt;" %}
                                                 
html character greater than "{{character}}"

```
{%raw%}
{% assign character  = ">" %}
{% assign character  = character | replace : ">","&gt;" %}
                                                 
html character greater than "{{character}}"
{% endraw %}
```



## prefixing a html character by NBSP


{% assign title = page.title %}
{% if title %}
{% assign title = title | escape | replace : " &gt;","&nbsp;&gt;" %}
{% endif %}

this should not break : {{title}}

```
{%raw%}
{% assign title = page.title %}
{% if title %}
{% assign title = title | escape | replace : " &gt;","&nbsp;&gt;" %}
{% endif %}

this should not break : {{title}}
{% endraw %}
```

## Accessing the local variable `test_list`
         
The loop :

{% for value in test_list %}
value : {{ value }}
{% endfor %}

printing `test_list` : `{{ test_list }}`

printing `test_list`  as json :  `{{ test_list | jsonify}}`

```
{%raw%}
The loop :

{% for value in test_list %}
value : {{ value }}
{% endfor %}

printing `test_list` : `{{ test_list }}`

printing `test_list`  as json :  `{{ test_list | jsonify}}`
{% endraw %}
```
## the To string function `inspect`


{% assign test_list = page.test_list%}
The `test_list` as a string : `{{ test_list | inspect }}`

```
{%raw%}
{% assign test_list = page.test_list%}
The `test_list` as a string : `{{ test_list | inspect }}`
{% endraw %}
```

## Displaying Liquid results in code ?

```
{% for value in test_list %}
{{ value }}
{% endfor %}
```

## `unless`

Unless 1 > 4 print 1 is smaller than 4

```
{% unless 1 > 4 %}
1 is smaller than 4
{% endunless %}
```

```
{%raw%}

{% unless 1 > 4 %}
1 is smaller than 4
{% endunless %}

{% endraw %}
```
## String contains

{% if "abc" contains "a" %}
abc contains a
{% endif %}

```
{%raw%}
{% if "abc" contains "a" %}
abc contains a
{% endif %}
{% endraw %}
```

## Accessing Jekyll variables

### `site.name`

`{{site.name}}`

### `page.url`

`{{page.url}}`

### `site.url`

`{{site.url}}`


## `post.id` and `post.url`

<ul>

{%- for post in site.posts -%}

<li>
POST ID : `{{post.id}}`
</li>

<li>
POST URL : `{{post.url}}`
</li>

{% break %}

{%- endfor -%}

</ul>

```
{%- raw -%}
<ul>

{%- for post in site.posts -%}

<li>
POST ID : `{{post.id}}`
</li>

<li>
POST URL : `{{post.url}}`
</li>

{% break %}

{%- endfor -%}

</ul>
{%- endraw -%}
```

### constructed canonical page url (need to set name in `_config.yml`)

`{{ site.url | append :"/" | append : site.name | append : page.url }}`

## `case` instruction

### split cases / non traversal

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

```
{%raw%}
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
```

### multiple cases / traversal / like in C
                         
expected : "a letter among a,b,c,d"

{% assign letter = "a" %}
{% case letter %}
  {% when "a", "b", "c", "d" %}
    a letter among a,b,c,d
  {% else %}
    not a letter among a,b,c,d
{% endcase %}

expected : "a letter among a,b,c,d"

{% assign letter = "d" %}
{% case letter %}
  {% when "a", "b", "c", "d" %}
    a letter among a,b,c,d 
  {% else %}
    not a letter among a,b,c,d
{% endcase %}

expected : "not a letter among a,b,c,d"

{% assign letter = "e" %}
{% case letter %}
  {% when "a", "b", "c", "d" %}
    a letter among a,b,c,d 
  {% else %}
    not a letter among a,b,c,d
{% endcase %}


```
{%raw%}
expected : "a letter among a,b,c,d"

{% assign letter = "a" %}
{% case letter %}
  {% when "a", "b", "c", "d" %}
    a letter among a,b,c,d
  {% else %}
    not a letter among a,b,c,d
{% endcase %}

expected : "a letter among a,b,c,d"

{% assign letter = "d" %}
{% case letter %}
  {% when "a", "b", "c", "d" %}
    a letter among a,b,c,d 
  {% else %}
    not a letter among a,b,c,d
{% endcase %}

expected : "not a letter among a,b,c,d"

{% assign letter = "e" %}
{% case letter %}
  {% when "a", "b", "c", "d" %}
    a letter among a,b,c,d 
  {% else %}
    not a letter among a,b,c,d
{% endcase %}
{% endraw %}
```

## Accessing global variables `_config.yml`

### global variable social_links

```
{% for link in site.social_links %}
{{ link }}
{% endfor %}
```

## Displaying an external image with HTML

<img src="{{site.image_color_1}}" alt="image_color_1">

## Displaying an external image in a Markdown link

![image_color_1]({{site.image_color_1}})

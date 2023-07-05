---
title : "Title > Testing > variables"
layout : post
test_list :
  - "a"
  - "b"
  - "c"
print_array : print_array_content.html
---




## &#35;&#35; assigning a variable `test_list`

{% assign test_list = page.test_list%}

```
{%raw%}
{% assign test_list = page.test_list%}
{% endraw %}
```

## &#35;&#35; printing a html character

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



## &#35;&#35; prefixing a html character by NBSP


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

## &#35;&#35; Accessing the local variable `test_list`
         
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
## &#35;&#35; the To string function `inspect`


{% assign test_list = page.test_list%}
The `test_list` as a string : `{{ test_list | inspect }}`

```
{%raw%}
{% assign test_list = page.test_list%}
The `test_list` as a string : `{{ test_list | inspect }}`
{% endraw %}
```

## &#35;&#35; Displaying Liquid results in code ?

```
{% for value in test_list %}
{{ value }}
{% endfor %}
```

## &#35;&#35; `unless`

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
## &#35;&#35; String contains

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

## &#35;&#35; Accessing Jekyll variables

### &#35;&#35; &#35;`site.name`

`{{site.name}}`

### &#35;&#35; &#35;`page.url`

`{{page.url}}`

### &#35;&#35; &#35;`site.url`

`{{site.url}}`


### &#35;&#35; &#35;`post.id` and `post.url`

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

### &#35;&#35; &#35;constructed canonical page url (need to set name in `_config.yml`)

`{{ site.url | append :"/" | append : site.name | append : page.url }}`

## &#35;&#35; Jekyll filter `slugify`

I suspect this thing to only work in HTML but I won't rely on it ...

"Dummy > something > something" : 

- value                         : {{ "Dummy > something > something" | slugify }}
- expecting something like this : `dummy--something--something`

## &#35;&#35; `case` instruction

### &#35;&#35; &#35;split cases / non traversal

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

### &#35;&#35; &#35;multiple cases / traversal / like in C
                         
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

## &#35;&#35; Accessing global variables `_config.yml`

### &#35;&#35; &#35;global variable social_links

```
{% for link in site.social_links %}
{{ link }}
{% endfor %}
```

## &#35;&#35; Displaying an external image with HTML

<img src="{{site.image_color_1}}" alt="image_color_1">

## &#35;&#35; Displaying an external image in a Markdown link

![image_color_1]({{site.image_color_1}})

## &#35;&#35; testing Jekyll `includes` example

In the include file (everywhere with `include` should be surrounded by brackets)

```html
<figure>
   <a href=" include.url ">
   <img src=" include.file " style="max-width:  include.max-width ;"
      alt=" include.alt "/>
   </a>
   <figcaption> include.caption </figcaption>
</figure>
```

```html

% include testing_jekyll_example.html url="http://jekyllrb.com"
max-width="200px" file="logo.png" alt="Jekyll logo"
caption="This is the Jekyll logo." %

```         

## &#35;&#35; testing Jekyll `includes` example without curly braces

print this "this is the sentence printed with include"

{% include testing_variables.html string="this is the sentence printed with include" %}

## &#35;&#35; testing Jekyll `includes` as a function

expected :

```
1
2
3
4
5
```
result :

```
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{%- include print_array_content.html array = array_numbers -%}
```


## &#35;&#35; testing Jekyll `includes` as a function called with a variable
expected :

```
1
2
3
4
5
```

result :
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{%- assign print_array = page.print_array -%}
{%- include {{print_array}} array=array_numbers -%}

## &#35;&#35; testing Jekyll `includes` as a function with file extension `.liquid`

expected
```
1
2
3
4
5
```

result :

```
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{% include print_array.liquid array=array_numbers %}
```

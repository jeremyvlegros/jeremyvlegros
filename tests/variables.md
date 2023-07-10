---
title : "Learning `Jekyll` and `Liquid`"
layout : post
test_list :
- "a"
- "b"
- "c"

print_array : print_array_content.html

---

## &#35;&#35; assigning a variable `test_list`

{% assign test_list = page.test_list %}

```liquid
{% raw %}
{% assign test_list = page.test_list %}
{% endraw %}
```





## &#35;&#35; printing a `HTML` character

{% assign character = ">" %}
{% assign character = character | replace : ">","&gt;" %}

html character greater than "{{character}}"

```liquid
{% raw %}
{% assign character  = ">" %}
{% assign character  = character | replace : ">","&gt;" %}
                                                 
html character greater than "{{character}}"
{% endraw %}
```

## &#35;&#35; prefixing a HTML character by `NBSP`

{% assign title = page.title %}
{% if title %}
{% assign title = title | escape | replace : " &gt;","&nbsp;&gt;" %}
{% endif %}

this should not break : {{title}}

```liquid
{% raw %}
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

```liquid
{% raw %}
The loop :

{% for value in test_list %}
value : {{ value }}
{% endfor %}

printing `test_list` : `{{ test_list }}`

printing `test_list`  as json :  `{{ test_list | jsonify}}`
{% endraw %}
```

## &#35;&#35; the To string function `inspect`

{% assign test_list = page.test_list %}
The `test_list` as a string : `{{ test_list | inspect }}`

```liquid
{% raw %}
{% assign test_list = page.test_list %}
The `test_list` as a string : `{{ test_list | inspect }}`
{% endraw %}
```

## &#35;&#35; Displaying `Liquid` results in code ?

```liquid
{% for value in test_list %}
{{ value }}
{% endfor %}
```

## &#35;&#35; `unless`

Unless 1 > 4 print 1 is smaller than 4

```liquid
{% unless 1 > 4 %}
1 is smaller than 4
{% endunless %}
```

```liquid
{% raw %}

{% unless 1 > 4 %}
1 is smaller than 4
{% endunless %}

{% endraw %}
```

## &#35;&#35; String `contains`

{% if "abc" contains "a" %}
abc contains a
{% endif %}

```liquid
{% raw %}
{% if "abc" contains "a" %}
abc contains a
{% endif %}
{% endraw %}
```

## &#35;&#35; Accessing `Jekyll` variables >`site.name`

`{{site.name}}`

## &#35;&#35; Accessing `Jekyll` variables >`page.url`

`{{page.url}}`

## &#35;&#35; Accessing `Jekyll` variables >`site.url`

`{{site.url}}`

## &#35;&#35; Accessing `Jekyll` variables > `post.id` and `post.url`

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

```
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
```

## &#35;&#35; constructed canonical page `URL` 

(need to set name in `_config.yml`)

`{{ site.url | append :"/" | append : site.name | append : page.url }}`

```liquid
{% raw %}
`{{ site.url | append :"/" | append : site.name | append : page.url }}`
{% endraw %}
```

## &#35;&#35; ## &#35;&#35;  filter `slugify`

I suspect this thing to only work in HTML, but I won't rely on it ...

"Dummy > something > something" :

- value                         : {{ "Dummy > something > something" | slugify }}
- expecting something like this : `dummy--something--something`

## &#35;&#35; `case` instruction

### &#35;&#35;&#35; split cases / non traversal

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
```

### &#35;&#35;&#35; multiple cases / traversal / like in `C`

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

```liquid
{% raw %}
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

### &#35;&#35;&#35; global variable social_links

```liquid
{% for link in site.social_links %}
{{ link }}
{% endfor %}
```

## &#35;&#35; Displaying an external image with `HTML`

<!--suppress HtmlUnknownTarget -->
<img src="{{site.image_color_1}}" alt="image_color_1">

## &#35;&#35; Displaying an external image in a `Markdown` link

![image_color_1]({{site.image_color_1}})

## &#35;&#35; `Jekyll` > `includes` > testing  example

In the include file (everywhere `{include ...}` should be surrounded by another bracket, escaping double brackets is a headheck)

`Liquid` file

```liquid
{% raw %}
<figure>
    <a href=" {{include.url}} ">
        <img src=" {{include.file}} " style="max-width:  include.max-width ;"
             alt=" {{include.alt}} "/>
    </a>
    <figcaption> {include.caption}</figcaption>
</figure>
{% endraw %}
```


`HTML` file

```liquid
{% raw %}
{% include testing_jekyll_example.html url="http://jekyllrb.com"
max-width="200px" file="logo.png" alt="Jekyll logo"
caption="This is the Jekyll logo." %}
{% endraw %}
```


## &#35;&#35; `includes` > testing as a function

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
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{% include print_array_content.html array = array_numbers %}
```

```liquid
{% raw %}
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{% include print_array_content.html array = array_numbers %}
{% endraw %}
```

## &#35;&#35; `includes` > as a function called with a variable

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
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{% assign print_array = page.print_array %}
{% include {{print_array}} array=array_numbers %}
```

```liquid
{% raw %}
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{% assign print_array = page.print_array %}
{% include {{print_array}} array=array_numbers %}
{% endraw %}
```


## &#35;&#35; `includes` > as a function with file extension `.liquid`

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
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{% include print_array.liquid array=array_numbers %}
```

```liquid
{% raw %}
{% assign array_numbers = "1,2,3,4,5" | split : ',' %}
{% include print_array.liquid array=array_numbers %}
{% endraw %}
```


## &#35;&#35; `includes` > as a sum function not printing variable

expected :

```
5 
```

result :

```liquid
{% include function_persistent_sum_of_a_and_b.liquid a=3 b=2 %}
```

```liquid
{% raw %}
{% include function_persistent_sum_of_a_and_b.liquid a=3 b=2 %}
{% endraw %}
```


## &#35;&#35; `includes` > as a sum function printing variable

expected :

```
5 
```

result :

```liquid
{% include function_persistent_sum_of_a_and_b.liquid a=3 b=2 %}
{{ result }}
```

```liquid
{% raw %}
{% include function_persistent_sum_of_a_and_b.liquid a=3 b=2 %}
{{ result }}
{% endraw %}
```

## &#35;&#35; `capture` > testing text

{% capture captured_text %}

this is the text to capture

{% endcapture %}

expected :

```
this is the text to capture
```

result :

```liquid
{{ captured_text }}
```

```liquid
{% raw %}
{% capture captured_text %}
  this is the text to capture
{% endcapture %}

{{ captured_text }}
{% endraw %}
```

## &#35;&#35; `capture` >`Shopify` > example

expected :

```
I am 35 and my favourite food is pizza.
```
                                       
result :

```liquid
{% assign favorite_food = "pizza" %}
{% assign age = 35 %}

{% capture about_me %}
I am {{ age }} and my favorite food is {{ favorite_food }}.
{% endcapture %}

{{ about_me }}
```

```liquid
{% raw %}
{% assign favorite_food = "pizza" %}
{% assign age = 35 %}

{% capture about_me %}
I am {{ age }} and my favorite food is {{ favorite_food }}.
{% endcapture %}

{{ about_me }}
{% endraw %}
```

#date 2023-07-06 11:45


## &#35;&#35; `capture` > testing content

{% capture captured_text %}

this is the text to capture

{% endcapture %}

expected :

```
this,is,the,text,to,capture
```

result :

```liquid
{{ captured_text|replace : " ", "," }}
```

```liquid
{% raw %}

{% capture captured_text %}
  this is the text to capture
{% endcapture %}

{{ captured_text|replace : " ", "," }}
{% endraw %}
```



#date 2023-07-06 11:48

## &#35;&#35; `capture` > `include` > without printing

(at last ...)

expected :

```
5
```
result :

```liquid
{% capture captured_text %}
  {% include function_persistent_sum_of_a_and_b.liquid a=3 b=2 %}
{% endcapture %}
{{ captured_text }}
```
 
## &#35;&#35; `capture` > `include` > internal variable persistency

Resetting the `result` variable

{% assign result = null %}

value of result before call include : `{{ result }}`

{% capture captured_text %}
  {% include function_persistent_sum_of_a_and_b.liquid a=3 b=2 %}
{% endcapture %}

value of result after call include : `{{ result }}`

```liquid
{% raw %}
Resetting the `result` variable

{% assign result = null %}

value of result before call include : `{{ result }}`

{% capture captured_text %}
  {% include function_persistent_sum_of_a_and_b.liquid a=3 b=2 %}
{% endcapture %}

value of result after call include : `{{ result }}`
{% endraw %}
```


## &#35;&#35; `capture` >`include` > function non-persistent

Resetting the `result` variable

{% assign result = null %}

value of result before call include : `{{ result }}`

{% capture sum %}
  {% include function_sum_of_a_and_b.liquid a=3 b=2 %}
{% endcapture %}

value of result after call include : `{{ result }}`
 
value of the function : `{{ sum }}`

```liquid
{% raw %}
Resetting the `result` variable

{% assign result = null %}

value of result before call include : `{{ result }}`

{% capture sum %}
  {% include function_sum_of_a_and_b.liquid a=3 b=2 %}
{% endcapture %}

value of result after call include : `{{ result }}`
 
value of the function : `{{ sum }}`

{% endraw %}
```
## &#35;&#35;  testing my assert procedure

expected success for 1 == 1

```liquid
 {% capture test %}
 {% include procedure_assert_this_and_that.liquid this=1 that=1 with_success=1 with_warning=1 %}
 {% endcapture %}{{test}}
```

expected failure for 1 == 0 
```liquid
 {% capture test %}
 {% include procedure_assert_this_and_that.liquid this=1 that=0 with_warning=1%}
 {% endcapture %}{{test}}
```
expected failure for 0 == ""
```liquid
 {% capture test %}
 {% include procedure_assert_this_and_that.liquid this=0 that="" with_warning=1%}
 {% endcapture %}{{test}}
``` 
expected failure for null == 0
```liquid
 {% capture test %}
 {% include procedure_assert_this_and_that.liquid this=null that=0 with_warning=1%}
 {% endcapture %}{{test}}
``` 
expected failure for null == ""
```liquid
 {% capture test %}
 {% include procedure_assert_this_and_that.liquid this=null that="" with_warning=1%}
 {% endcapture %}{{test}}
``` 
expected success for null == null
```liquid
 {% capture test %}
 {% include procedure_assert_this_and_that.liquid this=null that=null with_success=1 with_warning=1%}
 {% endcapture %}{{test}}
``` 

expected success for "" == ""
```liquid
 {% capture test %}
 {% include procedure_assert_this_and_that.liquid this="" that="" with_success=1 with_warning=1%}
 {% endcapture %}{{test}}
``` 

expected success for ["1,2,3"] == ["1,2,3"]

```liquid
{% comment %} not taking chances {% endcomment %}
{% assign array_1 = null %}
{% assign array_2 = null %}

{% assign array_1 = "1,2,3"|split : "," %}
{% assign array_2 = "1,2,3"|split : "," %}


 {% capture test %}
 {% include procedure_assert_this_and_that.liquid this=array_1 that=array_2 with_success=1 with_warning=1%}
 {% endcapture %}{{test}}
``` 

expected success for [""] == [""]

```liquid
{% comment %} not taking chances {% endcomment %}
{% assign array_1 = null %}
{% assign array_2 = null %}

{% assign array_1 = ",,"|split : "," %}
{% assign array_2 = ",,"|split : "," %}

 {% capture test %}
 {% include procedure_assert_this_and_that.liquid this=array_1 that=array_2 with_success=1 with_warning=1%}
 {% endcapture %}{{test}}
``` 

expected failure for ["1,2,4"] == ["1,2,3"]

```liquid
{% comment %} not taking chances {% endcomment %}
{% assign array_1 = null %}
{% assign array_2 = null %}

{% assign array_1 = "1,2,4"|split : "," %}
{% assign array_2 = "1,2,3"|split : "," %}

 {% capture test %}
 {% include procedure_assert_this_and_that.liquid this=array_1 that=array_2 with_success=1 with_warning=1%}
 {% endcapture %}{{test}}
``` 

## &#35;&#35; testing my date function

```liquid
{% assign expected = null %}
{% assign result = null %}
{% assign assert = null %}

{% assign expected = "2023-06-28T05:16:00+00:00,1687914994970097614" %}

{%- capture result -%}
    {% include as_date_utc_and_id_from_custom_date.liquid custom_date="#date 2023-06-28 05:16 1687914994970097614 GMT"%}
{%- endcapture -%}

{%- capture assert -%}
    {% include procedure_assert_this_and_that.liquid this=expected that=result with_success=1 with_warning=1 name="testing the date"%}
{%- endcapture -%}
{{assert}}

{% comment %}expected :"{{ expected }}"{% endcomment %}
{% comment %}result :"{{ result }}"{% endcomment %}

{% assign assert = null %}
{% assign expected = null %}
{% assign result = null %} 
```
---
#date 2023-07-10 22:31 1689013886644392432 GMT

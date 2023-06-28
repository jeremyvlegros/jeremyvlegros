---
title : "Title > Testing > variables"
layout : post
test_list :
  - "a"
  - "b"
  - "c"
---

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

{% for value in page.test_list %}
value : {{ value }}
{% endfor %}

printing `test_list` : `{{ test_list }}`

printing `test_list`  as json :  `{{ test_list | jsonify}}`

```
{%raw%}
The loop :

{% for value in page.test_list %}
value : {{ value }}
{% endfor %}

printing `test_list` : `{{ test_list }}`

printing `test_list`  as json :  `{{ test_list | jsonify}}`
{% endraw %}
```

## Displaying Liquid results in code ?

```
{% for value in page.test_list %}
{{ value }}
{% endfor %}
```

## Unless

Unless 1 > 4 print 1 is smaller than 4

`
{% unless 1 > 4 %}
1 is smaller than 4
{% endunless %}
`

```
{%raw%}
Unless 1 > 4 print 1 is smaller than 4

`
{% unless 1 > 4 %}
1 is smaller than 4
{% endunless %}
`
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

### `site.name` : `{{site.name}}`

### `page.url` : `{{page.url}}`

### `site.url` : `{{site.url}}`

### constructed canonical page url (need to set name in `_config.yml`) : `{{ site.url | append :"/" | append : site.name | append : page.url }}`

## Accessing global variables `_config.yml`

### global variable social_links

{% for link in site.social_links %}
{{ link }}
{% endfor %}

### global variable link name social_links

{% for link in site.social_links %}
{{ link.name }}
{% endfor %}

### global variable link url social_links

{% for link in site.social_links %}
{{ link.url }}
{% endfor %}


### global variable link name social_links, accessing as a dictionary

{% for link in site.social_links %}
{{ link[link.name] }}
{% endfor %}

### global variable link url social_links, accessing as a dictionary, with dot

{% for link in site.social_links %}
{{ link[link.url]}}
{% endfor %}

### global variable link url social_links, accessing as a dictionary, with string key

{% for link in site.social_links %}
{{ link["url"]}}
{% endfor %}

## Accessing variables in `_data > social_links.yml`

### social links

{% for link in site.data.social_links %}
{{ link }}
{% endfor %}

### social_links > name

{% for link in site.data.social_links %}
{{ link.name }}
{% endfor %}

### social_links > url

{% for link in site.data.social_links %}
{{ link.url }}
{% endfor %}


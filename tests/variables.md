---
title : "Title > Testing > variables >"
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

## prefixing a html character by NBSP


{% assign title = page.title %}
{% if title %}
{% assign title = title | escape | replace : " &gt;","&nbsp;&gt;" %}
{% endif %}

this should not break : {{title}}

## `local variable` list `test_list` a b c

{% for value in page.test_list %}
{{ value }}
{% endfor %}

## website name ? : "{{site.name}}"

## page URL ? : "{{page.url}}"

## `_config.yml`

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

## global variable link url social_links, accessing as a dictionary

{% for link in site.social_links %}
{{ link[link.url]}}
{% endfor %}


## `_data > social_links.yml`

### link social_links

{% for link in site.data.social_links %}
{{ link }}
{% endfor %}

### link name social_links

{% for link in site.data.social_links %}
{{ link.name }}
{% endfor %}

### link url social_links

{% for link in site.data.social_links %}
{{ link.url }}
{% endfor %}

### global variable link url social_links, accessing as a dictionary with string key

{% for link in site.social_links %}
{{ link["url"]}}
{% endfor %}

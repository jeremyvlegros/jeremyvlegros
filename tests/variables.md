---
title : "Testing variables"
layout : post
test_list :
  - "a"
  - "b"
  - "c"
---

## `local variable` list `test_list` a b c

{% for value in page.test_list %}
{{ value }}
{% endfor %}

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

#date 2023-06-20 1416 1687256188459386009 GMT

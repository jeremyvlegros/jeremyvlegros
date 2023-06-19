---
title : "Testing liquid `for` loop"
layout : base
---


---

# `_config.yml`

## list a b c

{% for value in site.test_list %}
{{ value }}
{% endfor %}


## link social_links

{% for link in site.social_links %}
{{ link }}
{% endfor %}

## link name social_links

{% for link in site.social_links %}
{{ link.name }}
{% endfor %}

## link url social_links

{% for link in site.social_links %}
{{ link.url }}
{% endfor %}


## link name social_links, accessing as a dictionary

{% for link in site.social_links %}
{{ link[link.name] }}
{% endfor %}

## link url social_links, accessing as a dictionary

{% for link in site.social_links %}
{{ link[link.url]}}
{% endfor %}

---


# `_data > social_links.yml`

## link social_links

{% for link in site.data.social_links %}
{{ link }}
{% endfor %}

## link name social_links

{% for link in site.data.social_links %}
{{ link.name }}
{% endfor %}

## link url social_links

{% for link in site.data.social_links %}
{{ link.url }}
{% endfor %}




#date 2023-06-19 0840 1687149656095196022 GMT

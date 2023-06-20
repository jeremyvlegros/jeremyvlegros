---
title : "Testing variables"
layout : base
test_list :
  - "a"
  - "b"
  - "c"
---

# `local variable` list `test_list` a b c

{% for value in page.test_list %}
<!----> {{ value }}
{% endfor %}

# `_config.yml`

## global variable social_links

{% for link in site.social_links %}
<!----> {{ link }}
{% endfor %}

## global variable link name social_links

{% for link in site.social_links %}
<!----> {{ link.name }}
{% endfor %}

## global variable link url social_links

{% for link in site.social_links %}
<!----> {{ link.url }}
{% endfor %}


## global variable link name social_links, accessing as a dictionary

{% for link in site.social_links %}
<!----> {{ link[link.name] }}
{% endfor %}

## global variable link url social_links, accessing as a dictionary

{% for link in site.social_links %}
<!----> {{ link[link.url]}}
{% endfor %}


# `_data > social_links.yml`

## link social_links

{% for link in site.data.social_links %}
<!----> {{ link }}
{% endfor %}

## link name social_links

{% for link in site.data.social_links %}
<!----> {{ link.name }}
{% endfor %}

## link url social_links

{% for link in site.data.social_links %}
<!----> {{ link.url }}
{% endfor %}

# `div creation`

{% include html_tag content="division html content tag" str_tag=div str_id="creation" str_class="logarithm" str_url=null str_alt_image=null %}


#date 2023-06-20 1416 1687256188459386009 GMT

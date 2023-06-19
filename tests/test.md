---
title : "Testing liquid `for` loop"
layout : base
---

# list a b c

{% for value in site.test_list %}
{{ value }}
{% endfor %}


# link from social_links

{% for link in site.social_links %}
{{ link }}
{% endfor %}

# link name from social_links

{% for link in site.social_links %}
{{ link.name }}
{% endfor %}

# link url from social_links

{% for link in site.social_links %}
{{ link.url }}
{% endfor %}


# link name from social_links, accessing as a dictionary

{% for link in site.social_links %}
{{ link[link.name] }}
{% endfor %}

# link url from social_links, accessing as a dictionary

{% for link in site.social_links %}
{{ link[link.url]}}
{% endfor %}

#date 2023-06-19 0830 1687149057148594805 GMT

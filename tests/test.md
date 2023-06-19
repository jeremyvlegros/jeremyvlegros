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


#date 2023-06-19 0816 1687148179676469576 GMT


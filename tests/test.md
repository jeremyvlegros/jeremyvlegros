---
title : "Testing liquid `for` loop"
layout : base
---

{% for value in site.test_list %}
{{ value }}
{% endfor %}


{% for link in site.social_links %}
{{ link }}
{% endfor %}



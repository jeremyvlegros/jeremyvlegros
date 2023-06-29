---
title                    : null
content_description      : null
date_of_creation         : null
date_of_modification     : null
content_background_color : null
category                 : null
tags                     : null
meta_image_url           : null
type                     : null
---

<!-- LIQUID HEAD -->

<!--   DECLARATION -->

{% assign page_title                    = page.title %}
{% assign page_tags                     = page.tags %}
{% assign page_url                      = page.url %}
{% assign page_category                 = page.category %}
{% assign page_content_description      = page.content_description %}
{% assign page_content_background_color = page.content_background_color %}
{% assign page_type                     = page.type %}

{% assign date_of_creation     = page.date_of_creation %}
{% assign date_of_modification = page.date_of_modification %}

{% assign site_name            = site.name %}
{% assign meta_image           = null %}

<!--   INITILISATION -->

<!-- default date
-->
{% unless date_of_creation %}
{% assign date_of_creation      = "2023-05-19T00:00:00+00:00"%}
{% endunless %}

{% unless date_of_modification %}
{% assign date_of_modification  = "2023-05-19T00:00:00+00:00"%}
{% endunless %}

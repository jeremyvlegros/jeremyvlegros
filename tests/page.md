---
title                    : null
content_description      : null
date_of_creation         : null
date_of_modification     : null
color_background         : null
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
{% assign page_color_background         = page.color_background %}
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

<!-- TITLE
-->
{% if page_title %}
{% assign page_title = page_title | escape | replace : " &gt;","&nbsp;&gt;" %}
{% endif %}

<!-- PAGE URL
-->
{% if site_name %}
{% assign page_url = site.url | append :"/" | append : site_name | append : page.url %}
{% endif %}

<!-- PROCESSING
 -->


<!-- DATE OF CREATION
 -->
{% if date_of_creation %}

<!-- input                        = "#date 2023-06-28 05:16 1687914994970097614 GMT"
     output                       =        "2023-06-28T05:16:00+00:00"

-->

<!-- removing "#date " and " GMT"
                                 => "2023-06-28 05:16 1687914994970097614"
-->
{% assign date_of_creation       =  date_of_creation     | replace : "#date ","" | replace " GMT",""%}

<!-- split date in array
                                => "[2023-06-28, 05:16, 1687914994970097614]"
-->
{% assign date_of_creation      =  date_of_creation     | split:" "%}

<!-- getting time
                                => 05:16
-->

{% assign time_of_creation      =  date_of_creation[1]    %}

<!-- hour with seconds and Time difference
I won't calculate the seconds ... for now ?
                               => "05:16:00+00:00"
-->

{% assign time_of_creation     =  time_of_creation     | append :":00+00:00" %}

<!-- adding 'T' and hour to date
                               => "2023-06-28T05:16:00+00:00"
-->
<!--                               2023-06-28                          T             05:16:00+00:00
-->
{% assign date_of_creation      =  date_of_creation[0]     | append : "T" | append : time_of_creation%}

{% endif %}

<!-- DATE OF MODIFICATION
 -->
{% if date_of_modification %}

<!-- input                        = "#date 2023-06-28 05:16 1687914994970097614 GMT"
     output                       =       "2023-06-28T05:16:00+00:00"

-->

<!-- removing "#date " and " GMT"
                                 => "2023-06-28 05:16 1687914994970097614"
-->
{% assign date_of_modification   =  date_of_modification     | replace : "#date ","" | replace " GMT",""%}

<!-- split date in array
                                 => "[2023-06-28, 05:16, 1687914994970097614]"
-->
{% assign date_of_modification   =  date_of_modification     | split:" "%}

<!-- getting time
                                => 05:16
-->

{% assign time_of_modification   =  date_of_modification[1]    %}

<!-- hour with seconds and Time difference
I won't calculate the seconds ... for now ?
                                => "05:16:00+00:00"
-->

{% assign time_of_modification   =  time_of_modification     | append :":00+00:00" %}

<!-- adding 'T' and hour to date
                               => "2023-06-28T05:16:00+00:00"
-->
<!--                               2023-06-28                          T             05:16:00+00:00
-->
{% assign date_of_modification  =  date_of_modification[0]     | append : "T" | append : time_of_creation%}

{% endif %}

---
title                : null
content_description  : null
date_of_creation     : "#date 2023-06-28 05:16 1687914994970097614 GMT"
date_of_modification : "#date 2023-06-28 05:16 1687914994970097614 GMT"
post_color           : null
category             : null
tags                 : null
---

<!-- BEGIN LIQUID -->

<!-- DECLARATION -->

{% assign title                = page.title %}
{% assign content_description  = page.content_description %}
{% assign date_of_creation     = page.date_of_creation %}
{% assign date_of_modification = page.date_of_modification %}
{% assign tags                 = page.tags %}

<!-- PROCESSING
 -->

{% assign title                = title | escape %}

<!-- PROCESSING > DATE
 -->

<!-- input                        = "#date 2023-06-28 05:16 1687914994970097614 GMT"
     output                       =       "2023-06-28T05:16:00+00:00"

-->

<!-- removing "#date " and " GMT"
                                 => "2023-06-28 05:16 1687914994970097614"
-->
{% assign date_of_creation       =  date_of_creation     | replace : "#date ","" | replace " GMT",""%}
{% assign date_of_modification   =  date_of_modification | replace : "#date ","" | replace " GMT",""%}

<!-- split date in array
                                => "[2023-06-28, 05:16, 1687914994970097614]"
-->
{% assign date_of_creation      =  date_of_creation     | split:" "%}
{% assign date_of_modification  =  date_of_modification | split:" "%}

<!-- getting time
                                => 05:16
-->

{% assign time_of_creation      =  date_of_creation[1]    %}
{% assign time_of_modification  =  date_of_modification[1]%}

<!-- hour with seconds and Time difference
I won't calculate the seconds ... for now ?
                               => "05:16:00+00:00"
-->


{% assign time_of_creation     =  time_of_creation     | append :":00+00:00" %}
{% assign time_of_modification =  time_of_modification | append :":00+00:00" %}

<!-- adding 'T' and hour to date
                               => "2023-06-28T05:16:00+00:00"
                      reference   "2023-06-28T05:16:00+00:00"
-->
<!--                               2023-06-28                          T             05:16:00+00:00
-->
{% assign date_of_creation      =  date_of_creation[0]     | append : "T" | append : time_of_creation%}
{% assign date_of_modification  =  date_of_modification[0] | append : "T" | append : time_of_modification%}

<!-- END LIQUID -->
## INPUT______: #date 2023-06-28 05:16 1687914994970097614 GMT
## EXPECTED___: 2023-06-28T05:16:00+00:00
## OUTPUT_____: {{date_of_creation}}
